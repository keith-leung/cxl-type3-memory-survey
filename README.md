# A Systematic Survey of CXL Type-3 Devices: Evolution, Architectures, and Future Directions for Memory-Intensive Computing

**Dawen Liang** · College of Engineering and Computer Science, Syracuse University

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

## Abstract

The rapid growth of memory-intensive workloads, such as trillion-parameter language models and in-memory databases that process petabytes of data, has revealed fundamental limitations in traditional memory architectures. Compute Express Link (CXL), a cache-coherent interconnect built on PCIe, introduces Type-3 memory expanders. These expanders create a new layer between local DRAM and storage, providing byte-addressable, load/store-accessible capacity with a latency of 200 to 400 nanoseconds. This survey examines CXL Type-3 devices in three areas: (1) hardware architecture and performance, (2) systems software including kernel-level tiering, allocation, and virtualization support, and (3) emerging applications in in-memory databases, high-performance computing, and AI/LLM workloads. We review over 40 papers from respected venues (OSDI, ASPLOS, MICRO, SIGMOD, SOSP) published from 2022 to 2025 and highlight key challenges such as managing tail latency, ensuring security in shared memory pools, and exploring hardware-software co-design opportunities. By connecting the systems and machine learning communities, we assert that CXL Type-3 devices are crucial for the next generation of memory-intensive computing systems.

## Key Findings

- **Real CXL hardware characterization**: CXL Type-3 devices add 200–400 ns latency vs. local DRAM; NUMA emulation overstates actual CXL overhead by up to 26% (Sun et al., MICRO '23)
- **Cold memory dominance**: 55–80% of datacenter memory is cold at Meta's production fleet, making CXL tiering highly effective (Maruf et al., ASPLOS '23)
- **Database workloads lead adoption**: PolarCXLMem achieves 3.27× throughput over RDMA baselines in Alibaba's production cloud-native databases (Yang et al., SIGMOD '25 Best Paper)
- **Tiering evolution**: Page-fault promotion (TPP) → pressure-based offloading (TMO) → loaded-latency balancing (Colloid) → non-exclusive caching (NOMAD), each addressing increasingly fine-grained aspects of CXL memory management
- **AI-CXL convergence**: Memory-augmented LLM architectures (Engram) exhibit deterministic, Zipfian, read-dominated access patterns that naturally fit CXL's byte-addressable, prefetchable, cache-coherent memory
- **36 papers** reviewed from top-tier venues across systems, architecture, and database communities (2009–2025)

## Survey Scope

| Section | Topic | Key Systems |
|---------|-------|-------------|
| §2 Background | CXL protocols, pre-CXL disaggregation | CXL 1.0–4.0, Lim et al. (ISCA '09, HPCA '12), Clio |
| §3 Hardware | Architecture, performance, pooling | Demystifying CXL, Melody, DirectCXL, Pond, DRack, Oasis |
| §4 Systems Software | Tiering, allocation, virtualization | TPP, TMO, Colloid, NOMAD, Memstrata, CXL-SHM, CXLfork |
| §5 Applications | Databases, HPC, AI/LLM | Tigon, CtXnL, PolarCXLMem, SmartQuant, CLAY, Engram |
| §6 Challenges | Latency, security, co-design | Salus, Toleo, AI-systems co-design opportunities |

## Repository Structure

```
cxl-type3-memory-survey/
├── README.md
├── LICENSE                    # CC BY 4.0
├── Paper_Final.pdf            # Compiled survey (8 pages, IEEEtran format)
├── paper/
│   ├── main.tex         # LaTeX source
│   └── references.bib         # BibTeX (51 entries, 36 cited)
└── data/
    
```

## Research Questions

| RQ | Question | Key Answer |
|----|----------|------------|
| RQ1 | What are the performance characteristics of real CXL Type-3 hardware? | 200–400 ns latency, 40 GB/s sequential read bandwidth; wide variation across implementations |
| RQ2 | How has systems software adapted to leverage CXL memory tiering? | From page-fault promotion to pressure-based, contention-aware, and non-exclusive tiering |
| RQ3 | Which application areas benefit the most from CXL Type-3 devices? | Databases (production-proven), HPC/serverless (capacity gains), AI (early but promising) |
| RQ4 | What are the key challenges for CXL adoption? | Tail latency management, shared-pool security, software ecosystem maturity |

## Related Work

This survey complements our earlier systematic literature review on I/O stack evolution:

> **A Systematic Literature Review of I/O Stack Evolution for Fully Utilizing SSDs**
> Dawen Liang and Hengbo Cai, Syracuse University
> [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18636357.svg)](https://doi.org/10.5281/zenodo.18636357)
> GitHub: [keith-leung/ullssd-iostack-kernelbypass](https://github.com/keith-leung/ullssd-iostack-kernelbypass)

While the SLR examines how the software I/O stack has evolved to keep up with fast NVMe SSDs, this survey looks one level higher in the memory hierarchy—at how CXL Type-3 devices are reshaping the boundary between DRAM and storage.

## Citation

```bibtex
@article{liang2025cxlsurvey,
  title={A Systematic Survey of {CXL} Type-3 Devices: Evolution, Architectures,
         and Future Directions for Memory-Intensive Computing},
  author={Liang, Dawen},
  year={2025},
  publisher={Zenodo},
  howpublished={\url{https://doi.org/10.5281/zenodo.XXXXXXX}},
  note={GitHub: \url{https://github.com/keith-leung/cxl-type3-memory-survey}}
}
```

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
