# Advanced Databases - Assignment 2

**AD-ODM (Assignment 2)** demonstrates practical usage of the core ODM through real-world queries for the Advanced Databases college project at U-TAD.

**Academic Project Details:**
- **Degree**: Software Engineering
- **University**: U-tad
- **Subject**: Advanced Databases
- **Authors**: Emilie Dubief, Itziar Morales Rodríguez

**Part 2/3**: Core ODM (assignment-1) → **Usage implementation** (this branch) → Redis caching (assignment-3).

## Key Features
- Jupyter notebook (`queries.ipynb`) executing complex ODM queries.
- Real-world data operations on users, companies, educational centers.
- Multiple environment support (Conda + Nix).
- Geospatial queries leveraging `geo.py` functionality.

## Tech Stack
- **Language**: Python 3.12
- **Database**: MongoDB
- **Notebook**: Jupyter Lab
- **Environments**: Conda (`environment.yml`), Nix (`shell.nix`)
- **Documentation**: LaTeX (`doc.pdf`)

## Project Structure
```
project_root/
|-- ODM/                 # Core ODM (from Assignment 1)
|   |-- __init__.py
|   |-- app.py
|   |-- geo.py
|   |-- model.py
|-- data/                # Mock datasets + schemas
|   |-- users.json
|   |-- companies.json
|   |-- educational_centers.json
|   |-- models.yml
|-- queries.ipynb        # Main query notebook
|-- environment.yml      # Conda environment
|-- shell.nix           # Nix environment
|-- README.md
```

## Setup & Run

### Option 1: Conda (Recommended)
```bash
# Create & activate environment
conda env create -f environment.yml
conda activate ODMEmilieItziar

# Register Jupyter kernel
python -m ipykernel install --user --name ODMEmilieItziar --display-name "Python (ODMEmilieItziar)"

# Start Jupyter
jupyter lab
```

### Option 2: Nix
```bash
# Install Nix
sh <(curl --proto '=https' --tlsv1.2 -L https://nixos.org/nix/install) --daemon

# Enter environment & start Jupyter
nix-shell
jupyter lab
```

**Prerequisites**: MongoDB service running locally.

## Usage
1. Open `queries.ipynb` in Jupyter Lab.
2. Run all cells sequentially (restart if rendering issues occur).
3. Explore ODM queries on mock educational platform data.

## Troubleshooting
- **Kernel issues**: Re-register kernel (Conda instructions above).
- **Rendering problems**: Restart kernel → Run All Cells.

## Progression Across Branches
- **assignment-1**: Core ODM design
- **assignment-2** (current): Query implementation & usage
- **assignment-3**: Redis caching optimization

See `doc.pdf` for detailed query explanations.
