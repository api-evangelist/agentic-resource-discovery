# Agentic Resource Discovery (ARD)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

An [API Evangelist](https://apievangelist.com) profile of the **Agentic Resource Discovery**
specification — the third class of repo in this network, alongside API-producing companies and
investors. A standard is not a product; it is **a coalition with artifacts**, so it gets profiled
that way: the specifications, the governance, the maturity ladder, and above all the people and
companies in the room.

- **Site** — https://agenticresourcediscovery.org
- **Specification** — https://agenticresourcediscovery.org/spec/ (v0.9 Draft, Proposal, 28 May 2026)
- **Source** — https://github.com/ards-project
- **Licence** — Apache-2.0
- **Catalog entry** — https://standards.apievangelist.com/store/agentic-resource-discovery/
- **The measured population** — https://apis.io/ard/

## What ARD is

ARD specifies the discovery layer that sits **in front of** every agentic protocol: the step before
invocation, where a client asks *"what is available for this task?"* and gets back a ranked set of
MCP servers, agent cards, skills, workflows and APIs. Publishers describe their resources once in an
**AI Catalog** manifest at `/.well-known/ai-catalog.json` on their own domain, anchored by a
`urn:air:` URN derived from that domain. Independent discovery services crawl those manifests and
answer questions over them through a small REST interface whose only mandatory endpoint is
`POST /search`.

It does not execute anything — MCP, A2A and OpenAPI keep that job. It does not try to be the one
registry: it inverts submit-to-a-registry into publish-to-your-own-domain, and expects many
competing indexes to federate.

## What is in here

| Path | What it holds |
|---|---|
| `apis.yml` | Identity — `x-type: standards-body`, the two contracts the standard publishes, the full property set |
| `specification/` | The verbatim specification, the URN naming guide, the AI Catalog spec, and every docs page |
| `openapi/_original/` | The ARD Registry API as the standard publishes it — analyse from here, never from a refined copy |
| `json-schema/` | The authoritative CDDL grammar and the `ai-catalog.json` JSON Schema |
| `governance/` | The governance read, the ADR ledger, CODEOWNERS, and the observed internal inconsistencies |
| `conformance/` | The project's own conformance CLI, its examples, and what it does and does not test |
| `taxonomy/` | The standard's own classification — media types, endpoints, discovery mechanisms, federation modes |
| `people/` | 44 named humans: three authors, three code owners, forty-one acknowledged contributors |
| `companies/` | The coalition graph — eleven logo-wall organizations, matched against the network |
| `leads/` | Coalition members not yet in the network. There are none, and that is the finding |
| `adoption/` | Who publishes a manifest, who merely claims the standard, and what the four registries return |
| `repositories/`, `releases/`, `contributors/`, `working-groups/` | The GitHub working surface, and the absences |

## What the profile found

Read `adoption/` and `governance/` for the evidence. In short:

- **Nine publishers.** Probing `/.well-known/ai-catalog.json` across 43,834 domains — every absolute
  host in the network plus each host's derived apex, 37,751 of them reachable — found nine
  publishers. **None is fully conformant.** Four pass the project's own conformance tool.
- **The authors are behind the adopters.** Across 127 domains belonging to the eleven organizations
  on ARD's contributors wall, **two** serve a manifest: Hugging Face, and Cisco — whose reference
  implementation fails the project's own conformance test. Google, Microsoft, GitHub, Databricks,
  Salesforce, Snowflake, Nvidia, GoDaddy, ServiceNow and AWS publish nothing on their own domains.
- **Publishing a manifest does not correlate with being a better API provider.** The nine publishers
  average a 57.5 Kin Score and 44.0 Agent Readiness; the eleven coalition companies average 57.0 and
  45.1. Statistically the same population.
- **The `urn:ai:` publishers are stale, not sloppy.** ADR-0009 moved the URN namespace identifier
  from `ai` to `air` for validity. Two publishers and one reference registry still emit `urn:ai:` —
  they implemented against the earlier draft, and nothing in the ecosystem told them.
- **Federation is specified, implemented and empty.** The only referral any of the four registries
  returns points at a second index run by the same operator.
- **The documentation contradicts the tooling in three places** — including the copy-pasteable
  template in the publishing guide, which warns under the project's own conformance CLI. All three
  are listed in `governance/`, with what each one costs.
- **There is no release train.** Zero tags, zero releases; the version lives in a line of markdown,
  and three artifacts disagree about what it is.

## The scoring caveat

Nothing here scores ARD with the provider [Kin Score](https://apievangelist.com/kin-score/)
composite. That rubric measures **services**; a standards body publishes **specifications**. Where a
score appears in this repo it belongs to a company in the coalition, never to the standard.

## Rules this profile follows

No fabrication — never an invented participant, seat, or adoption claim; a miss is recorded as a
miss. Provenance on every person, because a name on a title page and a name in an acknowledgements
list are different strengths of evidence. Absences are recorded rather than omitted: "defined but
empty" and "never defined" are different findings. And the standard's own words are reproduced, not
paraphrased — its taxonomy is a primary source about its own intent.

## Corrections

Everything here is read from a public artifact, and every claim carries the URL it came from.
Pointing at an artifact is the fastest way to change it — open an issue, or mail
[info@apievangelist.com](mailto:info@apievangelist.com).
