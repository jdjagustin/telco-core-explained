# 01 · 5G registration

Terms in **bold links** point to the [glossary](../glossary.md); each glossary row has a "back to topic" link.

## What you will learn

- What a UE must do before it can use a 5G network, and why it cannot send data yet.
- Who the main functions are and which interface connects each pair.
- The message sequence of an initial registration, simplified.
- Which parts are fixed by the standard and which depend on the vendor.

![Animated sequence diagram of 5G initial registration](diagrams/registration-flow.svg)

*The diagram loops. Bright arrows are the current step, dimmed ones are done. If your viewer does not animate SVG, open the file in a browser.*

## The cast

<a id="t-5gc"></a><a id="t-sba"></a>
The [**5GC**](../glossary.md#5gc) is built as a [**SBA**](../glossary.md#sba): each [**NF**](../glossary.md#nf) offers services to the others, instead of every pair having its own dedicated link.

<a id="t-ue"></a>
- [**UE**](../glossary.md#ue): the device. It holds a [**SIM / USIM**](../glossary.md#sim) with the subscriber identity and a secret key.

<a id="t-gnb"></a>
- [**gNB**](../glossary.md#gnb): the base station, part of the [**RAN**](../glossary.md#ran). It relays signalling; it does not decide anything about the subscriber.

<a id="t-amf"></a>
- [**AMF**](../glossary.md#amf): receives the registration, tracks the UE, and calls the other functions.

<a id="t-ausf"></a>
- [**AUSF**](../glossary.md#ausf): runs the authentication on behalf of the AMF.

<a id="t-udm"></a>
- [**UDM**](../glossary.md#udm): holds the subscriber data and the key material.

<a id="t-nrf"></a>
- [**NRF**](../glossary.md#nrf): the phone book. Before the AMF calls the AUSF or the UDM it finds them through the NRF. The NRF is not drawn in the diagram to keep it readable, but it is used in every step that starts a call between two NFs.

<a id="t-interfaces"></a>
### Interfaces used in this flow

| Reference point | Between | Carries |
|---|---|---|
| [**N1**](../glossary.md#n1) | UE – AMF | [**NAS**](../glossary.md#nas) signalling |
| [**N2**](../glossary.md#n2) | gNB – AMF | [**NGAP**](../glossary.md#ngap) signalling |
| [**N8**](../glossary.md#n8) | UDM – AMF | subscription and registration data |
| [**N12**](../glossary.md#n12) | AMF – AUSF | authentication requests |
| [**N13**](../glossary.md#n13) | UDM – AUSF | authentication data |

<a id="t-protocols"></a>
### Three signalling layers, one message

The Registration Request is a [**NAS**](../glossary.md#nas) message for the AMF. On the radio hop it rides inside [**RRC**](../glossary.md#rrc) (UE to gNB). The gNB then puts it inside an [**NGAP**](../glossary.md#ngap) message to the AMF. Same content, three envelopes.

<a id="t-ids"></a>
### Identities: SUPI, SUCI, 5G-GUTI

The permanent identity is the [**SUPI**](../glossary.md#supi). To avoid sending it in clear over the air, the UE sends a [**SUCI**](../glossary.md#suci): the SUPI encrypted with the operator's public key. The [**SIDF**](../glossary.md#sidf) (part of the UDM) reverses it. After registration the AMF hands out a temporary [**5G-GUTI**](../glossary.md#guti) for later use.

<a id="t-flow"></a>
## The flow

1. **Registration Request.** The UE sends it (NAS) to the gNB over RRC. It carries the SUCI (or a temporary identity if it has one).
2. **Initial UE Message.** The gNB cannot read the NAS content. It forwards it to an AMF over N2 in an NGAP *Initial UE Message*. The gNB selects the AMF; the AMF may later redirect the UE to a more suitable one.
3. **Authentication request towards the AUSF.** The AMF calls `Nausf_UEAuthentication_Authenticate` on the AUSF with the SUCI and the serving network name. The AUSF calls `Nudm_UEAuthentication_Get` on the UDM, which de-conceals the SUCI to the SUPI, selects the method and returns the authentication data.
4. **Challenge and NAS security.** The AMF sends an Authentication Request to the UE; the UE checks it with its SIM and answers. The AMF (with the AUSF) verifies the answer. Then the AMF sends a Security Mode Command and the UE confirms. From here NAS messages are protected.
5. **Registration with the UDM.** The AMF registers itself as the serving AMF (`Nudm_UECM_Registration`) and reads the subscription (`Nudm_SDM_Get`, with `Nudm_SDM_Subscribe` to be told about changes). Optionally it also fetches an access and mobility policy from the [**PCF**](../glossary.md#pcf).
6. **Registration Accept.** The AMF answers with Registration Accept, including a 5G-GUTI, and the UE replies with Registration Complete.

<a id="t-auth"></a>
### Authentication methods

The UDM chooses between [**5G AKA**](../glossary.md#aka) and [**EAP-AKA'**](../glossary.md#eapaka). In both, the SIM and the network prove to each other that they know the same secret key, without sending the key.

### What registration does *not* do

It does not create a data session. The UE is known and allowed on the network, but it cannot browse yet. That is the next topic (PDU session).

## Standard vs. implementation

| Defined by the standard | Left to the vendor / operator |
|---|---|
| Message names and order, reference points, service operation names | How the AMF is deployed (VMs, containers), how many instances, how they are scaled |
| Identity concealment and authentication procedures | Timers, retry policies and overload thresholds beyond the minimums |
| What each NF is responsible for | Logging format, counters, dashboards, alarms |
| | Whether the UDM is backed by one database or several, and how it is replicated |

Failure behaviour (what a UE sees when a step fails) is specified through cause values; what *operators* do to find the root cause is implementation. Scenarios will cover that.

## Scenarios

Planned for this topic (one page each in `scenarios/`): a subset of subscribers cannot register; the AMF is overloaded and the platform cannot create more instances.

<a id="t-refs"></a>
## References

- [**3GPP**](../glossary.md#3gpp) specs, each a [**TS**](../glossary.md#ts): archive at <https://www.3gpp.org/ftp/Specs/archive/>
  - TS 23.501, *System architecture for the 5G System*: functions and reference points (clause 4.2.7).
  - TS 23.502, *Procedures for the 5G System*: registration procedure (clause 4.2.2.2.2).
  - TS 24.501, *NAS protocol for 5G*: NAS messages.
  - TS 33.501, *Security architecture and procedures for 5G*: SUCI/SUPI, 5G AKA, EAP-AKA' (clauses 6.1.2, 6.1.3).
  - TS 38.413, *NG-AP*: Initial UE Message (clause 8.6.1).
- Clause numbers refer to the releases checked when writing; they can move between releases.
