# Week 02 — C2PA Experiments and Demonstration Preparation

## 1. Week and date range

**Week:** 02  
**Date range:** 5–11 October 2026.

## 2. Objectives

- I aimed to explore the C2PA CLI through controlled experiments.
- I wanted to read, create, embed, and verify manifests, distinguishing integrity from signer trust.
- I planned to prepare a concise demonstration for my supervisors.
- I aimed to improve my LaTeX workflow and organize my weekly progress reports.

## 3. Work completed

### C2PA investigation and tests

- I explored the Rust/Cargo CLI project and its relationship to the `c2pa-rs` library.
- I read an existing JPEG manifest and inspected its author declaration, actions, claim, assertions, hashes, and signing information.
- I compared signed samples with unsigned JPEGs, which returned `Error: No claim found`.
- I created and embedded a manifest in a new copy of an Apollo 17 photograph using an ES256 development key and certificate, then read and inspected the result.
- I repeated the creation and reading workflow with another sample JPEG.
- I prepared concise demonstration commands and explanations.

### Dissertation writing and Git

- I updated my dissertation cover's supervisor information and the handling of generated and local support files.
- I documented my LaTeX remote workflow and kept Overleaf synchronization under my manual control.
- I created my initial Markdown progress reports and the separate [PDE GitHub repository](https://github.com/joaovarela14/PDE), with `origin` pointing to it.

## 4. Meetings and important decisions

- On 6 October, I prepared a demonstration intended for the following day.
- I focused it on reading an existing manifest, showing an unsigned image, creating a signed image, and interpreting verification results.
- I kept my dissertation sources and weekly progress reports in separate repositories, each with its own remotes.

## 5. Research and technical findings

### Test results

| Test I performed | Result I observed |
| --- | --- |
| Read an existing signed JPEG | I found a manifest with author and action declarations; the signature and data hashes verified, but the test certificate was untrusted |
| Inspect the detailed manifest | I examined claim references, assertion hashes, and the content hash assertion |
| Read unsigned JPEGs | I received `Error: No claim found` |
| Create and read a signed Apollo 17 JPEG | I found the embedded manifest and verified its ES256 signature and hashes; the test certificate remained untrusted |
| Inspect the generated manifest in detail | I examined its claim, assertions, ingredient, and hash information |
| Repeat signing with another JPEG | I read the new manifest successfully and observed the same distinction between signature validity and certificate trust |

### What I learned

- I obtained validation results while reading manifests; I did not use a separate validation subcommand.
- I observed `claimSignature.validated`, `assertion.hashedURI.match`, and `assertion.dataHash.match` alongside `signingCredential.untrusted` and the overall state `Valid`. I learned that cryptographic validity does not establish signer trust.
- I found that the generated manifest included the input as an ingredient and a `c2pa.opened` action, despite my empty custom assertions list. I recorded local processing without establishing the photograph's earlier history.
- I observed `ingredient.unknownProvenance` for missing earlier provenance. I also learned that `signingCredential.ocsp.skipped` does not confirm that a certificate is unrevoked.
- I learned that signing an author declaration does not independently prove authorship or truth. I still need to investigate how Verifiable Credentials and EBSI could establish trust in producer identity and issuers.
- I explored sidecars, editing behavior, additional metadata, other media formats, and PKCS#11 conceptually, but I have not yet completed practical tests for them.

## 6. Challenges and open questions

- I still need an appropriate trust configuration for signing certificates.
- I have not yet tested content tampering, manifest modification, invalid signatures, or sidecar verification.
- I still need to confirm submission of the environment request and access to the environment.
- I have not selected a final credential schema, EBSI integration, or trust governance model.

## 7. Next steps

- I will keep my demonstration assets organized for reuse.
- I will test content alteration while retaining the manifest and distinguish a hash mismatch from metadata removal.
- I will test a sidecar and compare it with an embedded manifest.
- I will investigate certificate trust configuration and identity and issuer verification.
- I will continue the environment request, literature review, and coordination with my supervisors.

## 8. References and resources

- I use the [c2patool repository](https://github.com/contentauth/c2patool) for my tool investigation.
- I maintain my [dissertation sources](https://github.com/joaovarela14/Thesis_Latex) separately from my [weekly progress reports](https://github.com/joaovarela14/PDE).
