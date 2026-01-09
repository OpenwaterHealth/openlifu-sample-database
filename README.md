## Sample Data

Example database structure available at:
[OpenLIFU-sample-database](https://github.com/OpenwaterHealth/OpenLIFU-sample-database)
```python
from openlifu import Database

# Load sample database
db = Database('path/to/OpenLIFU-sample-database')

# Load transducer
transducer = db.load_transducer('openlifu_2x400_evt1_005')
```

### Update OpenLIFU-docs

Add to data management section:
```markdown
### Database Structure

OpenLIFU uses a standardized database structure for transducers, protocols, and subjects.

**Reference implementation:** [OpenLIFU-sample-database](https://github.com/OpenwaterHealth/OpenLIFU-sample-database)
```

### Update OpenLIFU-examples

Add example using the database:
```python
# examples/load_sample_database.py
"""
Example: Loading data from OpenLIFU sample database
"""
import json
from pathlib import Path

# Clone sample database first:
# git clone https://github.com/OpenwaterHealth/OpenLIFU-sample-database.git

db_path = Path('../OpenLIFU-sample-database')

# Load transducer
with open(db_path / 'transducers/openlifu_2x400_evt1_005/openlifu_2x400_evt1_005.json') as f:
    transducer = json.load(f)

print(f"Loaded: {transducer['name']}")
print(f"Elements: {len(transducer['elements'])}")
```

---

## 📋 TOPICS/TAGS TO ADD

When you create the repo, add these topics:
