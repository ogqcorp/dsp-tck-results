# OGQ Market Data Space Connector — Eclipse DSP / DCP TCK results

Published by OGQ Corporation (Seoul, Republic of Korea) for the IDSA Data Space Connector Report review.
Contact: I.T.SHIN, netclaus@ogqcorp.com · Website: https://ogq.market · Data space: https://nova.ogq.me

The connector is proprietary software operated as a service by OGQ Corporation. This repository contains only test output and the test configuration description; it contains no connector source code.

## Results (run 2026-11-03)

| Test kit | Target | Result | Log |
|---|---|---|---|
| Eclipse DSP TCK 1.0.2 (`eclipsedataspacetck/dsp-tck-runtime:1.0.2`), all 65 tests, **offer shim on** | Local test harness (production negotiation/transfer functions, in-memory DB) | **65/65 passed** (MET 1, CAT 3, CN 15, CN_C 16, TP 15, TP_C 15) | [logs/ogq_dsp-tck-1.0.2_local_offer-shim_65of65.txt](logs/ogq_dsp-tck-1.0.2_local_offer-shim_65of65.txt) |
| Eclipse DSP TCK 1.0.2, all 65 tests, **offer shim off** | Same harness | **61/65 passed** — CN:01-04, CN:02-03, CN:02-07, CN:03-01 fail (see below) | [logs/ogq_dsp-tck-1.0.2_local_no-shim_61of65.txt](logs/ogq_dsp-tck-1.0.2_local_no-shim_61of65.txt) |
| Eclipse DSP TCK 1.0.2, metadata + catalog | Hosted staging provider | MET 1/1, CAT 3/3 (negotiation/transfer modules not run against staging, see configuration) | [logs/ogq_dsp-tck-1.0.2_stg_MET-CAT.txt](logs/ogq_dsp-tck-1.0.2_stg_MET-CAT.txt) |
| Eclipse DCP TCK 1.2.1, Credential Service | Local | 53/54 (holderPid design difference) | [logs/ogq_dcp-tck-1.2.1_credential-service.txt](logs/ogq_dcp-tck-1.2.1_credential-service.txt) |
| Eclipse DCP TCK 1.2.1, Issuer | Local | 40/41 (TCK assumes two credentials) | [logs/ogq_dcp-tck-1.2.1_issuer.txt](logs/ogq_dcp-tck-1.2.1_issuer.txt) |
| Eclipse DCP TCK 1.2.1, Verifier | Local | 22/22 | [logs/ogq_dcp-tck-1.2.1_verifier.txt](logs/ogq_dcp-tck-1.2.1_verifier.txt) |

Why 4 tests fail without the shim: those tests send a fixed one-rule offer policy and expect the provider to agree to it. Our provider, by design, rejects agreements whose policy is broader than the catalog offer. The shim (below) is the only deviation; we report both numbers.

## Configuration

See [CONFIGURATION.md](CONFIGURATION.md).

- Dataspace Protocol: 2025-1 (the version endpoint also answers 2024/1)
- TCK: `eclipsedataspacetck/dsp-tck-runtime:1.0.2`, `dcp-tck-runtime:1.2.1`

The test-kit property file is not published because it contains test signing keys.

## Notice

Published for IDSA certification and connector report review. Log files are unmodified TCK output (file names changed to `.txt` for upload).

— I.T.SHIN, OGQ Corporation
