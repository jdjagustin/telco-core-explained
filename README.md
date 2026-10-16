# telco-core-explained

A visual, step-by-step guide to mobile core networks (5G Core and 4G EPC): what each network function does, how the main procedures flow, how they break, and how to troubleshoot them.

Every topic combines three things:

1. **Concepts**: plain-language explanations with animated diagrams.
2. **Flows**: the message sequence of the procedure, step by step.
3. **Scenarios**: a realistic failure, what happens, what is affected, where to start troubleshooting, and how to mitigate and fix it.

## How to read this repo

- Start with the topics in order; each one builds on the previous.
- Acronyms keep their English expansion on first use in every page (for example, AMF = Access and Mobility Management Function).
- Every page separates what a **3GPP standard defines** from what is **implementation or vendor specific**.
- Every topic ends with its own references section.

## Topics

| # | Topic | Status |
|---|-------|--------|
| 01 | [5G registration (UE, gNB, AMF, AUSF, UDM, NRF)](docs/01-5g-registration/README.md) | draft |
| 02 | 5G PDU session establishment (SMF, UPF, PCF, PFCP) | planned |

More topics are added as they are written, one branch and one pull request per topic.

## Repository layout

```
docs/
  _templates/       topic and scenario templates
  NN-topic-name/
    README.md       concept, flow, references
    diagrams/       animated SVG diagrams
    scenarios/      failure scenarios with troubleshooting and fixes
```

## Accuracy note

Message names, timers and cause codes are verified against the specifications before they are written down. If something here disagrees with the current spec, the spec wins; please open an issue.

## References and credits

- 3GPP specifications archive: https://www.3gpp.org/ftp/Specs/archive/
- TS 23.501: System architecture for the 5G System (5GS)
- TS 23.502: Procedures for the 5G System (5GS)
- TS 24.501: Non-Access-Stratum (NAS) protocol for 5GS
- TS 38.413: NG Application Protocol (NGAP)
- TS 29.244: Interface between the Control Plane and the User Plane nodes (PFCP)
- TS 23.401: GPRS enhancements for E-UTRAN access (EPC)
- RFC 6733, Diameter Base Protocol: https://www.rfc-editor.org/rfc/rfc6733

Topic-specific references are listed at the end of each topic page.
- Glossary: [docs/glossary.md](docs/glossary.md)
- Roadmap: [ROADMAP.md](ROADMAP.md)
- Sources: [docs/references.md](docs/references.md)
