# Backend API

This is the FastAPI backend service for the Digital Disaster Modeling application. It handles blueprint processing, 3D model generation, disaster simulation, damage prediction, and evacuation route calculation.

## Technology Stack

- **Framework**: FastAPI
- **Server**: Uvicorn
- **Language**: Python 3.10+

## Prerequisites

- Python 3.10+
- Node.js 18+ (for frontend integration)
- Blender (for model processing)

## Setup

### 1. Install Python Dependencies

```bash
python -m venv venv
# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate

pip install -r requirements.txt
```

### 2. Environment Variables

Create a `.env` file in the backend directory:

```env
DATABASE_URL=sqlite:///./test.db
DEBUG=True
LOG_LEVEL=info
```

## Running the Backend

### Development Mode

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

The API will be available at: `http://localhost:8000`

### Production Mode

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

## API Documentation

Once the server is running, access the interactive API documentation at:

- **Swagger UI**: `http://localhost:8000/docs`
- **ReDoc**: `http://localhost:8000/redoc`

## Project Structure

```
backend/
├── main.py              # FastAPI application entry point
├── api/                 # API route handlers
├── config/              # Configuration files
├── file/                # File handling utilities
├── flask/               # Flask-related utilities (if applicable)
├── process/             # Core processing logic
├── swagger/             # Swagger/OpenAPI documentation
├── test/                # Test files
└── requirements.txt     # Python dependencies
```

## Key Endpoints

### Blueprint Processing
- `POST /api/upload` - Upload blueprint image
- `POST /api/convert` - Convert blueprint to 3D model

### Simulation
- `POST /api/simulate` - Run disaster simulation
- `GET /api/simulation/{id}` - Get simulation results

### Damage Prediction
- `POST /api/predict-damage` - Predict damage severity
- `GET /api/damage/{id}` - Get damage prediction results

### Evacuation Routes
- `POST /api/generate-evacuation` - Generate evacuation paths
- `GET /api/evacuation/{id}` - Get evacuation route data

## Docker Setup

### Build Docker Image

```bash
docker build -f Dockerfile.backend -t digital-disaster-backend .
```

### Run with Docker Compose

```bash
docker-compose up
```

The backend will run on port 8000 inside the container.

## Integration with Blender

The backend uses Python Blender API (bpy) for:
- Model processing and transformation
- Evacuation pathfinding
- Model export (glb, obj, etc.)

Ensure Blender is installed and accessible in your system PATH.

## Testing

Run tests with:

```bash
pytest test/
```

## Troubleshooting

### ModuleNotFoundError

Ensure you've activated the virtual environment and installed all dependencies:

```bash
pip install -r requirements.txt
```

### Port Already in Use

If port 8000 is busy, use a different port:

```bash
uvicorn main:app --host 0.0.0.0 --port 8001 --reload
```

### Blender Not Found

Configure the Blender path in your environment or system PATH.

## Contributing

- Write clean, documented code
- Follow PEP 8 style guidelines
- Add tests for new features
- Update API documentation

## License

MIT License. See LICENSE for details.
