# Advanced Databases - Assignment 1

**AD-ODM (Assignment 1)** is the foundational Python MongoDB ODM implementation for a progressive Advanced Databases college project at U-TAD.

**Academic Project Details:**
- **Degree**: Software Engineering
- **University**: U-tad
- **Subject**: Advanced Databases
- **Authors**: Emilie Dubief, Itziar Morales Rodríguez

**Part 1/3**: Core ODM design (this branch) → Usage implementation → Redis caching.

## Key Features
- Object-Document Mapping (ODM) for MongoDB in pure Python.
- Geographic data handling (`geo.py`) for location-based queries.
- Model definitions via YAML schemas (`models.yml`).
- Mock data loading for users, companies, educational centers.

## Tech Stack
- **Language**: Python 3.12
- **Database**: MongoDB
- **Dependencies**: Nix (environment management)
- **Documentation**: LaTeX (`doc.pdf`)

## Project Structure
```
project_root/
|-- ODM/                 # Core ODM implementation
|   |-- __init__.py
|   |-- app.py          # Main application entrypoint
|   |-- geo.py          # Geospatial functionality
|   |-- model.py        # Model definitions & mapping
|-- data/                # Mock datasets + schemas
|   |-- users.json
|   |-- companies.json
|   |-- educational_centers.json
|   |-- models.yml
|-- README.md
|-- ODM.py              # Main executable
|-- doc.pdf             # Project documentation
|-- shell.nix           # Nix environment
```

## Setup & Run
1. **Install Nix** (if needed):
   ```bash
   sh <(curl --proto '=https' --tlsv1.2 -L https://nixos.org/nix/install) --daemon
   ```

2. **Enter development environment**:
   ```bash
   nix-shell
   ```

3. **Run the ODM**:
   ```bash
   python ODM.py
   ```

## Progression Across Branches
- **assignment-1** (current): Core ODM design
- **assignment-2**: Real-world application usage
- **assignment-3**: Redis caching layer integration

See `doc.pdf` for detailed technical explanation.
