---
generated: '2026-10-21'
method: generated
name: submit-oil-samples
description: Submit oil-analysis samples to ALS Tribology through Webtrieve, confirm the submission details and fetch the print labels.
api: openapi/als-global-webtrieve-export-openapi.yml
operations: [Sample_SampleSubmissionImport, Sample_SampleSubmissionGetDetails, Sample_SampleSubmissionGetPrintLabels]
source: Grounded in openapi/als-global-webtrieve-export-openapi.yml (Swagger 2.0, Webtrieve.ExportApi v1); all operationIds verified verbatim.
---

# Submit oil samples

## Auth
HTTP Basic (`securityDefinitions.basic`) against `https://api.alstribology.com`, using Webtrieve credentials issued by ALS.

## Steps
1. `Sample_SampleSubmissionImport` — POST /SampleSubmission/SampleSubmission with a `SampleSubmissionWebAPI` body (`sampleSubmissionData`). This writes data at ALS: confirm with a human first. The spec documents no idempotency key, so do not blindly retry on timeout — check step 2 before resubmitting.
2. `Sample_SampleSubmissionGetDetails` — POST /SampleSubmission/GetSubmissionsDetails with `SampleSubmissionGetDetailsCriteria` to confirm what was registered.
3. `Sample_SampleSubmissionGetPrintLabels` — POST /SampleSubmission/GetPrintLabels with `SampleSubmissionPrintLabelsCriteria` to retrieve labels for the sample bottles.

## Errors
The spec declares 400 and 500 responses only; no error body format is documented.
