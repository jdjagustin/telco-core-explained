# Roadmap

Status: done = `[x]`, pending = `[ ]`. This file is updated in the same commit that finishes an item.

## Topics

| # | Topic | Status |
|---|---|---|
| 01 | 5G registration (UE, gNB, AMF, AUSF, UDM, NRF) | in progress |
| 02 | 5G PDU session (SMF, UPF, PCF, PFCP over N4) | planned |
| 03 | 4G attach (eNodeB, MME, SGW, PGW, HSS) | planned |
| 04 | Diameter (S6a, Gx, Gy) | planned |
| 05 | IMS and SIP | planned |
| 06 | Telco workloads on Kubernetes | planned |
| 07 | Troubleshooting method (stabilize, scope, hypotheses, mitigate vs. fix, post-incident review) | planned |

## Topic 01 checklist

- [x] The cast and the reference points (N1, N2, N8, N12, N13)
- [x] Registration flow, animated diagram with hover explanations
- [x] Protocol stack per hop (RRC, NGAP over SCTP, HTTP/2 + JSON over TCP)
- [x] Glossary with back-links
- [x] Interface map (Mermaid)
- [ ] 4G equivalents table (eNodeB, MME, HSS)
- [ ] Scenario: the AMF is overloaded and the platform cannot create more instances
- [ ] Scenario: a subset of subscribers cannot register
- [ ] Verify every message name and clause number against the specs one last time

## Cross-cutting

- [ ] Choose a license
- [ ] Dark-theme HTML version of each topic, generated from the same Markdown
- [ ] Slide deck per topic, with a final references slide
- [ ] Add a scenario page to every topic where it applies (template in `docs/_templates/scenario.md`)
