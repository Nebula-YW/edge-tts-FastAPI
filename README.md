# FastAPI Vercel Template

A production-ready FastAPI template optimized for deployment on Vercel with serverless functions.

## ✨ Features

- **FastAPI** - Modern, fast web framework for building APIs
- **Vercel Ready** - Optimized for Vercel serverless deployment
- **Auto Documentation** - Interactive API docs with Swagger UI
- **CORS Support** - Cross-origin resource sharing configured
- **Environment Variables** - Dotenv support for configuration
- **Pydantic Models** - Data validation and serialization
- **Structured Logging** - Built-in logging configuration
- **Testing Setup** - Pytest configuration included
- **Type Hints** - Full type annotations throughout
- **UV Package Manager** - Fast Python package manager with lock file support

## 🚀 Quick Start

### Local Development

1. **Clone and install dependencies:**
```bash
git clone <your-repo>
cd fastapi-vercel-template
uv sync
```

2. **Run the development server:**
```bash
uv run uvicorn api.main:app --reload --port 3000
```

3. **Visit your API:**
- API: http://localhost:3000
- Interactive docs: http://localhost:3000/api/v1/docs
- ReDoc: http://localhost:3000/api/v1/redoc

### Deploy to Vercel

1. **Push to GitHub** and connect to Vercel
2. **Deploy** - Vercel will automatically detect the FastAPI app
3. **Environment Variables** - Add any required env vars in Vercel dashboard

## 📁 Project Structure

```
fastapi-vercel-template/
├── api/
│   ├── __init__.py
│   ├── main.py          # FastAPI app initialization
│   ├── routers.py       # API route definitions
│   └── schemas.py       # Pydantic models
├── tests/
│   ├── conftest.py      # Test configuration
│   └── test_all.py      # Test cases
├── .env.example         # Example environment variables
├── .gitignore          # Git ignore file
├── vercel.json          # Vercel configuration
├── requirements.txt     # Python dependencies (for Vercel)
├── pyproject.toml       # Project configuration with UV dependencies
├── uv.lock             # UV lock file
└── README.md
```

## 🔗 API Endpoints

### Core Endpoints
- `GET /` - Root endpoint with API information
- `GET /api/v1/health` - Health check endpoint
- `POST /api/v1/echo` - Echo endpoint for testing

### Items API (CRUD Example)
- `GET /api/v1/items` - List all items (with pagination)
- `POST /api/v1/items` - Create a new item
- `GET /api/v1/items/{item_id}` - Get item by ID
- `PUT /api/v1/items/{item_id}` - Update item by ID
- `DELETE /api/v1/items/{item_id}` - Delete item by ID

### Users API
- `GET /api/v1/users` - List all users (with pagination)
- `POST /api/v1/users` - Create a new user
- `GET /api/v1/users/{user_id}` - Get user by ID

## 📊 Example Usage

### Create an Item
```bash
curl -X POST "http://localhost:3000/api/v1/items" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Example Item",
    "description": "This is an example item",
    "price": 29.99,
    "tax": 2.99
  }'
```

### Echo Test
```bash
curl -X POST "http://localhost:3000/api/v1/echo" \
  -H "Content-Type: application/json" \
  -d '{"message": "Hello, FastAPI!"}'
```

### Health Check
```bash
curl "http://localhost:3000/api/v1/health"
```

## 🧪 Testing

Run tests with pytest:
```bash
uv run pytest tests/
```

Run with coverage:
```bash
uv run pytest tests/ --cov=api
```

Run specific test file:
```bash
uv run pytest tests/test_all.py -v
```

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in the root directory (copy from `.env.example`):
```bash
cp .env.example .env
```

Edit the `.env` file with your configuration:
```env
# Optional environment variables
API_TITLE="FastAPI Vercel Template"
API_VERSION="1.0.0"
DEBUG=false
```

### CORS Configuration

Update CORS settings in `api/main.py`:
```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=["https://yourdomain.com"],  # Specify domains in production
    allow_credentials=True,
    allow_methods=["GET", "POST"],
    allow_headers=["*"],
)
```

## 🔧 Customization

### Adding New Endpoints

1. **Define Pydantic models** in `api/schemas.py`
2. **Add route handlers** in `api/routers.py`
3. **Update tests** in `tests/test_all.py`

### Database Integration

To add database support:
1. Add your preferred database library to `pyproject.toml` (e.g., `sqlalchemy`, `databases`)
2. Run `uv sync` to install dependencies
3. Create database models and connection logic
4. Update the dependency injection in your routes

### Authentication

To add authentication:
1. Add `python-jose` and `passlib` to `pyproject.toml`
2. Run `uv sync` to install dependencies
3. Create authentication middleware
4. Add protected routes with dependencies

### Adding New Dependencies

To add new packages:
```bash
uv add package-name
```

To add development dependencies:
```bash
uv add --dev package-name
```

## 📈 Production Considerations

- **Environment Variables**: Use Vercel's environment variable system
- **CORS**: Configure appropriate origins for production
- **Rate Limiting**: Consider adding rate limiting middleware
- **Monitoring**: Add logging and monitoring solutions
- **Database**: Use a production database instead of in-memory storage
- **Dependencies**: Vercel uses `requirements.txt` for deployment, while development uses `uv.lock`

## 🛠️ UV Package Manager

This template uses [UV](https://github.com/astral-sh/uv) as the package manager for faster dependency resolution and installation.

### Key UV Commands

- `uv sync` - Install dependencies from lock file
- `uv add package-name` - Add a new dependency
- `uv add --dev package-name` - Add a development dependency
- `uv remove package-name` - Remove a dependency
- `uv run command` - Run a command in the project environment
- `uv lock` - Update the lock file

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.