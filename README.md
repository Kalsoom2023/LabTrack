# LabTrack2 - MCP Pipeline Project

## Quick Start (After Downloading ZIP)

### Prerequisites
- Node.js v18 or higher
- npm (comes with Node.js)

### Installation Steps

1. **Extract the ZIP file** and open a terminal in the `LabTrack2` folder

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Run the development server:**
   ```bash
   npm run dev
   ```

4. **Open your browser:**
   ```
   http://localhost:5000
   ```

5. **Login credentials:**
   - Username: `ali01` | Password: `password` (Manager)
   - Username: `ayeshaM` | Password: `password` (Admin)

6. **Navigate to "MCP Pipeline"** in the sidebar to see the visual flow

---

## Testing the MCP API with Postman

### Base URL (Local)
```
http://localhost:5000
```

### Available Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/mcp/projects` | List all projects |
| GET | `/api/mcp/projects/:id` | Get specific project |
| POST | `/api/mcp/projects` | Submit new project |
| POST | `/api/mcp/projects/:id/reprocess` | Rerun AI analysis |
| DELETE | `/api/mcp/projects/:id` | Delete project |
| GET | `/api/mcp/stats` | Get pipeline statistics |

### Example: Submit a Project (POST)

**URL:** `http://localhost:5000/api/mcp/projects`

**Headers:**
```
Content-Type: application/json
```

**Body:**
```json
{
  "title": "My AI Project",
  "estimated_cost": 25000,
  "estimated_time_needed": "3 months",
  "required_team": ["AI/ML Engineer", "Frontend Developer", "Backend Developer"],
  "required_resources": ["GPU Server", "Desktop PC", "Monitor"],
  "complexity_level": "High"
}
```

**Response:**
```json
{
  "message": "Project submitted for AI analysis",
  "project": {
    "id": "mcp-1733590800000-abc123xyz",
    "status": "pending",
    "originalInput": {...}
  }
}
```

### Import Postman Collection
Import `MCP_Postman_Collection.json` into Postman for pre-configured requests.

---

## MCP Pipeline Flow

```
INPUT (Postman/UI)
       ↓
  API Request (/api/mcp/projects)
       ↓
  Validation (check required fields)
       ↓
  Storage (save to data/mcp-projects.json)
       ↓
  AI Processing (match team & resources)
       ↓
OUTPUT (AI Recommendations)
  - Team Allocation
  - Resource Allocation
  - Budget Optimization
  - Risk Assessment
  - Timeline Milestones
```

---

## Project Structure

```
LabTrack2/
├── client/           # React frontend
├── server/           # Express backend
│   ├── mcpRoutes.ts  # MCP API endpoints
│   └── services/
│       ├── agenticAI.ts    # AI logic
│       └── mcpStorage.ts   # JSON storage
├── data/             # Project data storage
└── MCP_Postman_Collection.json  # Postman collection
```

