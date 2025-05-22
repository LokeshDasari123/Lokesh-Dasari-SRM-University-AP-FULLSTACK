# Todo Summary Assistant

A full-stack application that allows users to manage todos and automatically summarize them using AI, then send the summary to Slack.

## Features

- ✅ Create, edit, and delete todos
- 🤖 AI-powered todo summarization using Google Gemini
- 📢 Automatic Slack integration for sharing summaries
- 💾 PostgreSQL database storage
- 🎨 Clean, responsive React frontend

## Tech Stack

**Frontend:**
- React 18
- Axios for API calls
- Modern CSS with responsive design

**Backend:**
- Spring Boot 3.2
- Spring Data JPA
- PostgreSQL
- Google Gemini API integration
- Slack Webhooks

## Prerequisites

Before running this application, make sure you have:

- Java 17 or higher
- Node.js 16 or higher
- PostgreSQL database
- Google Gemini API key
- Slack workspace with webhook configured

## Setup Instructions

### 1. Database Setup

**Option A: Local PostgreSQL**
```bash
# Install PostgreSQL and create database
createdb todoapp
```

**Option B: Supabase (Recommended)**
1. Go to [supabase.com](https://supabase.com)
2. Create a new project
3. Get your database URL from Settings > Database
4. Update your connection string accordingly

### 2. Google Gemini API Setup

1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Copy the API key for your environment variables

### 3. Slack Webhook Setup

1. Go to your Slack workspace
2. Navigate to [api.slack.com/apps](https://api.slack.com/apps)
3. Click "Create New App" → "From scratch"
4. Name your app and select your workspace
5. Go to "Incoming Webhooks" and activate it
6. Click "Add New Webhook to Workspace"
7. Select the channel where you want summaries posted
8. Copy the webhook URL

### 4. Backend Configuration

1. **Clone and navigate to backend directory**
   ```bash
   cd backend
   ```

2. **Create environment file**
   ```bash
   cp .env.example .env
   ```

3. **Update `.env` file with your values:**
   ```bash
   DB_USERNAME=your_db_username
   DB_PASSWORD=your_db_password
   GEMINI_API_KEY=your_gemini_api_key
   SLACK_WEBHOOK_URL=your_slack_webhook_url
   ```

4. **Install dependencies and run**
   ```bash
   ./mvnw clean install
   ./mvnw spring-boot:run
   ```

   Backend will run on `http://localhost:8080`

### 5. Frontend Configuration

1. **Navigate to frontend directory**
   ```bash
   cd frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm start
   ```

   Frontend will run on `http://localhost:3000`

## Project Structure

```
todo-summary-assistant/
├── backend/
│   ├── src/main/java/com/todoapp/backend/
│   │   ├── controller/
│   │   │   ├── TodoController.java
│   │   │   └── SummaryController.java
│   │   ├── model/
│   │   │   └── Todo.java
│   │   ├── repository/
│   │   │   └── TodoRepository.java
│   │   ├── service/
│   │   │   └── TodoService.java
│   │   └── BackendApplication.java
│   ├── src/main/resources/
│   │   └── application.yml
│   ├── pom.xml
│   └── .env
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── TodoForm.jsx
│   │   │   ├── TodoList.jsx
│   │   │   └── SummaryButton.jsx
│   │   ├── api.js
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── index.js
│   ├── package.json
│   └── public/
└── README.md
```

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/todos` | Get all todos |
| POST | `/api/todos` | Create new todo |
| PUT | `/api/todos/{id}` | Update todo |
| DELETE | `/api/todos/{id}` | Delete todo |
| POST | `/api/summarize` | Generate summary and send to Slack |

## Usage

1. **Add Todos**: Use the form to add new todos with title and description
2. **Edit Todos**: Click the edit button to modify existing todos
3. **Delete Todos**: Use the delete button to remove todos
4. **Generate Summary**: Click "Summarize & Send to Slack" to:
   - Generate an AI summary of pending todos
   - Automatically post to your configured Slack channel

## Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `DB_USERNAME` | Database username | `postgres` |
| `DB_PASSWORD` | Database password | `your_password` |
| `GEMINI_API_KEY` | Google Gemini API key | `AIza...` |
| `SLACK_WEBHOOK_URL` | Slack webhook URL | `https://hooks.slack.com/...` |

## Deployment

### Frontend (Vercel/Netlify)
1. Build the project: `npm run build`
2. Deploy the `build` folder to your hosting platform
3. Update API URLs in production

### Backend (Railway/Heroku)
1. Create a production database
2. Set environment variables in your hosting platform
3. Deploy the Spring Boot application

## Troubleshooting

**Common Issues:**

1. **Database Connection Error**
   - Verify PostgreSQL is running
   - Check database credentials
   - Ensure database exists

2. **Gemini API Error**
   - Verify API key is correct
   - Check API quotas
   - Ensure proper formatting in requests

3. **Slack Integration Not Working**
   - Verify webhook URL is correct
   - Check channel permissions
   - Test webhook manually

4. **CORS Issues**
   - Ensure backend `@CrossOrigin` annotation includes frontend URL
   - Check if both servers are running

## Architecture Decisions

**Backend Framework**: Spring Boot was chosen for its robust ecosystem, built-in security features, and excellent database integration.

**Database**: PostgreSQL provides reliability and ACID compliance, perfect for todo management.

**LLM Integration**: Google Gemini offers a generous free tier and excellent text summarization capabilities.

**Frontend**: React provides component-based architecture and excellent user experience.

**Communication**: RESTful APIs ensure clear separation of concerns and easy testing.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes  
4. Test thoroughly
5. Submit a pull request

## License

This project is for educational purposes as part of a full-stack internship assignment.