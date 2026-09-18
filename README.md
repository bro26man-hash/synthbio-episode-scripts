# SynBio Episode Scripts Archive

A curated archive for episode scripts, source materials, transcripts, and production assets related to **synthetic biology** and **biotech software tools**. This repository serves as a reference library for anyone producing educational or research content about the synbio/biotech ecosystem — capturing the tools, communities, and open questions that define the field.

> **Research compiled:** September 2026 | **Sources:** GitHub issues, repository analysis, and community documentation across 10+ active synbio/biotech open-source projects.

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

| Project | Stars | Language | Description | Link |
|---------|-------|----------|-------------|------|
| **awesome-synthetic-biology** | 223 | — | Curated list of synbio projects, articles, resources & standards | [websemantics/awesome-synthetic-biology](https://github.com/websemantics/awesome-synthetic-biology) |
| **GENtle2** | 105 | JavaScript | Web-based DNA editor for synthetic biology | [Synbiota/GENtle2](https://github.com/Synbiota/GENtle2) |
| **act (20n)** | 92 | Java/Scala | Computational platform predicting DNA edits for bioengineering; first bio-route to acetaminophen | [20n/act](https://github.com/20n/act) |
| **SynBioHub** | 84 | JavaScript/Java | Web-based repository for browsing, uploading & sharing synthetic biology designs | [SynBioHub/synbiohub](https://github.com/SynBioHub/synbiohub) |
| **iBioSim** | 67 | Java | Computer-aided design (CAD) tool for modeling, analysis & design of genetic circuits (SBML/SBOL) | [MyersResearchGroup/iBioSim](https://github.com/MyersResearchGroup/iBioSim) |
| **ART (JBEI)** | 66 | Jupyter Notebook | Machine learning tool for automated strain engineering recommendations | [JBEI/ART](https://github.com/JBEI/ART) |
| **Coral** | 32 | Python | Library & framework for specifying synthetic biology design processes | [klavinslab/coral](https://github.com/klavinslab/coral) |

### Deep Dives on the Most Active Repos

#### 🔬 SynBioHub (84 stars, BSD-2-Clause license)
- **What it does:** Web application enabling users and software to browse, upload, and share synthetic biology designs. Hosts the iGEM Registry of Standard Biological Parts and enriched *B. subtilis* and *E. coli* data.
- **Stack:** JavaScript (Node.js) + Java (Maven) + OpenLink Virtuoso (RDF triplestore)
- **Development model:** PR-based with CI (Travis + Docker integration tests via SBOLTestSuite); automatic Docker Hub publishing via GitHub Actions
- **Current issue focus (8 open issues in latest milestone SBH 1.6.2):** Data portability, interoperability, and infrastructure maintenance
  - [Issue #1756 — SubCollections does not report members in public graph](https://github.com/SynBioHub/synbiohub/issues/1756) (bug, Sep 2026)
  - [Issue #1755 — Recursive download does not follow linked collections](https://github.com/SynBioHub/synbiohub/issues/1755) (bug, Aug 2026)
  - [Issue #1754 — Legacy data in Virtuoso should be deleted](https://github.com/SynBioHub/synbiohub/issues/1754) (Aug 2026)
  - [Issue #1753 — OMEX download missing SBML file attachments](https://github.com/SynBioHub/synbiohub/issues/1753) (bug, 2 comments, Aug 2026)
  - [Issue #1752 — Private-to-public visibility change resets prefix](https://github.com/SynBioHub/synbiohub/issues/1752) (Aug 2026)
  - [Issue #1746 — Incremental updates not working with SBOLExplorer](https://github.com/SynBioHub/synbiohub/issues/1746) (bug, Jul 2026)
  - [Issue #1744 — Backend lacks OR request parsing mechanism](https://github.com/SynBioHub/synbiohub/issues/1744) (bug, Jul 2026)
  - [Issue #1693 — SendGrid email service no longer working](https://github.com/SynBioHub/synbiohub/issues/1693) (bug, Oct 2025)

> **Takeaway:** The community is seriously focused on making design data more reliably portable and interoperable across tools. OMEX bundle integrity, recursive collection resolution, and database hygiene are the pain points. This signals the ecosystem is maturing — users need dependable data pipelines.

#### 🔬 iBioSim (67 stars, Apache-2.0 license)
- **What it does:** Computer-aided design (CAD) tool for modeling, analysis, and design of genetic circuits. Imports/exports SBML (all levels/versions) and supports SBOL. Includes multi-cellular and spatial modeling support.
- **Stack:** Java + libSBML + reb2sac + GeneNet + Yosys
- **Active developers:** Lukas Buecherl, Pedro Fontanarrosa, Chris Myers
- **Current issue focus (305+ open issues):** Cross-platform compatibility, Java dependency management, and SynBioHub integration
  - [Issue #640 — Java exception (NoClassDefFoundError with Apache Jena)](https://github.com/MyersResearchGroup/iBioSim/issues/640) (Aug 2025)
  - [Issue #639 — Can't upload SynBioHub design](https://github.com/MyersResearchGroup/iBioSim/issues/639) (May 2025)
  - [Issue #638 — Unable to run iBioSim 3.2.0 in Mac](https://github.com/MyersResearchGroup/iBioSim/issues/638) (May 2025)
  - [Issue #637 — Unable to generate models automatically (Xerces/Jena crash)](https://github.com/MyersResearchGroup/iBioSim/issues/637) (6 comments, Jan 2025)
  - [Issue #635 — I cannot open iBioSim on Windows 11](https://github.com/MyersResearchGroup/iBioSim/issues/635) (4 comments, Jan 2025)
  - [Issue #634 — Bug importing file and when starting](https://github.com/MyersResearchGroup/iBioSim/issues/634) (6 comments, Sep 2024)
  - [Issue #632 — Can't connect to LCP SynBioHub](https://github.com/MyersResearchGroup/iBioSim/issues/632) (Apr 2024)

**Key error from #637 (most discussed):**
```
java.lang.NoClassDefFoundError: Could not initialize class org.apache.jena.query.ARQ
Caused by: java.lang.NoClassDefFoundError: org/apache/xerces/util/XMLChar
```
This is a transitive dependency conflict — Apache Jena can't initialize because Xerces is missing or conflicting. Users hitting this when trying to generate models from SBOL designs via SynBioHub integration.

**Community discussion highlights from #637:**
- **Hatem-synbio** (reporter): Was debugging Kenzo's toggle switch model and following the iBioSim tutorial on page 94 for automatic model generation. Could share the COMBINE archive on Slack.
- **cjmyers (maintainer)**: Asked which SynBioHub instance was being used; later identified the root cause — *"I'm pretty sure the issue has to do with trying to create a model using iGEM parts. iGEM parts do not have interaction information, so it is impossible to generate a model. Granted, there should be a better error than an exception. To actually test this better, should use the Cello library."*

> **Takeaway:** Desktop-based synbio CAD tools struggle with Java dependency management and OS-specific behavior. The #637 discussion reveals a deeper issue: iBioSim fails with a cryptic Jena/Xerces crash when the underlying data (iGEM parts) lacks the required interaction information — rather than giving a user-friendly error. This signals a strong opportunity for containerized or web-based alternatives with better error handling.

#### 🔬 20n/act (92 stars, GPL-3.0 license)
- **What it does:** Data aggregation and prediction system for bioengineering. Predicts DNA insertions into cells that modify them to produce target molecules ("bioreachables"). Predicted the first bio-route to acetaminophen/Tylenol.
- **Stack:** Java/Scala + Python (deep learning for LCMS) + R (visualization)
- **Key modules:** Installer, Reaction Operator inference, SAR inference, Biointerpretation, Reachables computation, Cascades computation, DNA designer, NLP for enzymatic biochemistry, patent search, Bioreachables wiki
- **Current issue focus:** No open issues found — the project appears stable but is primarily maintained internally by 20n Inc.

#### 🔬 GENtle2 (105 stars, — license)
- **What it does:** Web-based DNA editor for synthetic biology. A re-think of the original GENtle desktop application for the web. Written in JavaScript (Node.js + Express + Gulp).
- **Current issue focus (75+ open issues, many dating to 2015):** Persistent UI/UX bugs and feature gaps
  - [Issue #253 — Jumping annotations](https://github.com/Synbiota/GENtle2/issues/253) (Sep 2015)
  - [Issue #252 — Anchor and Cap selections won't change](https://github.com/Synbiota/GENtle2/issues/252) (Sep 2015)
  - [Issue #251 — Spacing button doesn't work](https://github.com/Synbiota/GENtle2/issues/251) (Sep 2015)
  - [Issue #250 — BLAST show button doesn't do anything](https://github.com/Synbiota/GENtle2/issues/250) (Sep 2015)
  - [Issue #247 — SequenceModel should validate stickyEnds](https://github.com/Synbiota/GENtle2/issues/247) (Improvement, Aug 2015)
  - [Issue #245 — Chromatograph vertical scroll bar display issues](https://github.com/Synbiota/GENtle2/issues/245) (Bug, Deathcon 1, Aug 2015)
  - [Issue #243 — Ghost tooltip (Designer: remove single part)](https://github.com/Synbiota/GENtle2/issues/243) (Bug, Deathcon 3, Aug 2015)

**Community discussion highlights from #162:**
- **ghost (reporter):** "When selection is made and copied through context menu the selection disappears." — Related to earlier optimization #129, author said "I'll fix it ASAP" but it remains open since 2014.
- **#159 (6 comments):** "Tracking shapes in `Artist`" — Refactor milestone, suggesting the canvas event system needs a fundamental rethink.
- The majority of open issues are tagged with **Refactor** milestones like "Canvas events & RES/annotation cards information" and "Sequence opening/editing," indicating the maintainer (alexandremeunier) has a modernization plan but limited bandwidth.

> **Takeaway:** Even well-established tools have significant UI debt. The GENtle project's long-standing unaddressed issues suggest the community is waiting for a modernized, web-native replacement. GENtle2's rewrite is a step in this direction but still has its own open issues. The refactor milestones suggest awareness of the problems, but the 10+ year gap between issue creation and last update signals a community starved for contributors.

#### 🔬 Coral (32 stars, MIT license)
- **What it does:** Python library for encoding the process of designing synthetic DNA constructs. Mirrors traditional GUI-based design steps (ApE, j5, Benchling) as operations on data structures. Enables iterative design through analysis modules and connects seamlessly to outside libraries.
- **Stack:** Python (works with PyPy + numpy), Biopython, optional matplotlib/intermine
- **Key feature:** Encodes synthetic DNA design rules into core sequence data types (`DNA`, `RNA`, `Peptide`)
- **Current issue focus:** Actively maintained, recent updates (June 2026)

> **Takeaway:** Coral is a rare example of a well-maintained, open-source Python library for synbio design automation. It's a great tool for programmatic DNA design and a good reference for how to structure design-as-code workflows.

### Supporting Tools & Frameworks

Beyond the headline projects, the synbio ecosystem includes a rich set of supporting tools that are worth knowing about:

| Tool | Category | Description | Link |
|------|----------|-------------|------|
| **Cello/CelloCad** | Genetic circuit design | Logic-gate-based genetic circuit design automation | [CIDARLAB/cello](https://github.com/CIDARLAB/cello) |
| **Eugene** | Design language | Human- and machine-readable language for specifying biological system designs | [eugenecad.org](http://eugenecad.org/) |
| **SBOL Canvas** | Visualization | Genetic circuit schematic building using SBOL standard | [sbolcanvas.org](https://sbolcanvas.org/) |
| **SnapGene** | Plasmid simulation | Visual plasmid construction + simulation (commercial) | [snapgene.com](https://www.snapgene.com/) |
| **DNA Chisel** | Codon optimization | Codon optimization and solving sequence constraints | [Edinburgh-Genome-Foundry/DnaChisel](https://github.com/Edinburgh-Genome-Foundry/DnaChisel) |
| **PySB** | Systems biology modeling | Systems biology modeling in Python | [pysb.org](https://pysb.org/) |
| **COPASI** | Metabolic modeling | Modeling biochemical reaction networks | [copasi.org](https://copasi.org/) |
| **COBRA** | Metabolic modeling | Whole-cell metabolic modeler (E. Coli, etc.) | [opencobra.github.io](https://opencobra.github.io/) |
| **BioNetGen** | Rule-based modeling | Structure-based modeling of biochemical reaction networks | [RuleWorld/bionetgen](https://github.com/RuleWorld/bionetgen) |
| **BioCRNpyler** | CRN compiler | Biomolecular chemical reaction network compiler | [BuildACell/bioCRNpyler](https://github.com/BuildACell/bioCRNpyler) |
| **KBase** | Analysis platform | "AWS for systems bio analysis," hosted by DOE | [kbase.us](https://kbase.us) |

### Learning & Resource Hubs

| Project | Stars | Description | Link |
|---------|-------|-------------|------|
| **Learn_Synthetic_Biology** | 157 | Educational resources for getting started in synbio | [llSourcell/Learn_Synthetic_Biology](https://github.com/llSourcell/Learn_Synthetic_Biology) |
| **awesome-deep-learning-4-life-sciences** | 168 | Deep learning resources for life sciences (biotech & pharma focus) | [virtualramblas/awesome-deep-learning-4-life-sciences](https://github.com/virtualramblas/awesome-deep-learning-4-life-sciences) |
| **Machine-Learning-in-Biotechnology** | 106 | ML in biotechnology using Python (Packt Publishing companion) | [PacktPublishing/Machine-Learning-in-Biotechnology-and-Life-Sciences](https://github.com/PacktPublishing/Machine-Learning-in-Biotechnology-and-Life-Sciences) |
| **BioTech-Resources** | 16 | Resources for learning biotech, biology, synbio, genomics & bioinformatics | [robertosolari/BioTech-Resources](https://github.com/robertosolari/BioTech-Resources) |

### Standards & Interoperability

- **SBOL (Synthetic Biology Open Language)** — Standard interchange format for design information exchange. See [SynBioDex/libSBOLj](https://github.com/SynBioDex/libSBOLj) (Java library) and [SBOL-specification](https://github.com/SynBioDex/SBOL-specification)
- **SBML (Systems Biology Markup Language)** — Standards for mathematical models of biological systems, supported by iBioSim and many other tools
- **iGEM Registry** — Registry of Standard Biological Parts, accessible via SynBioHub
- **OMEX (Open Microscopy Environment)** — Format used by SynBioHub for bundled downloads (SBOL + SBML + other data)

---

## What the Community Is Currently Working On & Concerned About

Based on recent open issues across the top projects, here are the themes dominating community attention:

### 1. SBOL Data Handling & Interoperability (SynBioHub)

The SynBioHub team is actively fixing bugs around data portability — a sign the ecosystem is maturing and users need dependable data pipelines:

| Issue | Title | Labels | Date | Summary |
|-------|-------|--------|------|---------|
| [#1756](https://github.com/SynBioHub/synbiohub/issues/1756) | SubCollections does not report members in public graph | bug | Sep 2026 | Public graph views don't show members of sub-collections |
| [#1755](https://github.com/SynBioHub/synbiohub/issues/1755) | Recursive download does not follow linked collections | bug | Aug 2026 | Downloads don't traverse linked collection references |
| [#1754](https://github.com/SynBioHub/synbiohub/issues/1754) | Legacy data in Virtuoso should be deleted | — | Aug 2026 | Database cleanup needed for deprecated entries |
| [#1753](https://github.com/SynBioHub/synbiohub/issues/1753) | OMEX download missing SBML file attachments | bug | Aug 2026 | OMEX export missing SBML attachments (2 comments, community affected) |
| [#1752](https://github.com/SynBioHub/synbiohub/issues/1752) | Private-to-public visibility resets prefix | — | Aug 2026 | Changing visibility from private to public resets the URI prefix |
| [#1746](https://github.com/SynBioHub/synbiohub/issues/1746) | Incremental updates not working with SBOLExplorer | bug | Jul 2026 | SBOLExplorer can't pull incremental updates from SynBioHub |
| [#1744](https://github.com/SynBioHub/synbiohub/issues/1744) | Backend should parse OR requests | bug | Jul 2026 | Backend lacks OR (or) query parsing support |
| [#1693](https://github.com/SynBioHub/synbiohub/issues/1693) | SendGrid email service no longer working | bug | Oct 2025 | Email notification backend broken |

**Community discussion highlights from #1753:**
- **cjmyers (maintainer):** Explained that the root cause is *"Model->source is not followed to find all files. However, the SBML file will come in an OMEX download of the Attachment object or the Collection that has the Attachment as a member."*
- Also noted: *"For SynBioSuite, fixed this by making the SBML file an attachment of the Model object."* — suggesting the fix is to restructure how SBML files are referenced within OMEX bundles.

> **Takeaway:** The community is seriously focused on making design data more reliably portable and interoperable across tools. OMEX bundle integrity, recursive collection resolution, and database hygiene are the pain points. This signals the ecosystem is maturing — users need dependable data pipelines.

### 2. Cross-Platform Compatibility & Stability (iBioSim)

iBioSim users are hitting friction on multiple fronts — 305+ open issues suggest significant maintenance burden:

| Issue | Title | Labels | Date | Summary |
|-------|-------|--------|------|---------|
| [#640](https://github.com/MyersResearchGroup/iBioSim/issues/640) | A Java exception has occurred | — | Aug 2025 | Java runtime crash |
| [#639](https://github.com/MyersResearchGroup/iBioSim/issues/639) | Can't upload SynBioHub design | — | May 2025 | SBOL upload integration failure |
| [#638](https://github.com/MyersResearchGroup/iBioSim/issues/638) | Unable to run iBioSim 3.2.0 in Mac | — | May 2025 | macOS compatibility break |
| [#637](https://github.com/MyersResearchGroup/iBioSim/issues/637) | Unable to generate models automatically | — | Jan 2025 | `NoClassDefFoundError: org.apache.xerces.util.XMLChar` — Apache Jena init failure. 6 comments, active discussion. |
| [#635](https://github.com/MyersResearchGroup/iBioSim/issues/635) | I cannot open iBioSim on Windows 11 | — | Jan 2025 | Windows 11 launch failure (4 comments) |
| [#634](https://github.com/MyersResearchGroup/iBioSim/issues/634) | Bug importing file and when starting | — | Sep 2024 | Import/startup crash (6 comments) |
| [#632](https://github.com/MyersResearchGroup/iBioSim/issues/632) | Can't connect to LCP SynBioHub | — | Apr 2024 | SynBioHub connection handshake failure |
| [#631](https://github.com/MyersResearchGroup/iBioSim/issues/631) | Problem with External Components | — | Mar 2024 | External component integration problems |

> **Takeaway:** Desktop-based synbio CAD tools struggle with Java dependency management and OS-specific behavior. The #637 discussion reveals a deeper issue: iBioSim fails with a cryptic Jena/Xerces crash when the underlying data (iGEM parts) lacks the required interaction information — rather than giving a user-friendly error. This signals a strong opportunity for containerized or web-based alternatives with better error handling.

### 3. UI/UX Bugs in DNA Editors (GENtle2)

GENtle2's 75+ open issues (many dating to 2015) reveal persistent UX debt:

| Issue | Title | Labels | Date |
|-------|-------|--------|------|
| [#253](https://github.com/Synbiota/GENtle2/issues/253) | Jumping annotations | — | Sep 2015 |
| [#252](https://github.com/Synbiota/GENtle2/issues/252) | Anchor and Cap selections won't change | — | Sep 2015 |
| [#251](https://github.com/Synbiota/GENtle2/issues/251) | Spacing button doesn't work | — | Sep 2015 |
| [#250](https://github.com/Synbiota/GENtle2/issues/250) | BLAST show button doesn't do anything | — | Sep 2015 |
| [#247](https://github.com/Synbiota/GENtle2/issues/247) | SequenceModel should validate stickyEnds | Improvement | Aug 2015 |
| [#245](https://github.com/Synbiota/GENtle2/issues/245) | Chromatograph vertical scroll bar display issues | Bug, Deathcon 1 | Aug 2015 |
| [#243](https://github.com/Synbiota/GENtle2/issues/243) | Ghost tooltip (Designer: remove single part) | Bug, Deathcon 3 | Aug 2015 |

> **Takeaway:** Even well-established tools have significant UI debt. The GENtle project's long-standing unaddressed issues suggest the community is waiting for a modernized, web-native replacement. GENtle2's rewrite is a step in this direction but still has 75+ open issues of its own.

### 4. Machine Learning & Automated Design (ART, 20n/act)

- **ART** provides **probabilistic strain recommendations** without requiring full mechanistic understanding — a paradigm shift from trial-and-error to computational-directed metabolic engineering. Uses MCMC sampling and Bayesian optimization.
- **20n/act** demonstrates **end-to-end DNA design automation**, having predicted the first bio-route to acetaminophen. Its 10-module pipeline covers data integration, reaction inference, reachability computation, cascade enumeration, DNA design, NLP, and cost modeling.

> **Takeaway:** The field is moving from manual, intuition-driven engineering toward computational, ML-augmented design pipelines. However, ART's source code is private (access via license), and 20n/act is maintained internally — suggesting a gap for open-source alternatives.

### 5. Community Coordination & Resource Curation (awesome-synthetic-biology)

- The curated list (223 stars, 27 forks) remains the **central hub** for discovering tools, standards (SBOL, SBML), programming languages (Verilog/Cello, Eugene), and hardware (BioHackAcademy, 3DuF)
- Community contributions are welcome via a clear contributing guide
- Covers the full stack: software tools → standards → hardware → education → interviews

> **Takeaway:** As the ecosystem fragments across dozens of specialized tools, curated indexes and standards become increasingly critical glue. Content creators should reference this list as the canonical starting point.

---

## Emerging Themes & Opportunities for Content

Based on the research above, here are the stories the community is telling right now:

1. **"The Interoperability Crisis"** — SynBioHub's open issues are almost all about data not moving correctly between tools (OMEX bundles missing files, recursive downloads breaking, incremental sync failing). The #1753 discussion reveals the root cause: `Model->source` references aren't traversed during export, so SBML attachments get orphaned. This is the *current* bottleneck in the synbio workflow.

2. **"The Desktop Tool Bottleneck"** — iBioSim's 305+ issues and GENtle2's 75+ issues both point to the same problem: desktop-based CAD tools are struggling with Java dependency hell, OS compatibility, and aging UI codebases. The #637 discussion shows even the maintainer (cjmyers) acknowledges the error message is unhelpful — *"there should be a better error than an exception."* Web-native and containerized tools are the future.

3. **"From Hand Engineering to Computational Design"** — ART and 20n/act represent a fundamental shift: instead of designing one construct at a time, you enumerate all possible designs computationally and pick the best. This is the "DeepSeek moment" for synbio.

4. **"The Missing Open-Source Stack"** — ART's code is private, 20n/act is internally maintained, and GENtle2 has a fractured community. There's a clear opportunity for an open-source, web-native, ML-integrated design tool that the community can actually build and modify together.

5. **"Standards Are Maturing, but Pipelines Aren't"** — SBOL and SBML are well-defined standards, but the *pipelines* that move data between tools (OMEX exports, recursive downloads, incremental sync) are broken. The standards exist; the plumbing doesn't.

---

## Repository Structure

This archive is organized by episode/theme:

```
episode-scripts-archive/
├── README.md
├── episodes/
│   ├── episode-01-genome-editing/
│   ├── episode-02-synbio-tools/
│   ├── episode-03-DNA-data-storage/
│   ├── episode-04-interoperability-crisis/
│   ├── episode-05-ml-designed-biology/
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
- [SBML](https://sbml.org) — Systems Biology Markup Language
- [BioModels](https://www.ebi.ac.uk/biomodels) — Database of mathematical models
- [3DuF](https://3duf.org) — Open-source microfluidics design tool
- [BioHackAcademy](https://biohackacademy.github.io) — Community hardware/course platform
- [awesome-synthetic-biology](https://github.com/websemantics/awesome-synthetic-biology) — Curated list of all things synbio

---

*This archive was compiled from active GitHub research on the synthetic biology and biotech software ecosystem, capturing the tools, standards, and community concerns as of September 2026. Research methodology: repository search, star-ranked analysis, open-issue triage across 10+ projects, detailed issue inspection of 15+ high-priority bugs across 5 thematic categories, and direct review of community discussion threads on the most-reported issues.*
