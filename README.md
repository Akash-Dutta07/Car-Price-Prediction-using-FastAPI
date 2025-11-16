# Car Price Prediction API

A production-ready FastAPI application for predicting car prices using machine learning, featuring JWT authentication, Redis caching, and comprehensive monitoring.

## Features

- 🚀 **FastAPI Framework** - High-performance async API
- 🔐 **JWT Authentication** - Secure API access with token-based auth
- 💾 **Redis Caching** - Fast response times with intelligent caching
- 📊 **Machine Learning** - Trained model for accurate car price predictions
- 🐳 **Docker Support** - Containerized deployment with Docker Compose
- 📈 **Prometheus Monitoring** - Built-in metrics and observability
- 🔒 **Security** - API key and JWT-based security layers
- 📝 **Logging Middleware** - Comprehensive request/response logging

## Project Structure

```
app/
├── api/              # API route handlers
│   ├── routes_auth.py      # Authentication endpoints
│   └── routes_predict.py   # Prediction endpoints
├── cache/            # Redis caching layer
├── core/             # Core configuration and security
├── middleware/       # Custom middleware (logging)
├── models/           # Trained ML model
└── services/         # Business logic (model inference)
data/                 # Training dataset
notebooks/            # Jupyter notebooks for exploration
training/             # Model training scripts
```

## Prerequisites

- Python 3.8+
- Redis
- Docker & Docker Compose (optional)

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd project-fastapi
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   
   Copy `.env` and update values:
   ```env
   API_KEY=your-api-key
   JWT_SECRET_KEY=your-secret-key
   REDIS_URL=redis://localhost:6379
   ```

## Running the Application

### Local Development

```bash
# Start Redis
redis-server

# Run the application
uvicorn app.main:app --reload
```

The API will be available at `http://localhost:8000`

### Docker Deployment

```bash
# Build and run with Docker Compose
docker-compose up --build
```

Services:
- API: `http://localhost:8000`
- Prometheus: `http://localhost:9090`

## API Documentation

Interactive API documentation is available at:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

### Authentication Flow

1. **Get Access Token**
   ```bash
   POST /auth/token
   Headers: X-API-Key: demo-key
   ```

2. **Make Predictions**
   ```bash
   POST /predict
   Headers: Authorization: Bearer <token>
   Body: {
     "feature1": value1,
     "feature2": value2,
     ...
   }
   ```

## Model Training

To retrain the model with new data:

```bash
python training/train_model.py
```

The trained model will be saved to `app/models/model.joblib`.

See `training/train_model.py` for training configuration and `training/train_utils.py` for utility functions.

## Configuration

Key configuration files:
- `app/core/config.py` - Application settings
- `app/core/security.py` - Security utilities
- `docker-compose.yml` - Docker services configuration
- `prometheus.yml` - Metrics collection config

## Deployment

### Render.com

The project includes a `render.yaml` configuration for one-click deployment to Render.

### Docker

```bash
# Build image
docker build -t car-price-api .

# Run container
docker run -p 8000:8000 --env-file .env car-price-api
```

## Monitoring

Prometheus metrics are exposed at `/metrics` endpoint. Configure `prometheus.yml` to scrape metrics.

## Development

### Project Components

- **Routes**: `routes_auth.py` and `routes_predict.py`
- **Caching**: `redis_cache.py`
- **Model Service**: `model_service.py`
- **Middleware**: `logging_middleware.py`
- **Exceptions**: `exceptions.py`

### Adding New Features

1. Define routes in `app/api`
2. Implement business logic in `app/services`
3. Update dependencies in `requirements.txt`
4. Add tests and documentation

## Dataset

Training data is stored in `data/car-details.csv`. Jupyter notebooks for data exploration are available in the `notebooks` directory.

## License

[Add your license here]

## Contributing

[Add contribution guidelines here]

## Support

For issues and questions, please open an issue in the repository.
