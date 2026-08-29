# Australian Energy Sector Cyber Security Framework in OSCAL Format

## Introduction

The Australian Energy Sector Cyber Security Framework (AESCSF) is the cyber
security maturity and assessment framework for the Australian energy sector —
electricity, gas and liquid fuels — developed by the Australian Energy Market
Operator (AEMO) in partnership with industry, the Australian Cyber Security
Centre (ACSC) and the Cyber and Infrastructure Security Centre (CISC).

The authoritative source for the AESCSF is:

https://aemo.com.au/initiatives/major-programs/cyber-security/aescsf-framework-and-resources

The Open Security Controls Assessment Language (OSCAL) was developed by the
National Institute of Standards and Technology (NIST) to enable automation of
risk management and compliance frameworks based on security controls and
functional requirements, such as SOC 2, FedRAMP, ISO-27001, StateRAMP, CMMC,
HIPAA, and PCI. OSCAL is an open machine-readable information exchange format
that enables tools to interoperate. More info on OSCAL is available at:

https://pages.nist.gov/OSCAL/

AEMO does not publish an OSCAL version of the AESCSF. They publish the
framework documentation as PDF and the criteria as an Excel workbook.

We wrote some scripts which create OSCAL outputs from the AEMO published
AESCSF v2 Core workbook. In this repository we provide:

- AESCSF v2 OSCAL catalog in JSON, XML and YAML
- AESCSF v2 OSCAL profiles for each Maturity Indicator Level, each Security
  Profile, and each SP × MIL intersection
- AESCSF v2 resolved OSCAL profile catalogs for all of the above

While *unofficial*, we have published this openly to support AESCSF-focused
security and compliance engineers and governance, risk and compliance analysts
in using compliance automation tooling.

If you have questions - raise an issue or send us an email.

## About this repository

This repository is a passive publishing destination — no build or sync logic
lives here. The OSCAL artifacts in this repository are produced by the scripts
in the sibling `aescsf-oscal-builder` project and pushed here by that project.
If you are interested in those scripts, please contact the maintainer.

## Contents

_Last updated: 2026-08-29_

Files are named `aescsf-v<version>-<artifact>.<format>` throughout, so multiple
AESCSF revisions can coexist in one repository without collision. All artifacts
target OSCAL 1.2.2.

### Base catalog

The full AESCSF v2 Core as a single OSCAL catalog: 354 controls across 11
domains and 43 objectives, grouped Domain > Objective > Practice.

| Artifact | JSON | XML | YAML |
| --- | --- | --- | --- |
| Base catalog | `aescsf-v2-catalog.json` | `aescsf-v2-catalog.xml` | `aescsf-v2-catalog.yaml` |

Of the 354 controls, 312 are AESCSF Practices and 42 are AESCSF Anti-Patterns.
Anti-Patterns are modelled as controls with `class="anti-pattern"` — AEMO
describes them as "the non-negotiables of cyber", so they are in scope for
assessment rather than commentary. Consumers who want practices only can filter
on the `practice-type` prop.

### Profiles and resolved profile catalogs

For each scope below, an OSCAL profile document (listing the applicable control
IDs) and a resolved profile catalog (the filtered catalog itself, with empty
groups pruned):

| Scope | Controls | Profile | Resolved profile catalog |
| --- | ---: | --- | --- |
| MIL-1 | 62 | `aescsf-v2-mil-1-profile.{json,xml,yaml}` | `aescsf-v2-mil-1-resolved-profile-catalog.{json,xml,yaml}` |
| MIL-2 | 242 | `aescsf-v2-mil-2-profile.{json,xml,yaml}` | `aescsf-v2-mil-2-resolved-profile-catalog.{json,xml,yaml}` |
| MIL-3 | 354 | `aescsf-v2-mil-3-profile.{json,xml,yaml}` | `aescsf-v2-mil-3-resolved-profile-catalog.{json,xml,yaml}` |
| SP-1 | 123 | `aescsf-v2-sp-1-profile.{json,xml,yaml}` | `aescsf-v2-sp-1-resolved-profile-catalog.{json,xml,yaml}` |
| SP-2 | 275 | `aescsf-v2-sp-2-profile.{json,xml,yaml}` | `aescsf-v2-sp-2-resolved-profile-catalog.{json,xml,yaml}` |
| SP-3 | 354 | `aescsf-v2-sp-3-profile.{json,xml,yaml}` | `aescsf-v2-sp-3-resolved-profile-catalog.{json,xml,yaml}` |
| SP-1 at MIL-1 | 62 | `aescsf-v2-sp-1-mil-1-profile.{json,xml,yaml}` | `aescsf-v2-sp-1-mil-1-resolved-profile-catalog.{json,xml,yaml}` |
| SP-1 at MIL-2 | 119 | `aescsf-v2-sp-1-mil-2-profile.{json,xml,yaml}` | `aescsf-v2-sp-1-mil-2-resolved-profile-catalog.{json,xml,yaml}` |
| SP-1 at MIL-3 | 123 | `aescsf-v2-sp-1-mil-3-profile.{json,xml,yaml}` | `aescsf-v2-sp-1-mil-3-resolved-profile-catalog.{json,xml,yaml}` |
| SP-2 at MIL-1 | 62 | `aescsf-v2-sp-2-mil-1-profile.{json,xml,yaml}` | `aescsf-v2-sp-2-mil-1-resolved-profile-catalog.{json,xml,yaml}` |
| SP-2 at MIL-2 | 242 | `aescsf-v2-sp-2-mil-2-profile.{json,xml,yaml}` | `aescsf-v2-sp-2-mil-2-resolved-profile-catalog.{json,xml,yaml}` |
| SP-2 at MIL-3 | 275 | `aescsf-v2-sp-2-mil-3-profile.{json,xml,yaml}` | `aescsf-v2-sp-2-mil-3-resolved-profile-catalog.{json,xml,yaml}` |
| SP-3 at MIL-1 | 62 | `aescsf-v2-sp-3-mil-1-profile.{json,xml,yaml}` | `aescsf-v2-sp-3-mil-1-resolved-profile-catalog.{json,xml,yaml}` |
| SP-3 at MIL-2 | 242 | `aescsf-v2-sp-3-mil-2-profile.{json,xml,yaml}` | `aescsf-v2-sp-3-mil-2-resolved-profile-catalog.{json,xml,yaml}` |
| SP-3 at MIL-3 | 354 | `aescsf-v2-sp-3-mil-3-profile.{json,xml,yaml}` | `aescsf-v2-sp-3-mil-3-resolved-profile-catalog.{json,xml,yaml}` |

The profiles use cumulative semantics on both axes, per AEMO's *AESCSF
Overview*: "All SP-1 & SP-2 Practices and Anti-Patterns must be completed to
achieve Security Profile 2", and "All practices and anti-practices indicated
for an MIL must be present or absent within a domain, to achieve that level."
So an SP-2 profile is the SP-1 plus SP-2 practice set, and MIL-2 is MIL-1 plus
MIL-2. The cumulative SP totals reproduce AEMO's published figures of 123 /
275 / 354 exactly.

The full scope matrix:

|      | MIL-1 | MIL-2 | MIL-3 |  all |
| ---- | ----: | ----: | ----: | ---: |
| SP-1 |    62 |   119 |   123 |  123 |
| SP-2 |    62 |   242 |   275 |  275 |
| SP-3 |    62 |   242 |   354 |  354 |
| all  |    62 |   242 |   354 |  354 |

**Note on redundancy.** The 15 profiles resolve to only **6 distinct control
sets**. Every MIL-1 practice is tagged SP-1, and every MIL-2 practice is tagged
SP-1 or SP-2, so the Security Profile axis does no filtering work at the lower
maturity levels — `aescsf-v2-mil-1-profile` and `aescsf-v2-sp-3-mil-1-profile`
select identical control sets, for instance. This is a property of the AESCSF
data, not of the conversion. All 15 are published because each is addressable
by the name an assessor would use, but deduplicate before indexing them.

### AESCSF-specific vocabulary

Each control carries the following OSCAL `<prop>` elements under the namespace
`https://aemo.com.au/ns/oscal/aescsf` (except `label`, which uses the default
OSCAL namespace):

- `label` — the original AESCSF Practice ID (e.g. `ACCESS-1a`, `ACCESS-AP1`)
- `domain` — the AESCSF domain short code (e.g. `ACCESS`)
- `objective-id` — the AESCSF objective (e.g. `ACCESS-1`)
- `practice-type` — `practice` or `anti-pattern`
- `mil` / `mil-level` — Maturity Indicator Level, as `MIL-2` and as `2`
- `security-profile` / `security-profile-level` — Security Profile, as `SP-2` and as `2`
- `source-row` — the row in the AEMO workbook this control came from
- `ism-security-control` — one prop per referenced ISM control, `class="cross-reference"`
- `essential-eight-strategy` — one prop per referenced Essential Eight strategy
- one prop per international framework mapping (`nist-sp-800-53-r5`,
  `iso-iec-27001-2013`, `nist-csf-v1-1`, `cis-csc-v-7-1`, `cobit-5`,
  `isa-62443-2-1-2009`, `isa-62443-3-3-2013`), each `class="cross-reference"`

The numeric `*-level` props exist so tooling can filter with an integer
comparison rather than parsing `"MIL-2"`.

Consumers that don't recognise the AESCSF namespace can safely ignore these
props.

### Cross-framework references

References are parsed into structured OSCAL rather than carried as prose. The
catalog's back-matter holds 196 distinct ISM security controls (with revision,
update date, applicability and Essential Eight maturity mapping retained as
props, and the full ISM control text as the resource description), 8 Essential
Eight strategies, and 7 international frameworks. Controls point at them with
`rel="reference"` links.

This makes crosswalks queryable. For example, every AESCSF practice citing
ISM-0430:

```bash
jq -r '.catalog.groups[].groups[].controls[]
       | select(.props[]? | select(.name=="ism-security-control" and .value=="ISM-0430"))
       | .props[] | select(.name=="label") | .value' \
   aescsf-v2-catalog.json
```

## Validation

Unlike many hand-rolled OSCAL conversions, these artifacts are validated before
publication. Every file here has been checked against:

- the NIST OSCAL 1.2.2 **JSON Schema** (catalog and profile)
- the NIST OSCAL 1.2.2 **XSD**
- YAML/JSON structural equality
- XML/JSON control-set equality
- resolved-catalog versus profile-selection equality
- control-by-control fidelity back to the AEMO source workbook

Current status at last publish: 31 JSON and 31 XML documents valid, 354/354
controls verified against the source, 0 failures.

That said, validate independently before feeding these into tooling that will
reject invalid input silently — `oscal-cli`, `compliance-trestle`, or NIST's
online OSCAL validator are all reasonable second opinions.

## Known caveats

- **ACCESS domain title.** AEMO's *AESCSF Overview* Table 4 prints the ACCESS
  domain as "Identify and access management". That is a typo for "Identity".
  The catalog uses the corrected "Identity and Access Management" as the group
  title and retains AEMO's wording on a `source-title` prop.
- **Framework versions are as-published**: CIS CSC 7.1, COBIT 5, ISO/IEC
  27001:2013, NIST CSF 1.1, NIST SP 800-53 R5. The ISO/IEC 27001:2022 and NIST
  CSF 2.0 remappings are not present in the AEMO source and have not been
  inferred.
- **Resolved catalogs are produced natively**, not by an OSCAL profile
  resolver. The profiles use only `import` + `include-controls` with `as-is`
  merging and no `modify`, and each resolved catalog is asserted equal to its
  profile's selection. If you need canonical resolution, run the profiles
  through `oscal-cli`.

## Copyright

The Australian Energy Sector Cyber Security Framework (AESCSF) is published by
the Australian Energy Market Operator (AEMO). Framework content is copyright
AEMO and its licensing terms govern any redistribution of these derivative
artifacts.

The OSCAL derivative artifacts in this repository are created by independent
security and compliance engineer Baden Hughes. They are a mechanical
transformation of the AEMO published workbook and add no framework content.

This is an **unofficial** conversion. It is not endorsed by, affiliated with,
or supported by AEMO.
