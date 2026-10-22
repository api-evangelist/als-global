---
generated: '2026-10-21'
method: generated
name: export-sample-results
description: Incrementally export ALS Tribology oil-analysis sample results from Webtrieve using the sync time and criteria filters.
api: openapi/als-global-webtrieve-export-openapi.yml
operations: [Preference_Version, Search_GetSampleSyncTime, Search_GetSampleExportResultsExposed]
source: Grounded in openapi/als-global-webtrieve-export-openapi.yml (Swagger 2.0, Webtrieve.ExportApi v1); all operationIds verified verbatim.
---

# Export sample results

## Auth
HTTP Basic (`securityDefinitions.basic`) against `https://api.alstribology.com`.

## Steps
1. `Preference_Version` — GET /Preference/Version to confirm the API is reachable and which version answers.
2. `Search_GetSampleSyncTime` — GET /SampleResultsExport/GetSyncTime to read the sync time.
3. `Search_GetSampleExportResultsExposed` — POST /SampleResultsExport/SampleResults with `criteria.*` query parameters (each filter takes `value`, `valueCollection` and `operator`): e.g. `criteria.lastUpdateDate.*` for changes since your last pull, or `criteria.dateSampled`, `criteria.sIFNo`, `criteria.uIN`, `criteria.severityId`, `criteria.brand`, `criteria.trackingNumber`; `criteria.columnsRequired` limits returned columns. Read-only despite the POST verb.

## Errors
The spec declares 400 and 500 responses only. No pagination or rate limits are documented.
