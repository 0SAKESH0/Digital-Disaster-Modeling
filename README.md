# Frontend Application - Digital Disaster Modeling

This is the Next.js frontend application for the Digital Disaster Modeling platform. It provides an interactive user interface for uploading blueprint images, converting them to 3D models, running disaster simulations, predicting damage, and generating evacuation routes.

## 📋 Table of Contents

- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running the Frontend](#running-the-frontend)
- [Project Structure](#project-structure)
- [Features](#features)
- [Pages & Components](#pages--components)
- [API Integration](#api-integration)
- [Styling](#styling)
- [Environment Variables](#environment-variables)
- [Building for Production](#building-for-production)
- [Docker Setup](#docker-setup)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## 🛠️ Technology Stack

- **Framework**: Next.js 13+ with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: React components with custom styling
- **State Management**: React Context API / Zustand (optional)
- **HTTP Client**: Axios / Fetch API
- **3D Visualization**: Three.js
- **Package Manager**: npm / yarn

## 📦 Prerequisites

- **Node.js 18+** (LTS recommended)
- **npm 9+** or **yarn 3+**
- **Git** (for version control)
- **Modern web browser** (Chrome, Firefox, Safari, Edge)
- **Backend API** running on `http://localhost:8000`

## 🚀 Setup

### 1. Install Dependencies

```bash
cd webapp/frontend
npm install
# or
yarn install
```

### 2. Environment Variables

Create a `.env.local` file in the frontend directory:

```env
# API Configuration
NEXT_PUBLIC_API_URL=http://localhost:8000/api
NEXT_PUBLIC_API_TIMEOUT=30000

# Application
NEXT_PUBLIC_APP_NAME=Digital Disaster Modeling
NEXT_PUBLIC_APP_VERSION=1.0.0

# Features
NEXT_PUBLIC_ENABLE_3D_PREVIEW=true
NEXT_PUBLIC_ENABLE_SIMULATION=true
NEXT_PUBLIC_ENABLE_DAMAGE_PREDICTION=true

# File Upload
NEXT_PUBLIC_MAX_FILE_SIZE=50
NEXT_PUBLIC_ALLOWED_EXTENSIONS=jpg,jpeg,png,gif

# Logging
NEXT_PUBLIC_LOG_LEVEL=info
```

### 3. Build Next.js

```bash
npm run build
# or
yarn build
```

## ▶️ Running the Frontend

### Development Mode (with hot reload)

```bash
npm run dev
# or
yarn dev
```

Access the application at: `http://localhost:3000`

### Production Mode

```bash
npm run build
npm run start
# or
yarn build
yarn start
```

## 📁 Project Structure

```
webapp/frontend/
├── public/                 # Static assets
│   ├── images/            # Images and icons
│   ├── models/            # Example 3D models
│   └── favicon.ico        # Favicon
│
├── src/
│   ├── app/               # Next.js 13 App Router
│   │   ├── layout.tsx     # Root layout
│   │   ├── page.tsx       # Home page
│   │   ├── upload/        # Blueprint upload page
│   │   ├── model/         # 3D model viewer page
│   │   ├── simulate/      # Simulation page
│   │   ├── damage/        # Damage prediction page
│   │   ├── evacuation/    # Evacuation routes page
│   │   └── api/           # API routes (if needed)
│   │
│   ├── components/        # Reusable React components
│   │   ├── Header.tsx     # Header component
│   │   ├── Navigation.tsx # Navigation bar
│   │   ├── FileUpload.tsx # File upload component
│   │   ├── ModelViewer.tsx# 3D model viewer
│   │   ├── SimulationPanel.tsx
│   │   ├── DamageMap.tsx  # Damage visualization
│   │   ├── EvacuationRoute.tsx
│   │   └── Footer.tsx     # Footer component
│   │
│   ├── lib/               # Utility functions
│   │   ├── api.ts         # API client
│   │   ├── utils.ts       # Helper functions
│   │   ├── validators.ts  # Input validation
│   │   └── constants.ts   # Constants
│   │
│   ├── hooks/             # Custom React hooks
│   │   ├── useApi.ts      # API hook
│   │   ├── useUpload.ts   # Upload hook
│   │   └── useModelViewer.ts
│   │
│   ├── styles/            # Global styles
│   │   ├── globals.css    # Global CSS
│   │   └── variables.css  # CSS variables
│   │
│   ├── types/             # TypeScript type definitions
│   │   ├── api.ts         # API types
│   │   ├── models.ts      # Data models
│   │   └── ui.ts          # UI types
│   │
│   └── store/             # State management (optional)
│       └── appStore.ts    # App state
│
├── styles/                # Additional stylesheets
│   └── tailwind.config.js # Tailwind configuration
│
├── .env.local            # Environment variables (create locally)
├── .env.example          # Example environment variables
├── next.config.js        # Next.js configuration
├── tsconfig.json         # TypeScript configuration
├── tailwind.config.js    # Tailwind CSS configuration
├── package.json          # Dependencies
└── README.md            # This file
```

## ✨ Features

### 1. **Blueprint Upload**
- Drag-and-drop file upload
- Image preview before upload
- Support for JPG, PNG, GIF formats
- Real-time upload progress
- File size validation

### 2. **3D Model Conversion**
- Convert 2D blueprints to 3D models
- Interactive 3D viewer (Three.js)
- Model rotation, zoom, pan controls
- Multiple view modes (perspective, orthographic)
- Export to GLB/OBJ formats

### 3. **Disaster Simulation**
- Simulate multiple disaster types:
  - 🔥 Fire spread
  - 💧 Flood dynamics
  - 🌍 Earthquake effects
- Real-time simulation visualization
- Adjustable simulation parameters
- Simulation speed control
- Download simulation results

### 4. **Damage Prediction**
- Predict damage severity per area
- Color-coded damage visualization
- Detailed damage reports
- Statistical analysis
- Export damage maps

### 5. **Evacuation Route Generation**
- Optimal escape path calculation
- Multi-exit handling
- Real-time route visualization
- Reachable exit detection
- Route optimization algorithms
- Download evacuation paths

### 6. **Dashboard**
- Project management
- Recent projects list
- Favorites/bookmarks
- Search and filter
- Project statistics

## 📄 Pages & Components

### Pages

| Route | Component | Description |
|-------|-----------|-------------|
| `/` | `page.tsx` | Home/landing page |
| `/upload` | `upload/page.tsx` | Blueprint upload page |
| `/model` | `model/page.tsx` | 3D model viewer |
| `/simulate` | `simulate/page.tsx` | Disaster simulation |
| `/damage` | `damage/page.tsx` | Damage prediction |
| `/evacuation` | `evacuation/page.tsx` | Evacuation routes |
| `/dashboard` | `dashboard/page.tsx` | User dashboard |
| `/about` | `about/page.tsx` | About page |

### Key Components

- **FileUpload**: Drag-drop file upload with validation
- **ModelViewer**: Three.js based 3D model viewer
- **SimulationPanel**: Control panel for disaster simulations
- **DamageVisualization**: Heatmap for damage display
- **EvacuationMap**: Route visualization component
- **ProgressIndicator**: Multi-step workflow progress
- **Modal**: Reusable modal dialogs

## 🔌 API Integration

### API Client

```typescript
// lib/api.ts
import axios, { AxiosInstance } from 'axios';

const api: AxiosInstance = axios.create({
  baseURL: process.env.NEXT_PUBLIC_API_URL,
  timeout: parseInt(process.env.NEXT_PUBLIC_API_TIMEOUT || '30000'),
});

// Usage in components
const uploadBlueprint = async (file: File) => {
  const formData = new FormData();
  formData.append('file', file);
  const response = await api.post('/blueprints/upload', formData);
  return response.data;
};
```

### API Calls

```typescript
// Upload blueprint
POST /api/blueprints/upload

// Convert to 3D model
POST /api/convert
GET /api/models/{id}

// Run simulation
POST /api/simulate
GET /api/simulations/{id}

// Predict damage
POST /api/damage/predict
GET /api/damage/{id}

// Generate evacuation
POST /api/evacuation/generate
GET /api/evacuation/{id}
```

## 🎨 Styling

### Tailwind CSS Setup

```javascript
// tailwind.config.js
module.exports = {
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx}',
    './src/components/**/*.{js,ts,jsx,tsx}',
    './src/app/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {
      colors: {
        primary: '#3B82F6',
        secondary: '#1F2937',
      },
    },
  },
  plugins: [],
};
```

### CSS Variables

```css
/* styles/variables.css */
:root {
  --color-primary: #3b82f6;
  --color-secondary: #1f2937;
  --color-accent: #f59e0b;
  --color-success: #10b981;
  --color-error: #ef4444;
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
}
```

## 🔧 Environment Variables

### Development

```env
NEXT_PUBLIC_API_URL=http://localhost:8000/api
NEXT_PUBLIC_DEBUG=true
```

### Production

```env
NEXT_PUBLIC_API_URL=https://api.example.com/api
NEXT_PUBLIC_DEBUG=false
NODE_ENV=production
```

## 🔨 Building for Production

### Build Optimization

```bash
# Build with optimization
npm run build

# Analyze bundle size
npm run analyze

# Generate static export (if needed)
npm run export
```

### Performance Optimization

- Image optimization with Next.js Image component
- Code splitting and lazy loading
- CSS modules for scoped styling
- Dynamic imports for large components

```typescript
// Dynamic import example
const ModelViewer = dynamic(() => import('@/components/ModelViewer'), {
  loading: () => <LoadingSpinner />,
  ssr: false,
});
```

## 🐳 Docker Setup

### Build Docker Image

```bash
docker build -f Dockerfile.frontend -t digital-disaster-frontend:latest .
```

### Run Container

```bash
docker run -p 3000:3000 digital-disaster-frontend:latest
```

### Docker Compose

```bash
docker-compose up frontend
```

## 🚀 Deployment

### Vercel (Recommended for Next.js)

1. Push code to GitHub
2. Connect repository to Vercel
3. Set environment variables in Vercel dashboard
4. Deploy automatically on push

### Netlify

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Build
npm run build

# Deploy
netlify deploy --prod --dir=.next
```

### Traditional Server (Nginx)

1. Build the application: `npm run build`
2. Install production dependencies: `npm ci --production`
3. Configure Nginx as reverse proxy
4. Run with PM2: `pm2 start npm --name "frontend" -- start`

### Nginx Configuration

```nginx
server {
  listen 80;
  server_name example.com;

  location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }
}
```

## 🔧 Troubleshooting

### Port 3000 Already in Use

**Problem**: Address already in use

**Solution**:
```bash
# Use different port
npm run dev -- -p 3001

# Or find and kill process
# Windows:
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# macOS/Linux:
lsof -i :3000
kill -9 <PID>
```

### API Connection Failed

**Problem**: Cannot connect to backend API

**Solution**:
1. Check `.env.local` has correct `NEXT_PUBLIC_API_URL`
2. Verify backend is running on correct port
3. Check CORS settings on backend
4. Check network tab in browser DevTools

### Module Not Found

**Problem**: Import resolution errors

**Solution**:
```bash
# Clear cache and reinstall
rm -rf node_modules .next
npm install
npm run dev
```

### Build Fails

**Problem**: Build process errors

**Solution**:
```bash
# Clean and rebuild
npm run clean
npm run build

# Check for TypeScript errors
npx tsc --noEmit
```

### Styling Issues

**Problem**: Tailwind styles not applied

**Solution**:
1. Check `tailwind.config.js` content paths
2. Clear `.next` directory: `rm -rf .next`
3. Restart dev server: `npm run dev`

## 📝 Contributing

### Code Style

```typescript
// Use TypeScript with strict mode
// Follow ESLint rules
// Use Prettier for formatting
npm run lint
npm run format
```

### Git Workflow

```bash
# Create feature branch
git checkout -b feature/feature-name

# Make changes and commit
git add .
git commit -m "feat: Add new feature"

# Push and create pull request
git push origin feature/feature-name
```

### Component Structure

```typescript
// components/MyComponent.tsx
'use client'; // If using client-side features

import { FC, ReactNode } from 'react';

interface MyComponentProps {
  title: string;
  children: ReactNode;
  onAction?: () => void;
}

export const MyComponent: FC<MyComponentProps> = ({
  title,
  children,
  onAction,
}) => {
  return (
    <div className="my-component">
      <h2>{title}</h2>
      {children}
      {onAction && <button onClick={onAction}>Action</button>}
    </div>
  );
};

export default MyComponent;
```

## 📄 License

MIT License. See [LICENSE](../../LICENSE) for details.

## 📧 Support

For issues and questions:
- Open an issue on [GitHub](https://github.com/0SAKESH0/Digital-Disaster-Modeling)
- Check existing issues and discussions
- Contact the development team

## 🔗 Related Documentation

- [Backend README](../backend/README.md)
- [Main Project README](../../README.md)
- [Contributing Guide](../../CONTRIBUTING.md)
- [Next.js Documentation](https://nextjs.org/docs)
- [React Documentation](https://react.dev)


# Backend API - Digital Disaster Modeling

This is the FastAPI backend service for the Digital Disaster Modeling application. It provides REST API endpoints for blueprint processing, 3D model generation, disaster simulation (fire, flood, earthquake), damage prediction, and evacuation route calculation.

## 📋 Table of Contents

- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running the Backend](#running-the-backend)
- [API Documentation](#api-documentation)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Docker Setup](#docker-setup)
- [Blender Integration](#blender-integration)
- [Testing](#testing)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## 🛠️ Technology Stack

- **Framework**: FastAPI - Modern, fast web framework
- **Server**: Uvicorn - ASGI server
- **Language**: Python 3.10+
- **Database**: SQLite (configurable)
- **File Processing**: PIL, OpenCV
- **3D Model Processing**: Blender Python API (bpy)
- **Pathfinding**: NumPy, SciPy
- **Task Queue**: Celery (optional, for async tasks)

## 📦 Prerequisites

- **Python 3.10+**
- **Node.js 18+** (for frontend integration)
- **Blender 3.0+** (for 3D model processing)
- **Git** (for version control)
- **Docker & Docker Compose** (optional, for containerized deployment)

## 🚀 Setup

### 1. Install Python Dependencies

#### On Windows (PowerShell):

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

#### On macOS/Linux:

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 2. Environment Variables

Create a `.env` file in the backend directory:

```env
# Database
DATABASE_URL=sqlite:///./test.db

# Server
DEBUG=True
LOG_LEVEL=info
SECRET_KEY=your-secret-key-here

# Blender
BLENDER_PATH=/path/to/blender
BLENDER_SCRIPT_TIMEOUT=300

# File Upload
MAX_FILE_SIZE=50MB
UPLOAD_DIR=./uploads

# Simulation
SIMULATION_TIMEOUT=600
```

### 3. Database Setup

```bash
python -c "from api.database import init_db; init_db()"
```

## ▶️ Running the Backend

### Development Mode (with hot reload)

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Access the API at: `http://localhost:8000`

### Production Mode

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
```

### Using Gunicorn (Production)

```bash
gunicorn -w 4 -k uvicorn.workers.UvicornWorker main:app --bind 0.0.0.0:8000
```

## 📚 API Documentation

Once the server is running, access the interactive documentation:

- **Swagger UI**: `http://localhost:8000/docs`
- **ReDoc**: `http://localhost:8000/redoc`
- **OpenAPI Schema**: `http://localhost:8000/openapi.json`

## 📁 Project Structure

```
webapp/backend/
├── main.py                  # FastAPI application entry point
├── requirements.txt         # Python dependencies
├── .env                     # Environment variables (create locally)
├── README.md               # This file
│
├── api/                    # API route handlers
│   ├── __init__.py
│   ├── upload.py          # Blueprint upload endpoints
│   ├── convert.py         # 3D model conversion endpoints
│   ├── simulation.py      # Disaster simulation endpoints
│   ├── damage.py          # Damage prediction endpoints
│   └── evacuation.py      # Evacuation route endpoints
│
├── config/                # Configuration
│   ├── settings.py        # Application settings
│   └── database.py        # Database configuration
│
├── file/                  # File handling
│   ├── upload.py          # File upload handling
│   └── storage.py         # File storage management
│
├── process/               # Core processing logic
│   ├── blueprint.py       # Blueprint processing
│   ├── model_generator.py # 3D model generation
│   ├── simulator.py       # Disaster simulation
│   ├── damage_predictor.py# Damage prediction
│   └── pathfinder.py      # Evacuation pathfinding
│
├── swagger/               # Swagger/OpenAPI docs
│   └── paths.py          # API endpoint definitions
│
├── test/                 # Test suite
│   ├── test_api.py
│   ├── test_process.py
│   └── test_integration.py
│
└── utils/                # Utility functions
    ├── validators.py     # Input validation
    ├── helpers.py        # Helper functions
    └── logger.py         # Logging setup
```

## 🔌 API Endpoints

### Blueprint Processing

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/blueprints/upload` | Upload a blueprint image |
| `GET` | `/api/blueprints/{id}` | Get blueprint details |
| `GET` | `/api/blueprints` | List all blueprints |
| `DELETE` | `/api/blueprints/{id}` | Delete a blueprint |

### 3D Model Conversion

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/convert` | Convert blueprint to 3D model |
| `GET` | `/api/models/{id}` | Get model information |
| `GET` | `/api/models/{id}/download` | Download the 3D model (GLB/OBJ) |

### Disaster Simulation

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/simulate` | Start a disaster simulation |
| `GET` | `/api/simulations/{id}` | Get simulation results |
| `GET` | `/api/simulations/{id}/status` | Get simulation status |
| `POST` | `/api/simulations/{id}/cancel` | Cancel a running simulation |

Simulation types: `fire`, `flood`, `earthquake`

### Damage Prediction

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/damage/predict` | Predict damage severity |
| `GET` | `/api/damage/{id}` | Get damage prediction results |
| `GET` | `/api/damage/{id}/report` | Get detailed damage report |

### Evacuation Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/evacuation/generate` | Generate evacuation paths |
| `GET` | `/api/evacuation/{id}` | Get evacuation route data |
| `GET` | `/api/evacuation/{id}/export` | Export routes as JSON/GLB |

### Health & Status

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/health` | Health check endpoint |
| `GET` | `/api/status` | Server status information |

## 🐳 Docker Setup

### Build Docker Image

```bash
docker build -f Dockerfile.backend -t digital-disaster-backend:latest .
```

### Run with Docker Compose

```bash
docker-compose up -d
```

The backend will run on port 8000. Access it at `http://localhost:8000`

### Docker Compose Configuration

```yaml
services:
  backend:
    build:
      context: .
      dockerfile: Dockerfile.backend
    ports:
      - "8000:8000"
    volumes:
      - ./uploads:/app/uploads
      - ./models:/app/models
    environment:
      - DEBUG=False
      - DATABASE_URL=sqlite:///./test.db
    depends_on:
      - db
```

### Stop Containers

```bash
docker-compose down
```

## 🎨 Blender Integration

The backend uses the Blender Python API (bpy) for:

- **Model Processing**: Loading, modifying, and transforming 3D models
- **Evacuation Pathfinding**: Computing optimal escape routes
- **Model Export**: Exporting models to GLB, OBJ, and other formats
- **Damage Visualization**: Applying damage effects to 3D models

### Blender Configuration

1. **Install Blender**: Download from [blender.org](https://www.blender.org)
2. **Set Blender Path** in `.env`:
   ```env
   BLENDER_PATH=/path/to/blender
   ```
3. **Verify Installation**:
   ```bash
   blender --version
   ```

### Blender Script Examples

Scripts are located in `../../Blender/`:

- `blender_export_any.py` - Export models to various formats
- `blender_evacuate_path.py` - Generate evacuation paths
- `blender_simulate_disaster.py` - Run simulations

## 🧪 Testing

### Run All Tests

```bash
pytest test/ -v
```

### Run Specific Test File

```bash
pytest test/test_api.py -v
```

### Run with Coverage

```bash
pytest test/ --cov=. --cov-report=html
```

### Test Database

Tests use an in-memory SQLite database:

```python
# In test files
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker

SQLALCHEMY_DATABASE_URL = "sqlite:///:memory:"
engine = create_engine(SQLALCHEMY_DATABASE_URL, connect_args={"check_same_thread": False})
```

## 🔧 Troubleshooting

### ModuleNotFoundError

**Problem**: Missing Python dependencies

**Solution**:
```bash
pip install -r requirements.txt
```

### Port Already in Use

**Problem**: Port 8000 is already in use

**Solution**:
```bash
# Use a different port
uvicorn main:app --host 0.0.0.0 --port 8001 --reload

# Or find and kill the process using port 8000
# Windows:
netstat -ano | findstr :8000
taskkill /PID <PID> /F

# macOS/Linux:
lsof -i :8000
kill -9 <PID>
```

### Blender Not Found

**Problem**: Blender executable not found

**Solution**:
```bash
# Set Blender path in .env
BLENDER_PATH=C:\Program Files\Blender Foundation\Blender 3.6\blender.exe

# Or add to system PATH
# Windows: Add Blender bin directory to PATH
# macOS/Linux: export PATH="/path/to/blender:$PATH"
```

### Database Errors

**Problem**: Database locked or connection issues

**Solution**:
```bash
# Remove old database and reinitialize
rm test.db
python -c "from api.database import init_db; init_db()"
```

### CORS Issues

**Problem**: Cross-origin requests blocked

**Solution**: Update CORS settings in `main.py`:
```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000", "http://localhost:8080"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

## 📝 Contributing

1. **Code Style**: Follow PEP 8 guidelines
   ```bash
   pip install black flake8
   black .
   flake8 --max-line-length=88 .
   ```

2. **Type Hints**: Add type hints to all functions
   ```python
   def process_blueprint(file_path: str, model_type: str) -> Dict[str, Any]:
       pass
   ```

3. **Documentation**: Write docstrings using Google style
   ```python
   def function(arg1: str, arg2: int) -> bool:
       """Brief description.
       
       Longer description if needed.
       
       Args:
           arg1: Description of arg1
           arg2: Description of arg2
           
       Returns:
           Description of return value
       """
   ```

4. **Testing**: Add tests for new features
   ```bash
   pytest test/ -v
   ```

5. **Commit Messages**: Use clear, descriptive messages
   ```
   feat: Add evacuation route optimization algorithm
   fix: Resolve blueprint upload validation issue
   docs: Update API documentation
   ```

## 📄 License

MIT License. See [LICENSE](../../LICENSE) for details.

## 📧 Support

For issues and questions:
- Open an issue on [GitHub](https://github.com/0SAKESH0/Digital-Disaster-Modeling)
- Contact the development team

## 🔗 Related Documentation

- [Frontend README](../frontend/README.md)
- [Main Project README](../../README.md)
- [Contributing Guide](../../CONTRIBUTING.md)
