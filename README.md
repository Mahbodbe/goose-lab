# goose-lab — GOOSE / IEC 61850 Protocol Analyzer

> 🚧 **Status: just getting started.** This repo is a fresh scaffold — folders, docs and
> roadmap are in place, the implementation is ahead of us. Follow along as it grows.

A hands-on lab for understanding and analyzing **GOOSE**
(Generic Object-Oriented Substation Event) messaging from **IEC 61850** —
the protocol that carries protection trips and breaker statuses across
modern digital substations in under 3 ms, straight on Ethernet layer 2.

## Why

Substation automation replaced copper wires with Ethernet frames — but
TCP/IP is too slow and unpredictable for protection traffic. GOOSE solves
that with unacknowledged multicast retransmission directly over layer 2.
This project builds, parses and measures those frames with Python, and
visualizes substation topology from SCL configuration files.

## Roadmap

| Phase | Goal | Status |
|-------|------|--------|
| 1 — Parser | Parse raw GOOSE frames (`EtherType 0x88B8`, `stNum`/`sqNum`, `allData`) with scapy + unit tests | ⬜ not started |
| 2 — Latency lab | Multicast simulation, end-to-end latency/jitter histograms, `timeAllowedToLive` supervision | ⬜ not started |
| 3 — SCL graph | Parse substation SCL files, draw the topology with networkx | ⬜ not started |
| 4 — Report | 3–5 page report + demo video | ⬜ not started |

## Layout

```
goose-lab/
├── src/        # implementation (goose_parser, lab_network, scl_parser, ...)
├── frames/     # small sample pcaps only (large captures stay out of git)
├── analysis/   # latency plots (regenerated, not committed)
├── tests/      # pytest unit tests
└── docs/       # protocol notes
```

## Setup

```bash
python -m venv venv
# Windows: venv\Scripts\activate   |   Linux: source venv/bin/activate
pip install -r requirements.txt   # coming soon
```

(Windows needs [Npcap](https://nmap.org/npcap/) in WinPcap-compatible mode
for scapy to see the network card.)

## Author

**Mahbod BemaniCham** — B.Sc. Electrical Engineering (Control), Amirkabir
University of Technology (Tehran Polytechnic). SCADA/automation intern at
Modje Niroo. — [github.com/Mahbodbe](https://github.com/Mahbodbe)
