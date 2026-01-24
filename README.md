# Advanced Databases - Assignment 3

**AD-ODM (Assignment 3)** extends the ODM with Redis caching, session management, and HelpDesk for the Advanced Databases college project at U-TAD.

**Academic Project Details:**
- **Degree**: Software Engineering
- **University**: U-tad
- **Subject**: Advanced Databases
- **Authors**: Emilie Dubief, Itziar Morales Rodríguez

**Part 3/3**: Core ODM (assignment-1) → Usage (assignment-2) → **Redis caching + Sessions/HelpDesk** (this branch).

## Key Features
- Redis caching for ODM read ops (find, aggregate, find_by_id) with TTL=24h.
- Session management: Redis hashes (`user:username`) + expiring tokens (`token:value`).
- HelpDesk: Priority queues (`HelpRequests`) + individual request hashes.
- Jupyter queries (`queries.ipynb`) + testing scripts (`help_desk.py`, `send_request.py`).
- Write-through/invalidation for cache consistency.

## Tech Stack
- **Language**: Python 3.12
- **Databases**: MongoDB + Redis (cache, sessions, queues)
- **Notebook**: Jupyter Lab
- **Environments**: Conda (`environment.yml`), Nix (`shell.nix`)
- **Documentation**: LaTeX (`doc.pdf`)

## Project Structure
```
project_root/
|-- ODM/                 # Enhanced ODM with Redis caching
|   |-- __init__.py
|   |-- app.py
|   |-- geo.py
|   |-- model.py
|-- data/                # Mock data + schemas
|   |-- users.json
|   |-- companies.json
|   |-- educational_centers.json
|   |-- models.yml
|-- queries.ipynb        # Query notebook
|-- help_desk.py         # HelpDesk server
|-- send_request.py      # Request client
|-- session_help_desk_test.py
|-- sessions.py          # Session utils
|-- environment.yml      # Conda env
|-- shell.nix            # Nix env
|-- README.md
```

## Redis Data Design
- **Sessions**: `user:username` → hash {username, fullname, password, privileges}; `token:token_value` → username (exp: 1 month).
- **HelpDesk**: `HelpRequests` list → `priority:token` IDs; `priority:token` → hash {username, message}.
- **ODM Cache**: `<Model>:byid:<id>`, `<Model>:find:<filter>`, `<Model>:aggregate:<pipeline>` (TTL: 24h).

## Setup & Run

### Prerequisites
- MongoDB service running.
- Redis server running (default localhost:6379).

### Option 1: Conda
```bash
conda env create -f environment.yml
conda activate ODMEmilieItziarRedis
python -m ipykernel install --user --name ODMEmilieItziarRedis --display-name "Python (ODMEmilieItziarRedis)"
jupyter lab
```

### Option 2: Nix
```bash
sh <(curl --proto '=https' --tlsv1.2 -L https://nixos.org/nix/install) --daemon
nix-shell
jupyter lab
```

## Usage Examples
1. **Queries**: Open `queries.ipynb` → Run all cells.
2. **HelpDesk Test**:
   - Terminal 1: `python help_desk.py`
   - Terminal 2: `python send_request.py`
3. **Sessions**: Use `sessions.py` for token/session ops.

## Cache Mechanics
- **Reads** (`find`, `aggregate`, `find_by_id`): Check Redis → Cache miss → MongoDB → Cache JSON (ex=86400s).
- **Writes** (`save`, `delete`): Update DB + by-id cache → Invalidate find/aggregate via SCAN+DEL.

## Troubleshooting
- **Jupyter rendering**: Restart kernel → Run All.
- **ODM Geo**: API timeouts possible (unavoidable for tests).
- **Session.create**: Raises on missing fields or duplicate username.
- **HelpDesk**: Check Redis connections.

## Full Progression
- **assignment-1**: Core ODM
- **assignment-2**: Query usage
- **assignment-3** (current): Redis caching, sessions, HelpDesk

Detailed in `doc.pdf`.
