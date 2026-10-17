# Glossary

Every term used in the topic pages appears here once. Each row links back to where it was first explained.

Acronyms are kept in English on purpose: that is how the standards and the tools name them.

| Term | Type | Meaning in English | Plain-language explanation | Used in |
|---|---|---|---|---|
| <a id="5gc"></a>**5GC** | Network | 5G Core | The brain of the 5G network: the set of software functions that decide who may connect, where they are and how their data is routed. | [↩ back to topic](01-5g-registration/README.md#t-5gc) |
| <a id="sba"></a>**SBA** | Architecture | Service-Based Architecture | The design in which core functions expose services to each other over HTTP-style APIs, instead of fixed point-to-point links. | [↩ back to topic](01-5g-registration/README.md#t-sba) |
| <a id="nf"></a>**NF** | Concept | Network Function | One piece of software in the core with a single job (for example AMF). Many NFs together make the core. | [↩ back to topic](01-5g-registration/README.md#t-sba) |
| <a id="ue"></a>**UE** | Device | User Equipment | The phone (or modem) that holds the SIM and wants to use the network. | [↩ back to topic](01-5g-registration/README.md#t-ue) |
| <a id="gnb"></a>**gNB** | Radio | next generation NodeB | The 5G base station. It talks radio to the UE and forwards signalling to the core. | [↩ back to topic](01-5g-registration/README.md#t-gnb) |
| <a id="ran"></a>**RAN** | Network | Radio Access Network | All the base stations together. In 5G the RAN node is the gNB. | [↩ back to topic](01-5g-registration/README.md#t-gnb) |
| <a id="amf"></a>**AMF** | NF | Access and Mobility Management Function | The front door of the core. It receives the UE's requests, keeps track of where the UE is and coordinates the other functions. | [↩ back to topic](01-5g-registration/README.md#t-amf) |
| <a id="ausf"></a>**AUSF** | NF | Authentication Server Function | Checks that the SIM is genuine, using data from the UDM. It answers the AMF's question 'is this subscriber who they claim to be?'. | [↩ back to topic](01-5g-registration/README.md#t-ausf) |
| <a id="udm"></a>**UDM** | NF | Unified Data Management | Holds subscriber data (keys, subscription, which AMF serves whom). Usually backed by a database. | [↩ back to topic](01-5g-registration/README.md#t-udm) |
| <a id="nrf"></a>**NRF** | NF | Network Repository Function | The phone book of the core. NFs register there and ask it where to find other NFs. | [↩ back to topic](01-5g-registration/README.md#t-nrf) |
| <a id="pcf"></a>**PCF** | NF | Policy Control Function | Holds the rules (for example what the subscriber may do, how much bandwidth). The AMF can ask it for an access and mobility policy. | [↩ back to topic](01-5g-registration/README.md#t-flow) |
| <a id="uecm"></a>**UECM** | Service | UE Context Management | The UDM service where an AMF records that it is the one serving a given UE (`Nudm_UECM_Registration`). | [↩ back to topic](01-5g-registration/README.md#t-flow) |
| <a id="sdm"></a>**SDM** | Service | Subscriber Data Management | The UDM service for reading (and subscribing to changes of) subscription data (`Nudm_SDM_Get`, `Nudm_SDM_Subscribe`). | [↩ back to topic](01-5g-registration/README.md#t-flow) |
| <a id="sctp"></a>**SCTP** | Protocol | Stream Control Transmission Protocol | Reliable, message-oriented transport used on N2 between the gNB and the AMF. | [↩ back to topic](01-5g-registration/README.md#t-stack) |
| <a id="tcp"></a>**TCP** | Protocol | Transmission Control Protocol | Reliable byte-stream transport. The service-based interfaces use it under HTTP/2. | [↩ back to topic](01-5g-registration/README.md#t-stack) |
| <a id="ip"></a>**IP** | Protocol | Internet Protocol | The network layer that carries SCTP and TCP between the nodes. | [↩ back to topic](01-5g-registration/README.md#t-stack) |
| <a id="http2"></a>**HTTP/2** | Protocol | Hypertext Transfer Protocol version 2 | The web protocol that the 5G core reuses for the calls between NFs. | [↩ back to topic](01-5g-registration/README.md#t-stack) |
| <a id="json"></a>**JSON** | Format | JavaScript Object Notation | The text format of the request and response bodies on the service-based interfaces. | [↩ back to topic](01-5g-registration/README.md#t-stack) |
| <a id="tls"></a>**TLS** | Protocol | Transport Layer Security | Encrypts and authenticates a connection. The specs define it for the service-based interfaces. | [↩ back to topic](01-5g-registration/README.md#t-stack) |
| <a id="amfset"></a>**AMF Set** | Concept | AMF Set | A group of AMFs that can serve the same subscribers and back each other up. | [↩ back to scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| <a id="t3346"></a>**T3346** | Timer | Mobility management back-off timer | Sent to a UE with a congestion reject: the UE must wait this long before trying again. | [↩ back to scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| <a id="hpa"></a>**HPA** | Kubernetes | Horizontal Pod Autoscaler | Kubernetes component that raises or lowers the number of pod replicas based on load. | [↩ back to scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| <a id="sim"></a>**SIM / USIM** | Device | Subscriber Identity Module / Universal SIM | The card (or eSIM) holding the subscriber identity and the secret key shared with the operator. | [↩ back to topic](01-5g-registration/README.md#t-ue) |
| <a id="supi"></a>**SUPI** | Identifier | Subscription Permanent Identifier | The permanent identity of a subscriber, for example derived from the IMSI. It should never travel over the air in clear text. | [↩ back to topic](01-5g-registration/README.md#t-ids) |
| <a id="suci"></a>**SUCI** | Identifier | Subscription Concealed Identifier | The SUPI encrypted by the UE with the operator's public key, so that the radio link does not reveal who is connecting. | [↩ back to topic](01-5g-registration/README.md#t-ids) |
| <a id="routing-indicator"></a>**Routing Indicator** | Identifier field | Routing Indicator (part of the SUCI) | A short number (1 to 4 digits †) in the SUCI that helps the AMF pick which AUSF should handle that subscriber. Subscribers from different SIM batches can carry different values. | [↩ back to scenario](01-5g-registration/scenarios/subset-cannot-register.md) |
| <a id="hni"></a>**HNI** | Identifier field | Home Network Identifier (part of the SUCI) | The operator's network code (MCC and MNC) inside the SUCI. It says which home network the subscriber belongs to. | [↩ back to scenario](01-5g-registration/scenarios/subset-cannot-register.md) |
| <a id="sidf"></a>**SIDF** | Function | Subscription Identifier De-concealing Function | The function (part of the UDM) that turns a SUCI back into a SUPI. | [↩ back to topic](01-5g-registration/README.md#t-ids) |
| <a id="guti"></a>**5G-GUTI** | Identifier | 5G Globally Unique Temporary Identifier | A temporary identity given by the AMF after registration, so the permanent identity is not reused over the air. | [↩ back to topic](01-5g-registration/README.md#t-flow) |
| <a id="aka"></a>**5G AKA** | Procedure | 5G Authentication and Key Agreement | The challenge-response protocol in which the network and the SIM prove to each other that they know the shared key. | [↩ back to topic](01-5g-registration/README.md#t-auth) |
| <a id="eapaka"></a>**EAP-AKA'** | Procedure | Extensible Authentication Protocol, AKA prime | The other standard authentication method in 5G. The UDM chooses between 5G AKA and this one. | [↩ back to topic](01-5g-registration/README.md#t-auth) |
| <a id="nas"></a>**NAS** | Protocol | Non-Access Stratum | Signalling between the UE and the AMF. The gNB carries it but cannot read it. Registration Request and Accept are NAS messages. | [↩ back to topic](01-5g-registration/README.md#t-protocols) |
| <a id="rrc"></a>**RRC** | Protocol | Radio Resource Control | Signalling between the UE and the gNB over the radio link. It carries the NAS message on the first hop. | [↩ back to topic](01-5g-registration/README.md#t-protocols) |
| <a id="ngap"></a>**NGAP** | Protocol | Next Generation Application Protocol | The signalling protocol between the gNB and the AMF over N2. | [↩ back to topic](01-5g-registration/README.md#t-protocols) |
| <a id="n1"></a>**N1** | Interface | Reference point N1 | Logical link between the UE and the AMF (NAS signalling). It physically travels through the gNB. | [↩ back to topic](01-5g-registration/README.md#t-interfaces) |
| <a id="n2"></a>**N2** | Interface | Reference point N2 | Link between the RAN (gNB) and the AMF, carrying NGAP. | [↩ back to topic](01-5g-registration/README.md#t-interfaces) |
| <a id="n8"></a>**N8** | Interface | Reference point N8 | Link between the UDM and the AMF. | [↩ back to topic](01-5g-registration/README.md#t-interfaces) |
| <a id="n12"></a>**N12** | Interface | Reference point N12 | Link between the AMF and the AUSF. | [↩ back to topic](01-5g-registration/README.md#t-interfaces) |
| <a id="n13"></a>**N13** | Interface | Reference point N13 | Link between the UDM and the AUSF. | [↩ back to topic](01-5g-registration/README.md#t-interfaces) |
| <a id="service-ops"></a>**Nausf_ / Nudm_ services** | API | Service operations | Names of the APIs one NF offers to another, for example Nudm_SDM_Get ('read subscription data'). The prefix says which NF offers it. | [↩ back to topic](01-5g-registration/README.md#t-flow) |
| <a id="3gpp"></a>**3GPP** | Standards | 3rd Generation Partnership Project | The body that writes the telecom standards. Each spec is a TS (Technical Specification). | [↩ back to topic](01-5g-registration/README.md#t-refs) |
| <a id="ts"></a>**TS** | Standards | Technical Specification | A numbered 3GPP document, for example TS 23.502. | [↩ back to topic](01-5g-registration/README.md#t-refs) |
