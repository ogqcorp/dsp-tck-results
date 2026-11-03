# Configuration used for the DSP TCK runs (2026-11-03)

**Catalog and metadata.** The TCK ran as consumer against the hosted staging provider
`https://stg.nova.ogq.me/api/dsp/2025-1/tenants/ops-demo-stg` (DSP base URL is per organisation, path-based).
The test organisation's catalog was set to public only for the duration of the run.

**Negotiation and transfer.** The TCK ran against a local test harness that wraps our production
contract-negotiation and transfer-process service functions with an in-memory database. This is needed because
the TCK callback address is not reachable from our hosted environment. State machines and callbacks are the production code.

**Offer shim (`DSP_TCK_OFFER_SHIM=1`).** When the `@id` of the offer sent by the TCK equals our catalog offer,
the TCK's fixed one-rule policy is replaced by our catalog offer terms before validation. Nothing else is changed.
With the shim off, 61/65 pass (see README).

**Transfer start.** Provider auto-starts the transfer after acknowledging REQUESTED.

**Runtime.** Docker images `eclipsedataspacetck/dsp-tck-runtime:1.0.2` and `dcp-tck-runtime:1.2.1`, run 2026-11-03.

Contact: I.T.SHIN, netclaus@ogqcorp.com
