# OpenLIFU Sample Database

Example database for the [OpenLIFU](https://github.com/OpenwaterHealth) (Low-Intensity Focused Ultrasound) platform. This repository contains transducer configurations, treatment protocols, example subject records with session data, system definitions, and user account structures.

## Purpose

This repository provides a reference database structure for OpenLIFU, intended for community contributors, researchers, and developers building OpenLIFU applications. All data is synthetic example data — no real patient information is included.

## Directory Structure

```
.
├── protocols/          # Treatment protocol definitions
├── subjects/           # Subject records, sessions, and derived data
│   └── <subject_id>/
│       ├── sessions/
│       │   └── <session_id>/
│       │       ├── photocollections/   # Raw photo sets for 3D reconstruction
│       │       ├── photoscans/         # Reconstructed 3D meshes (.obj, .mtl, .png)
│       │       ├── solutions/          # Simulation results (.json, .nc)
│       │       └── runs/               # Treatment run logs and snapshots
│       └── volumes/                    # Imaging volumes (NIfTI)
├── systems/            # Hardware system configurations
├── transducers/        # Transducer array configurations and 3D models
└── users/              # User account structures
```

## Contents

### Transducers (`/transducers/`)

Configuration files and 3D models for OpenLIFU transducer arrays:

| Transducer ID | Name | Frequency |
|---------------|------|-----------|
| openlifu_1x180_evt1 | OpenLIFU 1x 180kHz Demo | 180 kHz |
| openlifu_1x400_evt1 | OpenLIFU 1x 400kHz EVT1 | 400 kHz |
| openlifu_2x180_evt1 | OpenLIFU 2x 180kHz EVT1 | 180 kHz |
| openlifu_2x400_evt0 | OpenLIFU 2x 400kHz EVT0 | 400 kHz |
| openlifu_2x400_evt1 | OpenLIFU 2x 400kHz EVT1 | 400 kHz |
| openlifu_2x400_evt2b | OpenLIFU 2x 400kHz EVT2b | 400 kHz |

Each transducer folder contains a `.json` configuration (element positions, orientations) and `.obj` 3D models (body and surface meshes in LPS coordinates).

### Protocols (`/protocols/`)

Treatment protocol definitions:

| Protocol | Application | Frequency | Pulse Duration | Target Pressure |
|----------|-------------|-----------|----------------|-----------------|
| neuromod_demo | Neuromodulation | 400 kHz | 5 ms | 100 kPa |
| oncolysis_demo | Oncolysis | 180 kHz | 40 ms | 73 kPa |

### Systems (`/systems/`)

Hardware system configurations, including the Verasonics Vantage HIFU system definition.

### Subjects (`/subjects/`)

Example subject records showing the full data hierarchy. Each subject can have multiple treatment sessions, and each session can include:

- **Photocollections** — raw photo sets (JPEG) used for photogrammetric 3D reconstruction of the subject's head
- **Photoscans** — reconstructed 3D mesh outputs (OBJ/MTL/PNG texture)
- **Solutions** — acoustic simulation results stored as JSON metadata and NetCDF (`.nc`) data files
- **Runs** — treatment execution logs with protocol and session snapshots
- **Volumes** — medical imaging data (NIfTI format)

### Users (`/users/`)

Example user account structures for system access control.

There is an example admin user (username `example_admin`, password "example") to get started.

## 🚀 Quick Start
#### Test Credentials

The user JSON files contain password hashes. For testing purposes, the plaintext passwords are:

- `complex_user` / `complex_user_hash`
- `example_admin` / `example_admin_hash`
- `example_operator` / `example_operator_hash`
- `example_restricted` / `example_restricted_hash`

## Data Formats

- **JSON** — configuration and metadata (UTF-8, pretty-printed)
- **OBJ/MTL** — 3D models (ASCII format, LPS coordinate system)
- **NetCDF (.nc)** — simulation result arrays
- **NIfTI (.nii)** — medical imaging volumes
- **JPEG** — photocollection images
- **PNG** — texture maps for 3D meshes
- **VTK** — visualization data

Coordinates use the LPS (Left-Posterior-Superior) system, consistent with 3D Slicer.

## Quick Start

```python
import json

# Load a transducer configuration
with open('transducers/openlifu_2x400_evt1/openlifu_2x400_evt1.json') as f:
    transducer = json.load(f)

print(f"Transducer: {transducer['name']}")
print(f"Elements: {len(transducer['elements'])}")
```

## Git LFS

Large binary files (`.obj`, `.stl`, `.mat`, `.h5`, `.nli`, `.nii`, `.nii.gz`) are tracked with Git LFS. After cloning, run:

```bash
git lfs pull
```

## Related Repositories

**Software:** [OpenLIFU-python](https://github.com/OpenwaterHealth/OpenLIFU-python) | [OpenLIFU-api](https://github.com/OpenwaterHealth/OpenLIFU-api) | [SlicerOpenLIFU](https://github.com/OpenwaterHealth/SlicerOpenLIFU)

**Hardware:** [OpenLIFU-hardware-mechanical](https://github.com/OpenwaterHealth/OpenLIFU-hardware-mechanical) | [OpenLIFU-hardware-electrical](https://github.com/OpenwaterHealth/OpenLIFU-hardware-electrical)

**Documentation:** [OpenLIFU-docs](https://github.com/OpenwaterHealth/OpenLIFU-docs) | [OpenLIFU-examples](https://github.com/OpenwaterHealth/OpenLIFU-examples)

## Contributing

We welcome contributions. See the shared [CONTRIBUTING.md](https://github.com/OpenwaterHealth/openwater-commons/blob/main/CONTRIBUTING.md) for guidelines. To add new data, follow the existing directory structure, validate JSON files, and submit a pull request.

## License

Database contents are licensed under CC-BY-4.0 (Creative Commons Attribution 4.0). See [LICENSE](LICENSE) for details.

## Data Privacy

This repository contains **example data only** — no real patient information, no proprietary transducer designs. Safe for public distribution and suitable as a template for your own data.

## Support

- [GitHub Issues](https://github.com/OpenwaterHealth/openlifu-sample-database/issues)
- [GitHub Discussions](https://github.com/OpenwaterHealth/openlifu-sample-database/discussions)
- [Discord #openlifu channel](https://discord.gg/openwater)
