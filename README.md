# OpenLIFU Sample Database

Example database structure for the OpenLIFU (Low-Intensity Focused Ultrasound) system.

## 🎯 Purpose

This repository provides a **reference database structure** for OpenLIFU, including:
- Transducer array configurations
- Treatment protocol definitions
- Example subject records
- User account structures

**Intended for:** Community contributors, researchers, and developers building OpenLIFU applications.

## 📦 Contents

### Transducers (`/transducers/`)

Configuration files and 3D models for OpenLIFU transducer arrays:

| Transducer ID | Name | Frequency | Elements |
|---------------|------|-----------|----------|
| openlifu_2x400_evt1_005 | OpenLIFU 2x 400kHz EVT1 S/N 005 | 400kHz | 2x16 |
| openlifu_2x400_evt1 | OpenLIFU 2x 400kHz EVT1 | 400kHz | 2x16 |
| openlifu_2x400_evt2a | OpenLIFU 2x 400kHz EVT2a | 400kHz | 2x16 |
| openlifu_2x180_evt1 | OpenLIFU 2x 180kHz EVT1 | 180kHz | 2x16 |
| openlifu_1x400_evt1 | OpenLIFU 1x 400kHz EVT1 | 400kHz | 16 |
| openlifu_1x180_evt1 | OpenLIFU 1x 180kHz Demo | 180kHz | 16 |

Each transducer folder contains:
- `.json` - Array configuration (element positions, orientations)
- `.obj` - 3D models (body and surface meshes in LPS coordinates)

### Protocols (`/protocols/`)

Treatment protocol definitions:

| Protocol | Application | Frequency | Pulse Duration | Pressure |
|----------|-------------|-----------|----------------|----------|
| oncolysis_demo | Oncolysis | 180 kHz | 40 ms | 73 kPa |
| neuromod_demo | Neuromodulation | 400 kHz | 5 ms | 100 kPa |

### Subjects (`/subjects/`)

Example subject records showing data structure for patient/subject information.

### Users (`/users/`)

Example user account structures for system access control.

## 🚀 Quick Start

### Loading Transducer Configuration
```python
import json

# Load transducer config
with open('transducers/openlifu_2x400_evt1_005/openlifu_2x400_evt1_005.json') as f:
    transducer = json.load(f)

print(f"Transducer: {transducer['name']}")
print(f"Elements: {len(transducer['elements'])}")
```

### Visualizing 3D Models
```python
# Visualize .obj files with your preferred 3D viewer
# Compatible with: 3D Slicer, MeshLab, Blender, etc.
```

### Validating Database Structure
```bash
# Run validation script
python scripts/validate_database.py
```

## 📚 Documentation

- [Database Schema](docs/database-schema.md) - JSON schema definitions
- [Transducer Specifications](docs/transducer-specs.md) - Detailed comparison
- [Protocol Guide](docs/protocol-guide.md) - Creating custom protocols
- [Getting Started](docs/getting-started.md) - Tutorial for new users

## 🔗 Related Repositories

### Software
- [OpenLIFU-python](https://github.com/OpenwaterHealth/OpenLIFU-python) - Python library to use this data
- [OpenLIFU-api](https://github.com/OpenwaterHealth/OpenLIFU-api) - REST API
- [SlicerOpenLIFU](https://github.com/OpenwaterHealth/SlicerOpenLIFU) - 3D Slicer extension

### Hardware
- [OpenLIFU-hardware-mechanical](https://github.com/OpenwaterHealth/OpenLIFU-hardware-mechanical) - CAD files
- [OpenLIFU-hardware-electrical](https://github.com/OpenwaterHealth/OpenLIFU-hardware-electrical) - Schematics

### Documentation
- [OpenLIFU-docs](https://github.com/OpenwaterHealth/OpenLIFU-docs) - Platform documentation
- [OpenLIFU-examples](https://github.com/OpenwaterHealth/OpenLIFU-examples) - Code examples

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](https://github.com/OpenwaterHealth/openwater-commons/blob/main/CONTRIBUTING.md)

**To add new data:**
1. Follow existing structure (see DATABASE-STRUCTURE.md)
2. Validate JSON against schemas
3. Include README in new folders
4. Submit pull request

## 📊 Data Format

All data follows standardized formats:
- **JSON** - Configuration and metadata (UTF-8, pretty-printed)
- **OBJ** - 3D models (ASCII format, LPS coordinate system)
- **Coordinates** - LPS (Left-Posterior-Superior) as used in 3D Slicer

## 📜 License

**Database contents:** CC-BY-4.0 (Creative Commons Attribution 4.0)
- ✅ Use for any purpose
- ✅ Modify and redistribute
- ✅ Commercial use allowed
- ✅ Attribution required

See [LICENSE](LICENSE) for details.

## 🔒 Data Privacy

⚠️ **This is EXAMPLE DATA ONLY**
- No real patient information
- No proprietary transducer designs
- Safe for public distribution
- Use as template for your own data

## 🆘 Support

- **Issues:** [GitHub Issues](https://github.com/OpenwaterHealth/OpenLIFU-sample-database/issues)
- **Discussions:** [GitHub Discussions](https://github.com/OpenwaterHealth/OpenLIFU-sample-database/discussions)
- **Discord:** [#openlifu channel](https://discord.gg/openwater)
- **Documentation:** [docs.openwater.health](https://docs.openwater.health)

## 📦 File Sizes & Git LFS

Large binary files (`.obj` 3D models) are stored using Git LFS:
- Clone with: `git lfs pull`
- Binary files tracked in `.gitattributes`
- See [Git LFS docs](https://git-lfs.github.com/) for more info

---

**Example database structure for the OpenLIFU open-source ultrasound platform** 🔬🧠
