# References

One place to audit every source used in this repository. Each row says what the source supports and how far it has been checked.

## How the links work

- 3GPP publishes specifications as complete documents (archive: <https://www.3gpp.org/ftp/Specs/archive/>, folder `<series>_series/<spec number>`), without a link per clause.
- Clause links below point to [iTecSpec](https://itecspec.com), a third-party reader that opens a given clause directly. Treat it as a reading shortcut: it sometimes shows only the clause index, so the **authoritative text is the official 3GPP document**.
- Status: **checked** = the clause content was read and matches what the repository says; **partly checked** = the clause exists and its purpose matches, but a specific detail is not confirmed (marked with † in the page where it is used); **title only** = only the title and table of contents were checked.

## 3GPP specifications

| Spec | Title | Clause | Used for | Status | Used in |
|---|---|---|---|---|---|
| TS 23.501 | System architecture for the 5G System (5GS) | [4.2.7 Reference points](https://itecspec.com/3gpp/23.501/s/4.2.7) | Roles of the functions; N1, N2, N8, N12, N13 | checked | [topic 01](01-5g-registration/README.md) |
| TS 23.501 | System architecture for the 5G System (5GS) | AMF Set and AMF selection (clauses not identified yet) | AMF Set concept | not checked (†) | [scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| TS 23.502 | Procedures for the 5G System (5GS) | [4.2.2.2.2 General Registration](https://itecspec.com/3gpp/23.502/s/4.2.2.2.2) | Registration message flow and service operation names | checked | [topic 01](01-5g-registration/README.md) |
| TS 24.501 | Non-Access-Stratum (NAS) protocol for 5GS | [5.3.9 Handling of NAS level mobility management congestion control](https://itecspec.com/3gpp/24.501/s/5.3.9) | Congestion reject with 5GMM cause #22 and back-off timer T3346 | checked | [scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| TS 33.501 | Security architecture and procedures for 5G system | [6.1.2](https://itecspec.com/3gpp/33.501/s/6.1.2), [6.1.3](https://itecspec.com/3gpp/33.501/s/6.1.3) | SUCI/SUPI, 5G AKA, EAP-AKA' | checked | [topic 01](01-5g-registration/README.md) |
| TS 38.413 | NG Application Protocol (NGAP) | [8.6.1 Initial UE Message](https://itecspec.com/3gpp/38.413/s/8.6.1) | First NAS message forwarded to the AMF | checked | [topic 01](01-5g-registration/README.md) |
| TS 38.413 | NG Application Protocol (NGAP) | [8.7.7 Overload Start](https://itecspec.com/3gpp/38.413/s/8.7.7) | Telling a gNB to reduce signalling towards an AMF | checked | [scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| TS 38.413 | NG Application Protocol (NGAP) | [8.7.3 AMF Configuration Update](https://itecspec.com/3gpp/38.413/s/8.7.3) | Updating configuration shared by the gNB and the AMF | partly checked (†): whether it changes the AMF weight is not confirmed | [scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| TS 38.413 | NG Application Protocol (NGAP) | [9.3.1.32 Relative AMF Capacity](https://itecspec.com/3gpp/38.413/s/9.3.1.32) | The weight an AMF advertises to gNBs | title only (†) | [scenario](01-5g-registration/scenarios/amf-overload-no-capacity.md) |
| TS 38.412 | NG-RAN; NG signalling transport | [7 Transport layer](https://itecspec.com/3gpp/38.412/s/7) | SCTP as the transport of N2 | checked | [topic 01](01-5g-registration/README.md) |
| TS 38.331 | NR; Radio Resource Control (RRC) protocol specification | whole spec | RRC, carrying of NAS messages (DedicatedNAS-Message) | title only | [topic 01](01-5g-registration/README.md) |
| TS 29.500 | 5G System; Technical Realization of Service Based Architecture | [5.3 Transport Protocol](https://itecspec.com/3gpp/29.500/s/5.3), [5.4 Serialization Protocol](https://itecspec.com/3gpp/29.500/s/5.4) | HTTP/2 over TCP, JSON | checked | [topic 01](01-5g-registration/README.md) |
| TS 29.500 | 5G System; Technical Realization of Service Based Architecture | [6.7.2 Transport layer security protection of messages](https://itecspec.com/3gpp/29.500/s/6.7.2) | TLS on the service-based interfaces | title only | [topic 01](01-5g-registration/README.md) |
| TS 29.501 | 5G System; Principles and Guidelines for Services Definition | whole spec | OpenAPI and JSON conventions of the service APIs | title only | [topic 01](01-5g-registration/README.md) |

## IETF

| Document | Title | Used for |
|---|---|---|
| [RFC 4960](https://www.rfc-editor.org/rfc/rfc4960) | Stream Control Transmission Protocol | SCTP on N2 |
| [RFC 9113](https://www.rfc-editor.org/rfc/rfc9113) | HTTP/2 | Service-based interfaces |
| [RFC 8259](https://www.rfc-editor.org/rfc/rfc8259) | The JSON Data Interchange Format | Message bodies of the service-based interfaces |

## Kubernetes

- [Horizontal Pod Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
- [Scheduling and eviction](https://kubernetes.io/docs/concepts/scheduling-eviction/)
- [kubectl reference](https://kubernetes.io/docs/reference/kubectl/)

## Maintenance rule

Every commit that introduces a source adds its row here and links the first mention in the text.
