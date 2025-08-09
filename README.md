# Dockerized Flask App

A simple Flask application containerized with Docker for easy deployment and development.

## Features

- Flask web application with REST API endpoints
- Docker containerization with multi-stage build
- Health check endpoint
- Production-ready with Gunicorn
- Docker Compose for easy management

## API Endpoints

- `GET /` - Welcome message
- `GET /health` - Health check endpoint
- `GET /api/hello?name=<name>` - Hello endpoint with optional name parameter

## Quick Start

### Using Docker Compose (Recommended)

1. **Build and run the application:**
   ```bash
   docker-compose up --build
   ```

2. **Run in background:**
   ```bash
   docker-compose up -d
   ```

3. **Stop the application:**
   ```bash
   docker-compose down
   ```

### Using Docker directly

1. **Build the Docker image:**
   ```bash
   docker build -t flask-app .
   ```

2. **Run the container:**
   ```bash
   docker run -p 5000:5000 flask-app
   ```

3. **Run in background:**
   ```bash
   docker run -d -p 5000:5000 --name flask-container flask-app
   ```

## Development

### Local Development (without Docker)

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the application:**
   ```bash
   python main.py
   ```

### Testing the API

Once the application is running, you can test the endpoints:

```bash
# Test the home endpoint
curl http://localhost:5000/

# Test the health endpoint
curl http://localhost:5000/health

# Test the hello endpoint
curl http://localhost:5000/api/hello?name=YourName
```

## Docker Configuration

### Dockerfile Features

- **Multi-stage build** for optimized image size
- **Non-root user** for security
- **Health checks** for container monitoring
- **Production-ready** with Gunicorn
- **Environment variables** for configuration

### Docker Compose Features

- **Volume mounting** for logs
- **Health checks** with proper intervals
- **Restart policy** for reliability
- **Port mapping** for easy access

## Project Structure

```
.
├── main.py              # Flask application
├── requirements.txt     # Python dependencies
├── Dockerfile          # Docker configuration
├── docker-compose.yml  # Docker Compose configuration
├── .dockerignore       # Files to exclude from Docker build
└── README.md          # This file
```

## Environment Variables

- `FLASK_ENV`: Set to 'production' for production deployment
- `PORT`: Port number (default: 5000)
- `FLASK_APP`: Flask application file (default: main.py)

## Troubleshooting

### Common Issues

1. **Port already in use:**
   ```bash
   # Check what's using port 5000
   netstat -tulpn | grep :5000
   # Or change the port in docker-compose.yml
   ```

2. **Permission issues:**
   ```bash
   # Make sure Docker has proper permissions
   sudo usermod -aG docker $USER
   ```

3. **Build failures:**
   ```bash
   # Clean Docker cache
   docker system prune -a
   ```

## Production Deployment

For production deployment, consider:

1. **Using a reverse proxy** (nginx) in front of the Flask app
2. **Setting up SSL/TLS** certificates
3. **Configuring proper logging**
4. **Setting up monitoring** and alerting
5. **Using environment-specific configurations**

## License

This project is open source and available under the MIT License.


