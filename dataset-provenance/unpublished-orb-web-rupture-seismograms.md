# Unpublished Orb-Web Rupture Seismograms

This page is the canonical public provenance and build record for the Project Eris dataset **Unpublished Orb-Web Rupture Seismograms**.

## Origin and ownership

This is a creator-owned, previously unpublished simulation corpus. It contains no downloaded images, recordings, specimens, annotations, numerical rows, or code from third-party datasets. Every feature and target was generated locally by the retained deterministic simulator for this release.

The scientific papers listed below motivated the physical theme only. They supplied no source objects, parameters, rows, labels, or code:

- Mortimer et al., *Decoding the locational information in the orb web vibrations*: https://doi.org/10.5061/dryad.7rm572m
- Masmeijer et al., *Spiders' gyroscopic motion via web mechanical intelligence facilitates prey sensing*: https://doi.org/10.5061/dryad.pc866t255
- Zhang et al., *Baseline-Free Damage Localization in Periodic Cable-Net Structures*: https://doi.org/10.32604/sdhm.2026.082602

## Licence and attribution

The dataset is licensed under the [Creative Commons Attribution 4.0 International licence](https://creativecommons.org/licenses/by/4.0/legalcode).

Required attribution: **Unpublished Orb-Web Rupture Seismograms, generated for Orb-Web Rupture Autopsy.**

## Independent samples and splits

The true independent unit is one independently parameterized 72-node, 136-edge radial network and its ordered three-event rupture history. One realization contributes exactly one row. No frame, crop, patch, repeated measurement, or augmentation is treated as an independent row.

- Training: 1,600 independent realizations
- Public evaluation: 350 independent realizations
- Private evaluation: 350 independent realizations
- Total: 2,300 unique physical groups and feature rows
- Regimes: clear, echoing, damped, and noisy; training has 400 rows per regime and each evaluation shard has 87 or 88 rows per regime

Node labels and edge ordering are independently permuted for every row. Public IDs are HMAC-derived opaque identifiers and encode no split, group, regime, geometry, seed, or target.

## Source-to-final build pipeline

1. Retain a private organizer master secret outside all distributed files.
2. Derive independent deterministic pseudorandom streams for each partition/index pair using HMAC-SHA256 domain separation.
3. For each row, generate a new irregular radial network; sample independent geometry, mass, stiffness, damping, noise, and rupture history; independently permute node and edge labels; place twelve sensors; and simulate 384-sample vibration traces.
4. Record the ordered three-event edge/time target and compute per-row feature and target hashes.
5. Validate exact row counts, finite arrays, unique IDs, unique physical groups, regime balance, target syntax, exact duplicates, near duplicates, public/private boundaries, and the package-size limit.
6. Prepare train inputs and labels, target-free test inputs, a valid nonconstant sample submission, private answers, split manifests, and audit receipts transactionally through staging and rollback.
7. Run public- and private-shard baseline/stability audits with 2,000 independent-row bootstrap replicates per shard.
8. Package the five raw contract files deterministically and run the unit, integration, grader-contract, leakage, and release-verification suites.

The retained build entry point is:

`python -m organizer.build_dataset --key-file organizer/master_secret.hex --output raw --train 1600 --public 350 --private 350`

The source-to-final process is byte-reproducible by the organizer from the retained versioned code and secret. The secret is deliberately excluded because publishing it before challenge retirement would disclose hidden evaluation histories.

## Release identity

- Project Eris dataset ID: `jd70pgxzp0aeg9ab8vc9kg87cn8ej9y7`
- Dataset ZIP size: 48,128,709 bytes (about 45.9 MiB)
- Dataset ZIP SHA-256: `a40951b65f7bdd4b8b908e5c054b3438cd670d180133cc5ccf2efb0a82a5ac8d`
- ZIP members: `build_metadata.json`, `features.npz`, `private_manifest.jsonl`, `records.csv`, and `targets.csv`

## Leakage and public-archive boundary

No evaluation realization has appeared in a public archive, website, DOI supplement, or source collection. There is therefore no external corpus containing the evaluation objects for perceptual, geometric, embedding, filename, OCR, EXIF, or metadata retrieval. Public artifacts contain no targets, target-derived statistics, private group identifiers, generation indices, seeds, source keys, or hidden event scripts.
