# Dissertation Notebook

**Title:** Verifiable Content Authenticity and Anti-Deepfake Provenance on the European Blockchain Services Infrastructure

**Institution:** University of Aveiro, Department of Electronics, Telecommunications and Informatics (DETI)  
**Student:** João Varela  
**Supervisor:** Professor Paulo Bartolomeu  
**Co-supervisor:** Professor André Zúquete

I record my weekly activities in this notebook. My dissertation objective is to design and prototype a framework integrating C2PA content credentials with EBSI to establish a verifiable chain of trust for digital content. I maintain my [dissertation sources](https://github.com/joaovarela14/Thesis_Latex) separately and use Overleaf for shared writing.

## Week 07 — PKCS#11 signing and content-versioning architecture

**9–15 November 2026**

### Activities completed

- I reviewed the Besu prototype, including the roles of validators and producer accounts, persistent node data, and the distinction between Besu software and EBSI infrastructure. In the supervisor meeting, I agreed with Professor Paulo Bartolomeu to continue local Besu experiments while pursuing EBSI access. I confirmed that an automatic acknowledgement of my request existed, but sandbox access remained unresolved.
- I analysed the *SmartCMD* dissertation Professor André Zúquete shared and reviewed the previous Edufiable integration. I found that the CMD OAuth flow provided authentication and identity attributes, rather than remote data signing. In the official CMD signing implementation I examined, RSA-PSS was unsupported, preventing direct use of that path for a C2PA claim signature. I prioritised the Citizen Card integration and did not make live CMD signing requests.
- I implemented a separate Rust external signer using the existing `c2patool --signer-path` interface and a PKCS#11 module. I added token and certificate inspection, certificate selection by fingerprint, certificate-chain handling, and RSA-PSS and ECDSA signing, with independent verification before returning each signature.
- I validated the signer with SoftHSM: nine Rust tests and eighteen integration checks passed, including authentication failures, missing tokens, incomplete chains, and ambiguous certificate selection. I created C2PA-signed images with both algorithms; they returned `Valid` without configured trust and `Trusted` with the laboratory root. These results demonstrate software-token integration; I have not tested the physical Citizen Card or its certificate.
- I prepared an initial architecture proposal for preserving and verifying content edits using C2PA and Besu, with traceability and cost as the main criteria. I proposed keeping published files and supporting evidence outside the blockchain and registering hashes and version links on the ledger. I addressed configurable registration granularity, branches, permissions, consistency with C2PA ingredients, and recovery after publication failures. I also assembled the original and signed sample images for future crop and resize experiments.
- I created six editable diagrams in Miro covering the architecture, publication sequence, data model, verification, version branches and cost, and failure recovery. I checked the diagram sources and local SVG/PNG renderings. The diagrams describe a proposal; I did not implement the new editing workflow or contract extensions this week.

### Ongoing work and next steps

- I will validate the signer with a USB reader and the physical Citizen Card, checking supported mechanisms, certificate compatibility, and trust separately. SoftHSM results do not establish compatibility with the card.
- I will discuss the architecture and diagrams with my supervisors and demonstrate real image edits linked through C2PA and Besu. The existing two-version experiment changes the manifest without changing the pixels; the crop and resize workflow remains to be implemented and evaluated.
- I will define the link between ledger accounts and signer identity, the evidence required for historical verification, and the evaluation of registration cost. I will continue following up on EBSI access while using Besu for local development.

## Week 06 — C2PA signing, blockchain alternatives, and Besu experiments

**2–8 November 2026**

### Activities completed

- I refined the practical guide for creating a local certification chain and signing C2PA manifests. I clarified the roles of private keys, certificates, trust anchors, and certificate usage settings, and demonstrated signing and verification with my local test certificates during the supervisor meeting.
- I investigated signing with the Citizen Card through PKCS#11. I confirmed that the local `c2patool` supports an external signing program through `--signer-path`, identifying a possible bridge to the card's middleware. I did not implement this bridge or test a physical card; algorithm and certificate compatibility remain to be checked.
- I discussed the pending EBSI sandbox request with my supervisors and the possibility of exploring an existing environment. I reviewed alternatives to EBSI, including consortium, public, and hybrid approaches, focusing on authorised registration, open verification, traceability, and cost. Besu emerged as a practical option for local experiments without waiting for external admission; the final technology and architecture remained open.
- I tested a local Besu network with four QBFT validators in Docker and a contract for authorised registration of linked provenance events. I validated two C2PA-signed JPEG versions against the local test root, registered their complete-file SHA-256 hashes, and linked the second record to the first. The second version added a manifest referencing the first without changing the pixels.
- I confirmed that all four local endpoints returned the registered data without a wallet or authentication, and that writes from an unauthorised account or after removal of a producer's authorisation were rejected. Earlier records remained accessible. These tests did not establish certificate revocation status or historical signature validity.
- I prepared a reusable Besu environment with the contract, scripts, Docker configuration, and persistent node data. I repeated the experiment and confirmed that records survived restarting the nodes, including records from the initial run. I preserved the original source image and stopped the containers after testing.

### Ongoing work and next steps

- I will develop a first architecture proposal for recording content changes, defining the minimum ledger information, links between versions, and registration granularity while considering cost.
- I will define how blockchain accounts relate to C2PA signer identity and producer accreditation, and what evidence must be preserved for historical verification.
- I will continue following up on EBSI access and comparing infrastructure options. The local Besu experiment does not establish institutional trust, a public verification service, or independence between operators: all four validators run on one computer.
- I will explore the Citizen Card integration further, beginning with certificate and algorithm compatibility, and prepare the Besu workflow for demonstration to my supervisors.

## Week 05 — Literature review, C2PA workflows, and PDE presentation

**26 October–1 November 2026**

### Activities completed

- I drafted an initial Literature Review chapter in English, comparing scientific papers, reports, and projects such as Project Origin, C2PA-MCNL, IIRY, C2PA Onchain, and Microsoft's C2PA Extension Validator. I added project–publication links and organised the comparison around identity, issuer authority, and trust.
- I extended the review beyond the six initial documents using the newer collection of papers and projects. I examined work on C2PA–eIDAS integration (Wagenpfeil et al.), issuer accreditation (Frutuoso et al.), long-term signature verification (Hyla and Pejaś), and user trust in provenance-enabled media (Feng et al.), alongside studies of privacy, soft bindings, security, and the Origin Lens verifier. I prepared a focused search specification and distinguished detailed readings, abstract-level reviews, and references requiring further analysis.
- I investigated the proposal to register signatures on a blockchain, using AMP and broker-assisted trust chains as precedents. I compared direct signature registration with anchoring a package of validation evidence, and examined timestamping and evidence renewal. This remained a literature investigation; I did not implement or benchmark these alternatives.
- I revised and improved the dissertation text in Overleaf, including the C2PA background. I added creation, editing, and verification workflows that distinguish users from tools, supported by a sixth figure. I also incorporated examples for JPEG, PNG, MP4, WAV, and MP3 and further explanations of manifest embedding and verification into the shared Overleaf document.
- I changed citations to point directly to sections of the relevant specifications. I also restored local LaTeX compilation and preview after synchronising changes from Overleaf, keeping the local build configuration separate, and corrected bibliography and layout warnings. I checked the resulting PDF.
- I prepared the state-of-the-art presentation for the PDE course, using three slides to introduce the problem, synthesise related papers and projects, and explain how the review informs the proposed work. I adapted the speaking notes to the three-minute limit and used accreditation revocation to illustrate the research questions and planned evaluation.

### Ongoing work and next steps

- I am continuing to analyse relevant papers and projects and improve the dissertation text in Overleaf.
- I will prepare the C2PA demonstration discussed in the meetings, using private keys and test certificates I created to show manifest creation, signing, and verification.
- I will begin turning the state-of-the-art bullet points in Overleaf into coherent prose, describing and comparing the existing work.

## Week 04 — C2PA illustrations and detailed literature analysis

**19–25 October 2026**

### Activities completed

- I prepared and revised original C2PA diagrams in Canva, using the specification's explanatory approach as a reference. I used concrete examples to explain manifests, ingredients, storage, content bindings, and validation.
- I shortened and reorganised the C2PA background chapter and integrated five figures with captions and references. I corrected the ingredient-composition diagram, documented the purpose of each selected figure, and compiled and checked the illustrated chapter.
- I collected the six papers and research reports listed in my initial state-of-the-art material, checked the downloaded PDFs, and indexed their titles and source links.
- I prepared detailed reading notes for all six documents, recording relevant pages, sections, figures, and tables. I compared their approaches, trust assumptions, evaluations, and limitations, and identified implications for the C2PA–EBSI framework, including issuer identity, blockchain evidence, revocation, and long-term verification.

### Ongoing work and next steps

- I will turn the reading notes into a comparative Literature Review chapter, connect repositories to associated publications, and separate technical background from the discussion of existing solutions and research gaps.
- I will refine the questions raised by the review, particularly the role of EBSI accreditation and the evidence needed for later verification. Candidate architectures, experiments, and preservation mechanisms remain proposals to assess.

## Week 03 — C2PA research, dissertation writing, and signing demonstration

**12–18 October 2026**

### Activities completed

- I researched projects, papers, and existing implementations that use C2PA to identify related work and possible reference systems for my dissertation. I surveyed the Content Authenticity tools and SDKs, including `c2pa-rs`, `c2patool`, and the Python and JavaScript libraries, alongside application projects such as Origin Lens, Fraunhofer FAMIUM, and the Qualabs live video toolkit.
- I identified academic work on C2PA video streaming, provenance security, privacy, and the use of watermarks and fingerprints as soft bindings. I organized these materials to compare their scope, available implementations, evaluation methods, and relevance to my proposed C2PA–EBSI framework.
- I added C2PA background material to the shared Overleaf dissertation, covering manifests, claims, assertions, ingredients, storage, content bindings, digital signatures, and validation. I clarified the distinction between content integrity, trust in the signer, and the factual truth of the content.
- I carried out the planned C2PA demonstration with private signing keys and certificates. I created a local test root and my own signing key and certificate, and used the demonstration to explain the signing workflow and the role of trust anchors in verification.
- I investigated PKCS#11 and external signing as possible ways to use protected signing keys in a later prototype. This remained a conceptual investigation; I did not implement a token or HSM integration.

### Ongoing work and next steps

- I will narrow the related-work selection and read the most relevant papers in depth, separating existing C2PA capabilities from the contribution I intend to make through EBSI integration.
- I will refine the C2PA background in Overleaf and connect it to producer identity, issuer trust, and Verifiable Credentials. I have not selected the final integration architecture or governance model.
- I will document the demonstration's detailed validation results and extend the experiments to content alteration, metadata removal, and embedded versus external manifests. The local test certificates do not establish public identity or EBSI integration.

## Week 02 — C2PA experiments and demonstration preparation

**5–11 October 2026**

### Activities completed

- I explored the Rust/Cargo [c2patool project](https://github.com/contentauth/c2patool) and its relationship to the `c2pa-rs` library.
- I read an existing signed JPEG manifest and inspected its author declaration, actions, claim, assertions, hashes, and signing information. I compared it with unsigned JPEGs, which returned `Error: No claim found`.
- I created and embedded a manifest in a copy of an Apollo 17 photograph using an ES256 development key and certificate, then read the output to verify its signature and hashes. I repeated the signing and reading workflow with another JPEG.
- I observed valid signatures and matching assertion and content hashes alongside `signingCredential.untrusted`. I established that cryptographic validity alone does not establish signer trust or prove an author declaration.
- I inspected the generated ingredient and `c2pa.opened` action, which appeared despite an empty custom assertions list. I recorded local processing without establishing the photograph's earlier history. I also observed that missing provenance and skipped revocation checks did not establish earlier provenance or certificate revocation status.
- On 6 October, I prepared commands and explanations for a demonstration intended for the following day, covering manifest reading, unsigned images, signing, and interpretation of verification results.
- I updated my dissertation cover's supervisor information, adjusted the handling of generated and local support files, and documented my LaTeX remote workflow while keeping Overleaf synchronization manual.
- I created the initial weekly progress reports and the separate [PDE repository](https://github.com/joaovarela14/PDE), with its GitHub remote configured.

### Ongoing work and next steps

- I explored sidecars, editing behavior, additional metadata, other media formats, and PKCS#11 conceptually; I have not completed practical tests for them.
- I will test content alteration while retaining a manifest, distinguish hash mismatches from metadata removal, and compare sidecar verification with embedded manifests. I have not yet tested manifest modification or invalid signatures.
- I will investigate signing-certificate trust configuration and how Verifiable Credentials and EBSI could establish trust in producer identity and issuers. I have not selected a final credential schema, integration architecture, or governance model.
- I will continue the literature review and environment request. I have not yet confirmed submission or access to the environment.

## Week 01 — Project preparation and Git integration

**28 September–4 October 2026**

### Activities completed

- I met with Professor Paulo Bartolomeu and Professor André Zúquete to discuss the dissertation, including manifests, internal and external storage, digital signatures, and authenticity metadata. Professor Paulo Bartolomeu created our shared Overleaf project using the University of Aveiro dissertation template.
- I configured my LaTeX repository with separate Overleaf and GitHub remotes and successfully tested synchronization with both using a test change.
- I read introductory material about C2PA and presented my initial understanding of provenance metadata, manifests, and signatures during the meeting.
- I prepared the cloned C2PA command-line tool repository for exploration and began investigating the application form for an EBSI conformance environment.

### Ongoing work and next steps

- I will explore the C2PA CLI, read sample manifests, create a signed output, and prepare a practical demonstration, following my supervisors' recommendation.
- I am investigating the environment application procedure. I will prepare a justification for Professor Paulo Bartolomeu's review before submission; Professor Paulo Bartolomeu may submit the request if university affiliation is required.
- I will review European and international provenance initiatives and investigate producer identity, issuer trust, governance, wallets, and potential EBC/EPC integration before selecting an architecture.
- I am waiting for a related digital wallet dissertation from Professor André Zúquete.

---

I add one entry per week to this file using the [weekly entry template](templates/weekly-template.md), placing the most recent week first, summarizing completed activities, and separating ongoing work from planned tasks.
