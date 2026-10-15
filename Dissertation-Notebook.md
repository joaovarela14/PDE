# Dissertation Notebook

**Title:** Verifiable Content Authenticity and Anti-Deepfake Provenance on the European Blockchain Services Infrastructure

**Institution:** University of Aveiro, Department of Electronics, Telecommunications and Informatics (DETI)  
**Student:** João Varela  
**Supervisor:** Paulo Jorge de Campos Bartolomeu  
**Co-supervisor:** André Ventura da Cruz Marnôto Zúquete

I record my weekly activities in this notebook. My dissertation objective is to design and prototype a framework integrating C2PA content credentials with EBSI to establish a verifiable chain of trust for digital content. I maintain my [dissertation sources](https://github.com/joaovarela14/Thesis_Latex) separately and use Overleaf for shared writing.

## Week 01 — Project preparation and Git integration

**28 September–4 October 2026**

### Activities completed

- I met with Paulo Bartolomeu and André Zúquete to discuss the dissertation, including manifests, internal and external storage, digital signatures, and authenticity metadata. Paulo created our shared Overleaf project using the University of Aveiro dissertation template.
- I configured my LaTeX repository with separate Overleaf and GitHub remotes and successfully tested synchronization with both using a test change.
- I read introductory material about C2PA and presented my initial understanding of provenance metadata, manifests, and signatures during the meeting.
- I prepared the cloned C2PA command-line tool repository for exploration and began investigating the application form for an EBSI conformance environment.

### Ongoing work and next steps

- I will explore the C2PA CLI, read sample manifests, create a signed output, and prepare a practical demonstration, following my supervisors' recommendation.
- I am investigating the environment application procedure. I will prepare a justification for Paulo's review before submission; Paulo may submit the request if university affiliation is required.
- I will review European and international provenance initiatives and investigate producer identity, issuer trust, governance, wallets, and potential EBC/EPC integration before selecting an architecture.
- I am waiting for a related digital wallet dissertation from André.

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

---

I append one entry per week to this file using the [weekly entry template](templates/weekly-template.md), summarizing completed activities and separating ongoing work from planned tasks.
