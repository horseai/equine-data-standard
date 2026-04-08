# Equine Data Standard

**An open, MIT licensed JSON schema for equine digital identity.**

[![Licence: MIT](https://img.shields.io/badge/Licence-MIT-blue.svg)](LICENSE.txt)
[![Version](https://img.shields.io/badge/Version-1.0-green.svg)](equine-profile-standard/v1.0/schema/equine.profile.standard.v1.0.json)

Published by **Horse AI — TechXZone Pvt Ltd**  
Contact: akanksha@horseai.org

---

## What Is This?

The **Equine Data Standard** is an umbrella repository for open, MIT licensed data standards for equine digital identity and interoperability.

Any developer, platform, breed society, or institution can adopt these standards to ensure horse data is consistent, machine-readable, and portable across systems.

---

## Repository Structure

```
equine-data-standard/
├── README.md
├── LICENSE.txt
│
└── equine-profile-standard/
    ├── README.md
    └── v1.0/
        ├── schema/
        │   └── equine.profile.standard.v1.0.json
        ├── examples/
        │   └── equine.profile.example.v1.0.json
        ├── docs/
        │   ├── equine.profile.data.dictionary.v1.0.md
        │   ├── equine.profile.changelog.v1.0.md
        │   └── equine.profile.implementation.guide.v1.0.md
        └── database/
            ├── mysql/
            │   └── equine_standard_mysql_v1.0.sql
            ├── postgresql/
            │   └── equine_standard_postgresql_v1.0.sql
            ├── sqlite/
            │   └── equine_standard_sqlite_v1.0.sql
            └── mongodb/
                └── equine_standard_mongodb_v1.0.js
```

---

## Standards in This Repository

| Standard | Directory | Version | Status |
|----------|-----------|---------|--------|
| Equine Profile Standard | `equine-profile-standard/` | v1.0 | Published |

---

## Schema Domains

| Domain | Key Fields |
|--------|------------|
| Horse Identity | `horseName`, `dob`, `breed`, `gender`, `color`, `ueln`, `passportNo`, `microchip` |
| Pedigree | `sire`, `dam`, `sireOfSire`, `damOfSire`, `sireOfDam`, `damOfDam`, `description` |
| Owner & Breeder | `ownerName`, `ownerContact`, `stableLocation`, `breederName`, `breederContact` |
| Media | `photos[].url`, `photos[].caption`, `photos[].isPrimary` |
| Meta | `schemaVersion`, `createdAt`, `updatedAt`, `capturedBy`, `sourceApp`, `geo` |
| Consent | `acknowledged`, `acknowledgedAt`, `acknowledgedBy`, `disclaimer`, `ipAddress` |

---

## Quick Start

### Minimum Valid Profile

```json
{
  "horseName": "Desert Storm",
  "dob": "2019-03-15",
  "breed": "Marwari",
  "gender": "stallion",
  "color": "Bay",
  "meta": {
    "schemaVersion": "1.0",
    "createdAt": "2026-04-07T10:30:00Z"
  }
}
```

### Validate with JavaScript

```javascript
import Ajv from "ajv";
import addFormats from "ajv-formats";
import schema from "./equine-profile-standard/v1.0/schema/equine.profile.standard.v1.0.json" assert { type: "json" };

const ajv = new Ajv();
addFormats(ajv);

const validate = ajv.compile(schema);
const valid = validate(horseProfile);

if (!valid) console.log(validate.errors);
```

### Validate with Python

```python
import json
from jsonschema import validate, ValidationError

with open("equine-profile-standard/v1.0/schema/equine.profile.standard.v1.0.json") as f:
    schema = json.load(f)

with open("my-horse-profile.json") as f:
    profile = json.load(f)

try:
    validate(instance=profile, schema=schema)
    print("Valid.")
except ValidationError as e:
    print(f"Error: {e.message}")
```

---

## Documentation

For complete field definitions, validation guidance, and implementation notes see [`equine-profile-standard/v1.0/docs/equine.profile.data.dictionary.v1.0.md`](equine-profile-standard/v1.0/docs/equine.profile.data.dictionary.v1.0.md).

---

## Versioning

This repository follows semantic versioning. The `meta.schemaVersion` field in every profile records which version of the standard it conforms to.

- **v1.x** — backwards-compatible additions
- **v2.0+** — breaking changes

---

## Contributing

Issues and pull requests are welcome. Please open an issue before proposing breaking changes.

---

## Licence

MIT License — Copyright (c) 2026 Horse AI — TechXZone Pvt Ltd

See [LICENSE.txt](LICENSE.txt) for full terms.
