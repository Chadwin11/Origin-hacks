# Origin

> A NO-CODE platform that enables users to control and program robots using simple intuitive visual workflows or natural language, eliminating the need for technical expertise.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📌 Problem Statement

Controlling industrial mobile robots usually requires complex coding and technical expertise, which makes it hard for non-experts to use.
There's no simple way to visually design and manage robot actions, making automation slow and difficult.

---

## 🚀 Features

| Feature | Description |
|--------|-------------|
| 🧩 Visual Flow Builder | Drag-and-drop interface to create robot workflows using connected nodes |
| 🧠 Prompt-to-Flow (AI) | Convert natural language instructions into executable workflows |
| 🧱 Workflow Nodes | Predefined blocks like Move, Turn, Pick, Drop, and logic nodes (IF/ELSE) |
| ⚙️ Workflow Execution Engine | Executes workflows step-by-step with full control over execution state |
| ▶️ Run / Pause / Resume / Stop | Complete control over workflow execution lifecycle |
| 📊 Real-Time Dashboard | Displays robot status including battery, position, and system health |
| 🎮 Manual Control Panel | Directly control robot movement using a D-pad interface |
| 🚨 Emergency Stop (E-STOP) | Instantly halts robot operations for safety |
| 🎮 Simulation Mode (Digital Twin) | Simulates robot behavior in a virtual environment before execution |
| 🧠 Workflow Validation | Detects errors, missing steps, and invalid logic before execution |
| 📡 Real-Time Communication | WebSocket-based live updates between frontend and backend |
| 🤖 ROS2 Integration | Connects to real robots using ROS2 and rosbridge for real-world deployment |
| 📦 Command Generator | Converts workflows into structured JSON commands for execution |
| 📁 Workflow Management | Create, save, load, update, and delete workflows |
| 🧩 Workflow Templates | Pre-built workflows like Patrol, Delivery, and Pick & Place |
| 🧾 Logging System | Tracks execution logs, errors, and system events with timestamps |
| 🌐 RESTful API | Backend APIs for workflow control, robot status, and system operations |
| 🖥️ Modern UI | Responsive React interface with interactive components |
| 🗺️ Map Visualization Mode | Radar map and camera-based view of robot environment |
| 🧠 AI Chat Assistant | ARIA — AI assistant for natural language robot control |
| 👤 Authentication | Login system with session management |

---

## 🏗️ Tech Stack

### Frontend
- ⚛️ React.js — Component-based UI
- 🔗 React Flow — Drag-and-drop workflow builder
- ⚡ Vite — Fast development server and build tool
- 📡 WebSockets (Socket.io / native) — Real-time communication
- 🎮 HTML Canvas — 2D simulation and visualization
- 🗄️ Supabase — Authentication and data layer

### Backend
- 🟢 Node.js — Runtime environment
- 🚀 Express.js — REST API framework
- 📡 WebSocket Server — Real-time data exchange
- 🤖 ROS2 (rosbridge) — Robot communication layer
- 🧠 OpenAI / Gemini API — Natural language → workflow conversion
- 💾 Prisma ORM — Database schema and management

---

## 📂 Project Structure

```
Origin/
├── backend/
│   ├── server.js                     # Express server entry point & API routes
│   ├── workflowEngine.js             # Core workflow execution engine
│   ├── ros2Bridge.js                 # ROS2 (rosbridge) communication layer
│   ├── prisma/
│   │   └── schema.prisma             # Database schema (Prisma ORM)
│   ├── .env                          # Environment configuration
│   └── package.json                  # Backend dependencies
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── AIChatPanel.jsx       # AI assistant (ARIA) chat interface
│   │   │   ├── ControlPanel.jsx      # Manual robot control (D-pad)
│   │   │   ├── CustomNode.jsx        # Custom workflow node renderer
│   │   │   ├── Dashboard.jsx         # System/robot status dashboard
│   │   │   ├── DigitalTwinMaster.jsx # Digital twin simulation controller
│   │   │   ├── EmergencyStop.jsx     # E-STOP button component
│   │   │   ├── FlowBuilder.jsx       # Drag-and-drop workflow builder
│   │   │   ├── Header.jsx            # Top navigation bar
│   │   │   ├── Login.jsx             # Authentication/login screen
│   │   │   ├── LoginBackground.jsx   # Animated login background
│   │   │   ├── RadarMap.jsx          # Radar/map visualization
│   │   │   ├── RobotSim.jsx          # Robot simulation component
│   │   │   ├── RobotSimulation.jsx   # Full simulation environment
│   │   │   ├── Sidebar.jsx           # Navigation sidebar
│   │   │   └── SimulationView.jsx    # Simulation view panel
│   │   │
│   │   ├── pages/
│   │   │   └── Simulation.jsx        # Simulation page
│   │   │
│   │   ├── assets/
│   │   │   └── hero.png              # Hero/branding image
│   │   │
│   │   ├── App.jsx                   # Root component & routing
│   │   ├── App.css                   # Global styles
│   │   ├── index.css                 # Base CSS
│   │   ├── main.jsx                  # Entry point
│   │   ├── MapConfig.js              # Map configuration
│   │   ├── rosService.js             # ROS service client (frontend)
│   │   └── supabaseClient.js         # Supabase client setup
│   │
│   ├── public/
│   │   ├── favicon.svg               # App favicon
│   │   └── icons.svg                 # Icon set
│   │
│   ├── index.html                    # HTML template
│   ├── vite.config.js                # Vite configuration
│   └── package.json                  # Frontend dependencies
│
├── docker-compose.yml                # Containerized setup
├── README.md                         # Project documentation
└── .gitignore                        # Git ignore rules
```

---

## ⚙️ Installation & Setup

### Prerequisites
- Node.js 18+
- npm (comes with Node.js)
- ROS2 with `rosbridge_server` *(optional — simulation mode works without it)*
- Docker *(optional)*

### 1. Clone the Repository

```bash
git clone https://github.com/Chadwin11/Origin-hacks.git
cd Origin
```

### 2. Backend Setup

```bash
cd backend
npm install
npm start
```

Backend runs at `http://localhost:3001`

### 3. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs at `http://localhost:5173`

---

## 🧠 How It Works

### System Flow

1. User interacts with the frontend UI to create workflows, send commands, or monitor system state
2. Frontend sends requests to the backend via REST APIs and establishes a WebSocket connection for real-time updates
3. Backend receives requests and routes them through Express handlers
4. Workflow engine parses incoming workflow definitions and determines execution order
5. Backend executes each workflow step sequentially or conditionally
6. Commands are either sent to a real robot (via ROS2) or handled in simulation mode
7. Backend streams execution progress and system status back to frontend
8. Frontend renders updates dynamically for real-time user feedback

### ROS2 Integration Flow

1. User enables robot connectivity and provides a ROS bridge endpoint
2. Backend connects to `rosbridge_server` using WebSocket (`ROSBRIDGE_URL`)
3. Workflow actions are translated into ROS topic messages
4. Backend publishes commands (e.g., movement, actions) to ROS topics
5. Backend subscribes to robot topics (status, telemetry, sensors)
6. Incoming ROS messages are processed and converted into usable data
7. Data is streamed back to frontend via WebSocket for live visualization

### Simulation Flow

1. If ROS2 is not configured, backend runs in simulation mode
2. Workflow steps are executed logically without real hardware
3. Mock data simulates robot responses and state changes
4. Backend tracks execution progress internally
5. Simulated updates are emitted to frontend in real time
6. Frontend displays results as if interacting with a real system

### Workflow Execution Flow

1. User defines or triggers a workflow through the UI
2. Workflow is sent to backend for processing
3. Backend parses steps and determines execution logic
4. Each step is executed in order or based on conditions
5. Actions are dispatched to ROS2 or simulation engine
6. Execution state is tracked and updated continuously
7. Results and progress are streamed back to frontend for display

---

## 📈 Scalability

* Backend can be containerized using Docker and scaled horizontally behind a load balancer
* WebSocket layer supports multiple clients simultaneously
* Workflow engine can be decoupled into background workers for parallel execution
* ROS2 integration allows distributed robot systems via separate ROS bridge endpoints
* Frontend is a lightweight Vite/React app deployable via CDN
* Simulation mode enables scaling development and testing without physical hardware

---

## 💡 Feasibility

Built using production-ready technologies (Node.js, Express, React, WebSockets, Supabase), ensuring strong community support and reliability. ROS2 integration leverages existing robotics infrastructure. Simulation mode removes the dependency on physical robots, allowing development and testing in any environment.

---

## 🌟 Novelty

Most robotics control systems require complex setups limited to robotics experts. Origin introduces a unified, web-based platform that allows users to design, execute, and monitor robot workflows in real time through an intuitive interface. The combination of a workflow engine, AI chat assistant (ARIA), live WebSocket communication, and optional ROS2 connectivity enables both simulation and real-world execution within the same system — making robotics accessible to a broader audience beyond traditional developers.

---

## ⚠️ Ethical Use & Disclaimer

This project is intended strictly for **educational, research, and authorized robotics development purposes only**.

Do **NOT** use this system to control, access, or interact with any robot, device, or network without **explicit permission** from the owner.

Always validate workflows in **simulation mode** before deploying them to real-world systems.

Use responsibly, ethically, and within legal and safety boundaries.

---

## 📜 License

Licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes:
   - `frontend/` for UI changes
   - `backend/` for APIs, workflows, or integrations
4. Commit your changes: `git commit -m "Add feature-name"`
5. Push to your fork: `git push origin feature-name`
6. Open a Pull Request with a clear description

**Guidelines:**
- Follow existing project structure and coding style
- Test features in simulation mode before submitting
- Ensure backend and frontend both run without errors
- For ROS-related features, include fallback/simulation support

---

## 🧩 Authors

**Dhurgesh S**
📧 [dhurgesh1011@gmail.com](mailto:dhurgesh1011@gmail.com)
🔗 [GitHub](https://github.com/dhurgesh1011-ai)

**Aahil M S**
📧 [aahilms2007@gmail.com](mailto:aahilms2007@gmail.com)
🔗 [GitHub](https://github.com/aahil-ms)

**Chadwin L**
📧 [chadwinlazur@gmail.com](mailto:chadwinlazur@gmail.com)
🔗 [GitHub](https://github.com/Chadwin11)

**Akash M**
📧 [akashmariappan007@gmail.com](mailto:akashmariappan007@gmail.com)
🔗 [GitHub](https://github.com/Akash12072007)
