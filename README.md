# SynBio Episode Scripts Archive

A curated archive for episode scripts, source materials, transcripts, and production assets related to **synthetic biology** and **biotech software tools**. This repository serves as a reference library for anyone producing educational or research content about the synbio/biotech ecosystem — capturing the tools, communities, and open questions that define the field.

---

## Purpose

This archive exists to:

- **Document** the synthetic biology and biotech software landscape as it evolves
- **Preserve** episode scripts and source materials tied to specific tools, standards, and research projects
- **Connect** content creators with the active open-source communities and their current concerns
- **Serve as a starting point** for anyone wanting to understand what the synbio community is building and struggling with

---

## Key Synbio & Biotech Tools & Communities

Below are the most active open-source projects we've identified, along with the issues the community is currently focused on.

### Core Tools

| Project | Stars | Description | Link |
|---------|-------|-------------|------|
| **awesome-synthetic-biology** | 223 | Curated list of synbio projects, articles, resources & standards | [websemantics/awesome-synthetic-biology](https://github.com/websemantics/awesome-synthetic-biology) |
| **GENtle2** | 105 | Web-based DNA editor for synthetic biology (JavaScript) | [Synbiota/GENtle2](https://github.com/Synbiota/GENtle2) |
| **act (20n)** | 92 | Computational platform predicting DNA edits for bioengineering; first bio-route to acetaminophen | [20n/act](https://github.com/20n/act) |
| **SynBioHub** | 84 | Web-based repository for browsing, uploading & sharing synthetic biology designs | [SynBioHub/synbiohub](https://github.com/SynBioHub/synbiohub) |
| **iBioSim** | 67 | Computer-aided design (CAD) tool for modeling, analysis & design of genetic circuits (Java, SBML/SBOL) | [MyersResearchGroup/iBioSim](https://github.com/MyersResearchGroup/iBioSim) |
| **ART (JBEI)** | 66 | Machine learning tool for automated strain engineering recommendations | [JBEI/ART](https://github.com/JBEI/ART) |
| **Coral** | 32 | Library & framework for specifying synthetic biology design processes (Python) | [klavinslab/coral](https://github.com/klavinslab/coral) |

### Learning & Resource Hubs

| Project | Stars | Description | Link |
|---------|-------|-------------|------|
| **Learn_Synthetic_Biology** | 157 | Educational resources for getting started in synbio | [llSourcell/Learn_Synthetic_Biology](https://github.com/llSourcell/Learn_Synthetic_Biology) |
| **awesome-deep-learning-4-life-sciences** | 168 | Deep learning resources for life sciences (biotech & pharma focus) | [virtualramblas/awesome-deep-learning-4-life-sciences](https://github.com/virtualramblas/awesome-deep-learning-4-life-sciences) |
| **BioTech-Resources** | 16 | Resources for learning biotech, biology, synbio, genomics & bioinformatics | [robertosolari/BioTech-Resources](https://github.com/robertosolari/BioTech-Resources) |
| **Machine-Learning-in-Biotechnology** | 106 | ML in biotechnology using Python (Packt Publishing companion) | [PacktPublishing/…](https://github.com/PacktPublishing/Machine-Learning-in-Biotechnology-and-Life-Sciences) |

### Standards & Interoperability

- **SBOL (Synthetic Biology Open Language)** — Standard interchange format for design information exchange. See [SynBioDex/libSBOLj](https://github.com/SynBioDex/libSBOLj) (Java library) and [SBOL-specification](https://github.com/SynBioDex/SBOL-specification)
- **SBML (Systems Biology Markup Language)** — Standards for mathematical models of biological systems, supported by iBioSim and many other tools
- **iGEM Registry** — Registry of Standard Biological Parts, accessible via SynBioHub

---

## What the Community Is Currently Working On & Concerned About

Based on recent open issues across the top projects, here are the themes dominating community attention:

### 1. SBOL Data Handling & Interoperability (SynBioHub)
The SynBioHub team is actively fixing bugs around:
- **SubCollections not reporting members** in public graph views (issue #1756, milestone SBH 1.6.2)
- **Recursive downloads** not following linked collections (#1755)
- **OMEX downloads** missing SBML files (#1753)
- **Incremental updates** not working with SBOLExplorer (#1746)
- **Legacy data cleanup** in Virtuoso database (#1754)

> **Takeaway:** The community is seriously focused on making design data more reliably portable and interoperable across tools — a sign that the ecosystem is maturing and users need dependable data pipelines.

### 2. Cross-Platform Compatibility & Stability (iBioSim)
iBioSim users are hitting friction on multiple fronts:
- **Java crashes** (`NoClassDefFoundError` with Apache Jena) when generating models from SBOL (#637)
- **Mac & Windows 11 compatibility** issues (#638, #635)
- **SBOL import failures** and reconnection issues to SynBioHub (#639, #632)
- **External component integration** problems (#631)

> **Takeaway:** Desktop-based synbio CAD tools struggle with Java dependency management and OS-specific behavior. This signals an opportunity for containerized or web-based alternatives.

### 3. UI/UX Bugs in DNA Editors (GENtle2)
GENtle2's open issues (though older, still unaddressed) reveal persistent UX challenges:
- **Jumping annotations** during rapid scrolling on Mac (#253)
- **BLAST and toolbar buttons** not responding (#250, #252)
- **Sequence model validation** gaps (#247)
- **Ghost tooltips** and UI rendering glitches (#243)

> **Takeaway:** Even well-established tools have lingering UI debt. Web-based editors and newer projects are positioning themselves as the path forward.

### 4. Machine Learning & Automated Design (ART, 20n/act)
- ART provides **probabilistic strain recommendations** without requiring full mechanistic understanding — a paradigm shift in metabolic engineering
- 20n/act demonstrates **end-to-end DNA design automation**, having predicted the first bio-route to acetaminophen

> **Takeaway:** The field is moving from manual, intuition-driven engineering toward computational, ML-augmented design pipelines.

### 5. Community Coordination & Resource Curation (awesome-synthetic-biology)
- The curated list remains the **central hub** for discovering tools, standards (SBOL, SBML), programming languages (Verilog/Cello, Eugene), and hardware (BioHackAcademy, 3DuF)
- Community contributions are welcome via a clear contributing guide

> **Takeaway:** As the ecosystem fragments across dozens of specialized tools, curated indexes and standards become increasingly critical glue.

---

## Repository Structure

This archive is organized by episode/theme. Suggested subdirectories:

```
synthbio-episode-scripts/
├── README.md
├── episodes/
│   ├── episode-01-genome-editing/
│   ├── episode-02-synbio-tools/
│   ├── episode-03-DNA-data-storage/
│   └── ...
├── source-materials/
│   ├── presentations/
│   ├── datasets/
│   └── references/
└── transcripts/
```

Add a `CONTRIBUTING.md` with format and naming conventions.

---

## Contributing

Contributions are welcome! To add materials:

1. Fork this repository
2. Create a new branch for your episode or addition
3. Add your scripts, source materials, or transcripts under the appropriate directory
4. Submit a pull request

---

## License

This archive is released under the [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/), same as the awesome-synthetic-biology list. Individual episode scripts may carry their own licenses — check each episode directory for details.

---

## Related Communities & Links

- [SynBioHub](https://synbiohub.org) — Design repository & sharing platform
- [Addgene](https://www.addgene.org) — Nonprofit plasmid repository
- [iGEM Registry](http://parts.igem.org) — Standard Biological Parts
- [SBOL Standard](https://sbolstandard.org) — Synthetic Biology Open Language
- [BioModels](https://www.ebi.ac.uk/biomodels) — Database of mathematical models
- [3DuF](https://3duf.org) — Open-source microfluidics design tool
- [BioHackAcademy](https://biohackacademy.github.io) — Community hardware/course platform

---

*This archive was compiled from active GitHub research on the synthetic biology and biotech software ecosystem, capturing the tools, standards, and community concerns as of 2025–2026.*
