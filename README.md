# EdTech Fullstack Project

A complete, production-ready EdTech platform built with FastAPI backend, React frontend, and Docker deployment.

## Features

### Backend
- **FastAPI** with async support
- **SQLModel** for ORM with SQLite database
- **JWT Authentication** for secure user sessions
- **Courses, Lessons, Quizzes** management
- **Progress Tracking** for users
- **Seed Script** for sample data

### Frontend
- **React** with **Vite** for fast development
- **Tailwind CSS** for styling
- **Single-Page Application** with smooth navigation
- **Login** authentication
- **Course Listing** and browsing
- **Lesson Player** with content display
- **Quiz Interface** for assessments

### DevOps
- **Docker** containerization for both backend and frontend
- **Docker Compose** for local development
- **GitHub Actions** CI/CD workflow
- **Container Registry** push to GitHub Container Registry (GHCR)

## Project Structure

```
edtech-project/
├── backend/
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── app/
│   │   ├── main.py
│   │   ├── database.py
│   │   ├── models.py
│   │   ├── schemas.py
│   │   ├── auth.py
│   │   ├── routers/
│   │   │   ├── users.py
│   │   │   ├── courses.py
│   │   │   ├── lessons.py
│   │   │   └── quizzes.py
│   │   ├── seed.py
│   │   └── tests/
│   │       └── test_basic.py
│   └── docker-compose.override.yml
├── frontend/
│   ├── Dockerfile
│   ├── package.json
│   ├── vite.config.js
│   ├── index.html
│   └── src/
│       ├── main.jsx
│       ├── App.jsx
│       ├── api.js
│       ├── pages/
│       │   ├── Login.jsx
│       │   ├── Courses.jsx
│       │   ├── Course.jsx
│       │   ├── Lesson.jsx
│       │   └── Quiz.jsx
│       └── components/
│           └── Nav.jsx
├── docker-compose.yml
├── .gitignore
└── README.md
```

## Quick Start

### Prerequisites
- Docker and Docker Compose installed
- Git installed
- (Optional) GitHub CLI for direct repo creation

### Local Development

1. **Clone or setup the repository**
   ```bash
   git clone https://github.com/pokasatyapriya/edtech-fullstack-project.git
   cd edtech-fullstack-project
   ```

2. **Run with Docker Compose**
   ```bash
   docker-compose up --build
   ```

3. **Access the application**
   - Frontend: http://localhost:5173
   - API Documentation: http://localhost:8000/docs

### Default Credentials
- Email: `teacher@example.com`
- Password: `password`

## Deployment

### GitHub Actions CI/CD

The project includes a GitHub Actions workflow that:
1. Builds Docker images for both backend and frontend
2. Pushes images to GitHub Container Registry (GHCR)
3. Can be extended to deploy to cloud platforms (Render, Railway, etc.)

### Setup for Automated Deployment

1. **Create Personal Access Token (PAT)**
   - Go to GitHub Settings → Developer settings → Personal access tokens
   - Create a token with `write:packages` and `repo` scopes
   - Copy the token

2. **Add GitHub Secret**
   - Go to repository Settings → Secrets and variables → Actions
   - Add new secret: `CR_PAT` with your token value

3. **Push to trigger workflow**
   ```bash
   git push origin main
   ```

## API Endpoints

### Authentication
- `POST /users/register` - Register a new user
- `POST /users/token` - Login and get JWT token

### Courses
- `GET /courses/` - List all courses
- `GET /courses/{course_id}` - Get course details

### Lessons
- `GET /lessons/by_course/{course_id}` - Get lessons for a course
- `GET /lessons/{lesson_id}` - Get lesson details

### Quizzes
- `GET /quizzes/lesson/{lesson_id}` - Get quiz for a lesson

## Technology Stack

- **Backend Framework**: FastAPI
- **Database**: SQLite with SQLModel ORM
- **Authentication**: JWT (python-jose)
- **Password Hashing**: bcrypt
- **Frontend Framework**: React
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **Containerization**: Docker
- **Orchestration**: Docker Compose
- **CI/CD**: GitHub Actions

## Environment Variables

Backend environment variables can be set in `docker-compose.yml` or `.env` file:

```env
SECRET_KEY=your-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440
DATABASE_URL=sqlite:///./edtech.db
```

## Development

### Backend Development

```bash
cd backend
pip install -r requirements.txt
python -m uvicorn app.main:app --reload
```

### Frontend Development

```bash
cd frontend
npm install
npm run dev
```

## Testing

### Run Backend Tests

```bash
cd backend
pip install -r requirements.txt
pytest
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

MIT License - see LICENSE file for details

## Support

For issues and questions, please open an issue on GitHub.

---

**Built with ❤️ for EdTech enthusiasts**
