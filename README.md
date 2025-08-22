# IAA Feedback System

A comprehensive feedback management system built for Indian Aviation Academy (IAA) using FastAPI, React, and PostgreSQL.

![IAA Logo](frontend/public/images/iaa-logo.png)

## 🌐 Live Demo
- **Frontend**: https://iaa-feedback.vercel.app/
- **Backend**: https://iaa-2bs1.onrender.com/

## 🌟 Features

- **Multi-Role Support**: Different interfaces for Admins, Trainers, and Trainees
- **Dynamic Form Builder**: Create customizable feedback forms
- **Real-time Analytics**: Instant feedback analysis and reporting
- **Department Management**: Organize users by departments
- **Automated Reports**: Generate PDF reports with insights
- **Mobile Responsive**: Works seamlessly on all devices
- **Multi-language Support**: Built-in internationalization
- **Secure Authentication**: JWT-based auth with role management

## 🏗️ Architecture

The project follows a modern microservices architecture:

- **Frontend**: React + Vite
- **Backend**: FastAPI (Python)
- **Database**: PostgreSQL (Supabase)
- **File Storage**: Local/Cloud (configurable)
- **Deployment**: Vercel (Frontend) + Render (Backend)

## 🚀 Quick Start

### Prerequisites

- Node.js 16+
- Python 3.9+
- PostgreSQL 13+
- Git

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/iaa-feedback-system.git
   cd iaa-feedback-system
   ```

2. **Backend Setup**
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows: .\venv\Scripts\activate
   pip install -r requirements.txt
   
   # Create .env file
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Frontend Setup**
   ```bash
   cd frontend
   npm install
   
   # Create .env file
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Start Development Servers**

   Backend:
   ```bash
   cd backend
   uvicorn working_backend:app --reload
   ```

   Frontend:
   ```bash
   cd frontend
   npm run dev
   ```

## 🔧 Configuration

### Backend Environment Variables (.env)

```env
# Database Configuration
DATABASE_URL=postgresql://user:password@host:port/dbname
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=your_db_host
DB_PORT=5432
DB_NAME=your_db_name

# JWT Configuration
JWT_SECRET=your-secret-key
JWT_ALGORITHM=HS256
JWT_ACCESS_TOKEN_EXPIRE_MINUTES=30
JWT_REFRESH_TOKEN_EXPIRE_DAYS=7

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USERNAME=your-email@gmail.com
SMTP_PASSWORD=your-app-password
FROM_EMAIL=noreply@iaa.edu.in
FROM_NAME=IAA Feedback System

# Application Configuration
APP_NAME=IAA Feedback System
APP_VERSION=1.0.0
DEBUG=False
ENVIRONMENT=production
```

### Frontend Environment Variables (.env)

```env
VITE_API_BASE_URL=http://localhost:8000
VITE_APP_NAME=IAA Feedback System
VITE_DEFAULT_LANGUAGE=en
```

## 🌐 Deployment Guides

### Vercel Deployment (Frontend)

1. **Prepare Your Frontend**
   ```bash
   cd frontend
   npm run build
   ```

2. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

3. **Deploy to Vercel**
   ```bash
   vercel login
   vercel
   ```

4. **Configure Environment Variables**
   - Go to Vercel Dashboard
   - Select your project
   - Navigate to Settings > Environment Variables
   - Add all required environment variables

5. **Configure Build Settings**
   - Build Command: \`npm run build\`
   - Output Directory: \`dist\`
   - Install Command: \`npm install\`

### Render Deployment (Backend)

1. **Create a Render Account**
   - Sign up at render.com
   - Connect your GitHub repository

2. **Create a New Web Service**
   - Choose your repository
   - Select the backend directory
   - Choose Python environment

3. **Configure Build Settings**
   ```bash
   # Build Command
   pip install -r requirements.txt

   # Start Command
   uvicorn working_backend:app --host 0.0.0.0 --port $PORT
   ```

4. **Set Environment Variables**
   - Add all environment variables from your .env file
   - Make sure to update DATABASE_URL for production

5. **Deploy**
   - Click "Create Web Service"
   - Wait for deployment to complete

### AWS Deployment Guide

1. **Set Up AWS Environment**
   - Create an AWS account
   - Install AWS CLI
   - Configure AWS credentials

2. **Create an Elastic Beanstalk Application**
   ```bash
   # Initialize EB CLI
   eb init -p python-3.8 iaa-feedback-system

   # Create environment
   eb create iaa-feedback-prod

   # Deploy
   eb deploy
   ```

3. **Configure RDS Database**
   - Create PostgreSQL RDS instance
   - Update security groups
   - Configure DATABASE_URL in environment variables

4. **Set Up S3 for Static Files**
   - Create S3 bucket
   - Configure CORS
   - Update frontend configuration

### Azure Deployment Guide

1. **Prepare Azure Environment**
   ```bash
   # Install Azure CLI
   az login
   az group create --name iaa-feedback --location eastus
   ```

2. **Deploy Database**
   ```bash
   az postgres flexible-server create \
     --name iaa-feedback-db \
     --resource-group iaa-feedback
   ```

3. **Deploy Backend**
   ```bash
   # Create App Service
   az webapp up --runtime PYTHON:3.9 --sku B1
   ```

4. **Configure Environment**
   - Set environment variables in App Service
   - Configure connection strings

### Google Cloud Platform (GCP) Deployment

1. **Set Up GCP Project**
   ```bash
   # Install Google Cloud SDK
   gcloud init
   gcloud app create
   ```

2. **Deploy to App Engine**
   ```bash
   # Create app.yaml
   gcloud app deploy
   ```

3. **Set Up Cloud SQL**
   - Create PostgreSQL instance
   - Configure connection
   - Update environment variables

## 📦 Project Structure

```
iaa-feedback-system/
├── backend/
│   ├── working_backend.py
│   ├── requirements.txt
│   └── ... (other backend files)
├── frontend/
│   ├── src/
│   ├── public/
│   └── ... (other frontend files)
├── documentation/
│   └── ... (documentation files)
└── README.md
```

## 🔒 Security Considerations

1. **Environment Variables**
   - Never commit .env files
   - Use strong, unique passwords
   - Rotate secrets regularly

2. **Database Security**
   - Use connection pooling
   - Implement proper backups
   - Regular security updates

3. **API Security**
   - CORS configuration
   - Rate limiting
   - Input validation

## 🧪 Testing

### Backend Tests
```bash
cd backend
pytest
```

### Frontend Tests
```bash
cd frontend
npm test
```

## 📈 Performance Optimization

1. **Backend Optimizations**
   - Database query optimization
   - Caching strategies
   - Async operations

2. **Frontend Optimizations**
   - Code splitting
   - Lazy loading
   - Image optimization

## 🔄 Continuous Integration/Deployment

- GitHub Actions workflows
- Automated testing
- Deployment pipelines

## 🆘 Troubleshooting

### Common Issues

1. **Database Connection Issues**
   - Check DATABASE_URL format
   - Verify network connectivity
   - Check firewall settings

2. **CORS Errors**
   - Verify ALLOWED_ORIGINS in backend
   - Check API_BASE_URL in frontend
   - Clear browser cache

3. **Authentication Issues**
   - Verify JWT configuration
   - Check token expiration
   - Clear local storage

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📞 Support

For support, email support@iaa.edu.in or create an issue in the repository.

## 🙏 Acknowledgements

- Indian Aviation Academy for the opportunity
- All contributors and testers
- Open source community

---

Made with ❤️ for Indian Aviation Academy

