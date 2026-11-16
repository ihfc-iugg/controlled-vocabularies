# Changelog

All notable changes to the vocabularies are recorded here. Versions are calendar versions,
`<year>.<release>`.

## [Unreleased]

### Changed

- Addresses start with `https://w3id.org/ihfc-iugg/vocabularies/`, a permanent address
  that does not depend on where the vocabularies are hosted
  (`https://w3id.org/ihfc-iugg/vocabularies/heat-flow-method/bullard`).
- Each vocabulary's `rdfs:seeAlso` points at the repository's new address,
  `https://github.com/ihfc-iugg/controlled-vocabularies`.
- Identifiers are written one way in every vocabulary: lowercase words joined by hyphens,
  acronyms in capitals and the symbols `p` for pressure and `T` for temperature in their
  usual case. `well_log` is now `well-log`, `hornerPlot` is `horner-plot`, `HT_FTpert` is
  `HT-FT-perturbed`, `consideredPT` is `considered-pT` and `BirchClark1940` is
  `T-birch-clark-1940`. The codes in `skos:notation` are unchanged. Each identifier the 2026.03
  submission template needs is listed beside the template's term for it in
  https://github.com/ihfc-iugg/controlled-vocabularies/issues/38.
- Some identifiers now say what the concept is:
  - `onshore-marine` is `onshore-lake-river`, for lakes and rivers on land.
  - `outrigger-ewing` is `outrigger-ewing-corer` and `outrigger-lister` is
    `outrigger-lister-corer`, the probes used with a corer. A plain name is a probe used
    without one, so `outrigger-autonomous-no-corer` is `outrigger-autonomous` and
    `outrigger-autonomous-with-corer` is `outrigger-autonomous-corer`.
  - The temperature methods spell out their states: `LOGeq` is `log-equilibrium`, `DTSpert`
    is `DTS-perturbed` and `cBHT` is `BHT-corrected`. Shortened words become words: `XEN`
    is `xenolith`, `BLK` is `thermal-blanket` and `SUR` is `surface`.
  - `not-corrected` and `notCorrected` are `uncorrected`, `not-recognized` is
    `unrecognized` and `present-not-significant` is `present-insignificant`.
  - The pressure and temperature functions start with `T`, `p` or `pT`, so one author's
    functions for each are told apart, and `ZothHaenal1988` and `Radcliff1960` are spelt as
    the authors' names are (`T-zoth-haenel-1988`, `pT-ratcliffe-1960`).
- Collections that held one concept, or that grouped concepts only the way the quality
  scoring does, are gone. In the conductivity conditions `ambient` and `in-situ` replace
  `actual`, `recorded`, `replicated` and `corrected`. In the conductivity sources `measured`
  and `estimated` replace `computation` and `in-situ`, and `well-log` is estimated, because
  the conductivity is derived from the logs rather than measured. The conductivity methods
  lose `other`, which held only `unspecified`. The correction flags' `generic`, `insitu`
  and `temperature` give way to one collection per flag column.

### Added

- `outrigger-ewing` in the heat-flow probes: the Ewing outrigger probe used without a corer,
  which the 2026.03 submission template lists.
- Two collections in the exploration methods: `excavation` (drilling, drilling and
  clustering, mining and tunnelling) and `probe-sensing` (onshore, offshore and clustered
  probing).
- A collection for each column of the submission template that shares a vocabulary with
  other columns, so each column's accepted values can change on their own:
  - in the correction flags, one for each of the nine flag columns, from `in-situ`
    (`corr_IS_flag`) and `instrumental` (`corr_T_flag`) to `heat-refraction` (`corr_HR_flag`)
  - in the temperature methods, `top` and `bottom`. The bottom of the interval does not
    accept `surface`, and neither accepts `DST` or `DST-corrected`.
- Collections that group concepts by what they are:
  - temperature methods: `continuous-log`, `point-measurement` and `estimated` for the kind
    of measurement, and `equilibrium`, `perturbed` and `corrected` for the thermal state of
    the borehole
  - conductivity sources: `measured` and `estimated`
  - conductivity conditions: `ambient` and `in-situ`
  - conductivity saturation: `saturated`
- A documentation site, with a page for every vocabulary, concept and collection, and its
  RDF in every format beside it.
- `CONTRIBUTORS.md`, listing everyone who has contributed to the vocabularies with their
  affiliation and ORCID iD.
- A release archive, `vocabularies-full.zip`, with every vocabulary in every format,
  the README, contributors, changelog and licence.

## [2026.1] - 2026-10-27

### Changed

- The vocabularies now match the ones the Global Heat Flow Database portal uses, and the files
  in `vocabularies/` are edited directly. The Python code that generated them is gone.
- Addresses start with `https://portal.heatflow.world/vocabularies/`, where the portal serves
  the vocabularies, and use a slash before the identifier
  (`https://portal.heatflow.world/vocabularies/heat-flow-method/bullard`). Several vocabularies take
  the names the portal uses (`heat-flow-probes`, `geographic-environments`,
  `conductivity-sources`, `conductivity-methods`, `conductivity-conditions`,
  `heat-flow-corrections`, `exploration-methods`, `temperature-corrections`).
- Every vocabulary has an English label and a `dcterms:description`. The descriptions taken
  from the portal were corrected for grammar and checked against the concepts they cover.
- Every vocabulary names its creator (the International Heat Flow Commission), its publisher
  (GFZ Helmholtz Centre for Geosciences), its licence, its language, the publications its values
  come from, the data publication it belongs to
  (https://doi.org/10.5880/fidgeo.2026.065), and the Global Heat Flow Database fields that use it.
- Every concept now names its vocabulary (`skos:inScheme`), and every vocabulary lists its top
  concepts.
- The onshore geographic environments and the correction flags each named a concept that
  does not exist. They now name `onshore_marine` and `not_recognized`.

### Added

- Definitions for every concept in the thermal conductivity vocabularies, citations and DOIs for the published pressure and temperature corrections, and the missing members of their collections.
- Definitions, codes, readable labels and links between corrected and uncorrected measurements for every concept in the temperature method and temperature correction vocabularies, and the drill stem test values the 2023 structure lists.
- Definitions, alternative labels and corrected labels for every concept in the heat-flow method, probe type, geographic environment, exploration method, exploration purpose and correction flag vocabularies.
- Each release carries every vocabulary in Turtle, RDF/XML, JSON-LD and N-Triples, each as its
  own file with its own download link.
- Checks that run on every pull request.

### Removed

- The transfer mechanism vocabulary, which the portal no longer uses.
- Empty definitions. 149 concepts have no definition yet.
