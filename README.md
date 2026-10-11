# Master's Dissertation Progress

**Title:** Verifiable Content Authenticity and Anti-Deepfake Provenance on the European Blockchain Services Infrastructure

**Institution:** University of Aveiro, Department of Electronics, Telecommunications and Informatics (DETI)  
**Student:** João Varela  
**Supervisor:** Paulo Jorge de Campos Bartolomeu  
**Co-supervisor:** André Ventura da Cruz Marnôto Zúquete

**Keywords:** Blockchain, EBSI, C2PA, Content Authenticity, Verifiable Credentials, Deepfake, eIDAS 2.0.

## Problem and objective

Generative AI makes realistic synthetic and manipulated digital content increasingly easy to produce, raising concerns about authenticity and trust. C2PA records content provenance and modification history through cryptographically signed manifests, but does not by itself establish whether a signer is trustworthy. EBSI provides infrastructure for verifiable credentials, trusted issuers, identity registries, and revocation mechanisms.

My objective is to design and prototype a framework integrating C2PA content credentials with EBSI to establish a verifiable chain of trust for digital content.

I plan to:

- I will study C2PA, EBSI, Verifiable Credentials, and eIDAS 2.0.
- I will review related research and European and international initiatives.
- I will define credential schemas for content provenance.
- I will investigate issuer identity, trust registries, governance, and revocation.
- I will develop tools for creating and verifying content credentials.
- I will explore integration with digital identity wallets.
- I will evaluate the solution using authentic, AI-generated, and AI-edited media.

## Current progress

- I met with my supervisors and began studying C2PA and digital provenance. Paulo created our shared Overleaf project using the University of Aveiro template.
- I connected my LaTeX repository to Overleaf and GitHub and successfully tested synchronization with both remotes.
- I explored the C2PA CLI, read existing manifests, and created and verified signed JPEGs. I observed valid signatures and matching hashes, alongside an untrusted test signing certificate.
- I prepared a practical demonstration of manifest reading, creation, and verification.
- I am investigating the compliance-environment application process. I have not yet confirmed submission or access.
- I still need to develop the literature review, credential schemas, and integration architecture.
- I created this progress repository on GitHub and configured its `origin` remote.

## Weekly reports

- [Week 01 — project preparation and Git integration](weeks/week-01.md): 28 September–4 October 2026.
- [Week 02 — C2PA experiments and demonstration preparation](weeks/week-02.md): 5–11 October 2026.
- [Reusable weekly template](templates/weekly-template.md).

## Research topics

I am investigating C2PA manifests, digital signatures, file modification, EBSI compliance environments, Verifiable Credentials, issuer identity, trust registries, governance, and revocation. I also plan to study digital identity wallets, eIDAS 2.0, European and international provenance initiatives, and media evaluation. I still need to clarify the role of potential EBC/EPC integration.

## Weekly maintenance

1. I copy [the weekly template](templates/weekly-template.md) to a new report in `weeks/`.
2. I enter the reporting dates and describe my completed work, ongoing investigation, and next steps separately.
3. I add the report to the index and update my current progress.

I keep these reports concise, factual, and in English. I use Overleaf for dissertation writing.

## Repositories and remotes

| Repository | Purpose | Remotes |
| --- | --- | --- |
| [PDE](https://github.com/joaovarela14/PDE) | English Markdown progress reports | `origin`: `https://github.com/joaovarela14/PDE.git` |
| [Thesis_Latex](https://github.com/joaovarela14/Thesis_Latex) | Dissertation sources, separate from this repository | `github`: GitHub thesis repository; `overleaf`: shared Overleaf project |

I tested synchronization of my LaTeX repository with both remotes during Week 01. I synchronize with Overleaf manually and keep my dissertation sources separate from these progress reports.
