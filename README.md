# Cricket Scoring API - FastAPI Backend

A comprehensive, production-ready FastAPI backend for cricket scoring and management with real-time features, complete test coverage, and modern Python practices.

## 🎯 Project Status

✅ **Production Ready** - All 280 tests passing  
✅ **Complete Test Coverage** - Unit, integration, and API tests  
✅ **Modern Python** - Pydantic V2, Python 3.13+ compatible  
✅ **Security Hardened** - JWT auth, CORS, rate limiting, audit logging  
✅ **Real-time Features** - WebSocket support for live scoring  
✅ **Comprehensive API** - 60+ endpoints with full documentation  

## 🚀 Features

### Core Functionality
- **🏏 Live Cricket Scoring**: Real-time match updates with ball-by-ball tracking
- **👥 User Management**: Multi-role authentication (11 roles) with granular permissions
- **🏆 Team Management**: Complete team lifecycle with player statistics
- **🏟️ Tournament Management**: Tournament creation, scheduling, and results tracking
- **📍 Venue Management**: Location-based venue tracking and management
- **📊 Analytics & Reports**: Advanced statistics, performance metrics, and PDF reports
- **🔔 Notification System**: Real-time push notifications and email alerts
- **📁 File Management**: Secure file upload, processing, and storage system
- **🔍 Search & Dashboard**: Global search functionality with comprehensive analytics
- **📝 Audit Logging**: Complete user action tracking and security monitoring

### Technical Excellence
- **🔐 Security**: JWT Authentication, CORS, Rate Limiting, Input Validation
- **🗄️ Database**: PostgreSQL with SQLAlchemy ORM and Alembic migrations
- **⚡ Real-time**: WebSocket gateway for live updates and notifications
- **🏗️ Architecture**: Clean modular design with separation of concerns
- **🧪 Testing**: 280 comprehensive tests (unit, integration, API)
- **📚 Documentation**: Auto-generated OpenAPI/Swagger documentation
- **🐳 Docker**: Containerized deployment ready
- **📈 Monitoring**: Built-in logging, health checks, and performance metrics

## 👥 User Roles & Access Rights

### Role Hierarchy (11 Roles)
1. **SUPER_ADMIN** - Full system administration and user management
2. **APP_ADMIN** - Application-level administration and configuration
3. **LEAGUE_OWNER** - League-specific administration and tournament management
4. **TEAM_OWNER** - Team-specific management and player administration
5. **UMPIRE** - Live match scoring and real-time updates
6. **THIRD_UMPIRE** - Video review decisions and match oversight
7. **TEAM_CAPTAIN** - Team strategy management and player coordination
8. **VICE_CAPTAIN** - Team support functions and backup management
9. **PLAYER** - Personal statistics and match participation
10. **SPONSOR** - Team analytics access and performance insights
11. **TOURNAMENT_SPONSOR** - Tournament analytics and sponsorship data

## 🛠️ Quick Start

### Prerequisites
- **Python**: 3.8+ (tested with 3.13.5)
- **PostgreSQL**: 12+ 
- **Redis**: 6+ (optional, for caching and sessions)

### Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd cricket-api
   ```

2. **Create virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

5. **Set up database:**
   ```bash
   # Create PostgreSQL database
   createdb cricket_scoring
   
   # Run migrations
   alembic upgrade head
   ```

6. **Run the application:**
   ```bash
   uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```

### Running Tests

```bash
# Run all tests (280 tests)
pytest

# Run with coverage
pytest --cov=app --cov-report=html

# Run specific test categories
pytest tests/unit/          # Unit tests
pytest tests/integration/   # Integration tests
pytest tests/test_api_endpoints.py  # API endpoint tests
```

## 📊 Test Results

### Current Status: ✅ All Tests Passing
- **Total Tests**: 280
- **Unit Tests**: 109 (service layer)
- **Integration Tests**: 81 (API endpoints)
- **API Tests**: 60 (endpoint validation)
- **Type Tests**: 17 (data consistency)
- **Auth Tests**: 7 (authentication)
- **Manual Tests**: 6 (manual verification)

### Test Categories
- ✅ **Authentication & Authorization**
- ✅ **Team Management**
- ✅ **Player Management**  
- ✅ **Match Management**
- ✅ **Scoring & Live Updates**
- ✅ **Analytics & Statistics**
- ✅ **File Uploads**
- ✅ **Notifications**
- ✅ **Reports & Auditing**
- ✅ **Search Functionality**
- ✅ **Dashboard & Statistics**
- ✅ **Error Handling**
- ✅ **Data Validation**
- ✅ **Type Consistency**

## 🏗️ Architecture

### Project Structure
```
cricket-api/
├── app/
│   ├── api/v1/           # API endpoints (REST)
│   ├── api/websockets/   # WebSocket endpoints
│   ├── core/             # Configuration and settings
│   ├── db/               # Database models and connections
│   ├── models/           # SQLAlchemy models
│   ├── schemas/          # Pydantic schemas
│   ├── services/         # Business logic layer
│   └── utils/            # Utilities and helpers
├── tests/
│   ├── unit/             # Unit tests
│   ├── integration/      # Integration tests
│   └── conftest.py       # Test configuration
├── docs/                 # Documentation
├── uploads/              # File uploads
└── main.py              # Application entry point
```

### Technology Stack
- **Framework**: FastAPI 0.104.1
- **Database**: PostgreSQL with SQLAlchemy
- **Authentication**: JWT with python-jose
- **Validation**: Pydantic V2
- **Testing**: pytest with 100% coverage
- **Documentation**: Auto-generated OpenAPI/Swagger
- **Real-time**: WebSocket support
- **Security**: CORS, rate limiting, audit logging

## 🔧 Configuration

### Environment Variables
```bash
# Database
DATABASE_URL=postgresql://user:password@localhost/cricket_scoring

# Security
SECRET_KEY=your-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# Email (optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASSWORD=your-app-password

# File Upload
UPLOAD_DIR=uploads
MAX_FILE_SIZE=10485760  # 10MB

# Redis (optional)
REDIS_URL=redis://localhost:6379
```

## 🚀 Deployment

### Development
```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

### Production with Gunicorn
```bash
gunicorn main:app -w 4 -k uvicorn.workers.UvicornWorker --bind 0.0.0.0:8000
```

### Docker Deployment
```bash
# Build image
docker build -t cricket-api .

# Run container
docker run -p 8000:8000 cricket-api
```

### Docker Compose
```bash
docker-compose up -d
```

## 📚 API Documentation

### Interactive Documentation
- **Swagger UI**: `http://localhost:8000/docs`
- **ReDoc**: `http://localhost:8000/redoc`
- **OpenAPI JSON**: `http://localhost:8000/openapi.json`

### API Endpoints Overview
- **Authentication**: `/api/v1/auth/*`
- **Teams**: `/api/v1/teams/*`
- **Players**: `/api/v1/players/*`
- **Matches**: `/api/v1/matches/*`
- **Scoring**: `/api/v1/scoring/*`
- **Analytics**: `/api/v1/analytics/*`
- **Files**: `/api/v1/files/*`
- **Search**: `/api/v1/search/*`
- **Dashboard**: `/api/v1/dashboard/*`

## 🔐 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Role-based Access Control**: 11 different user roles with granular permissions
- **CORS Protection**: Configurable cross-origin resource sharing
- **Rate Limiting**: Protection against abuse and DDoS
- **Input Validation**: Comprehensive data validation with Pydantic
- **Audit Logging**: Complete user action tracking
- **SQL Injection Protection**: Parameterized queries with SQLAlchemy
- **File Upload Security**: Secure file handling with size and type validation

## 📈 Performance Features

- **Async/Await**: Non-blocking I/O operations
- **Database Connection Pooling**: Optimized database connections
- **Caching Support**: Redis integration for performance
- **Compression**: Gzip compression for responses
- **Health Checks**: Built-in health monitoring
- **Metrics**: Request timing and performance tracking

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines
- Follow PEP 8 style guidelines
- Write comprehensive tests for new features
- Update documentation for API changes
- Ensure all tests pass before submitting PR

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: Check the `/docs` directory for detailed API documentation
- **Issues**: Report bugs and feature requests via GitHub Issues
- **Discussions**: Use GitHub Discussions for questions and ideas

## 🎉 Acknowledgments

- FastAPI team for the excellent framework
- SQLAlchemy for robust database ORM
- Pydantic for data validation
- The Python community for amazing tools and libraries

---

**Built with ❤️ by Geek Tech Sol**
