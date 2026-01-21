# Pregnancy Health Monitoring App

A comprehensive web application for maternal and fetal health monitoring, featuring user authentication, health assessments, and AI-powered predictions using machine learning.

## Features

### Frontend (Static Web App)
- **Patient Dashboard**: Health monitoring, kick counter, nutrition tracking, exercise guidance
- **Doctor Portal**: Patient management, health assessments
- **Health Monitoring**: Fetal development tracking, mental health support
- **Emergency Access**: Quick access to emergency resources
- **Responsive Design**: Dark/light theme toggle

### Backend (Node.js/Express)
- **Authentication**: JWT-based login/registration for patients and doctors
- **API Endpoints**:
  - `/api/auth`: User authentication
  - `/api/patient`: Patient profiles and assessments
  - `/api/doctor`: Doctor profiles and patient management
- **Database**: MongoDB for user data and health records
- **Security**: CORS, cookie-based auth, password hashing

### Machine Learning Service (Python/Flask)
- **Fetal Health Prediction**: Gaussian Naive Bayes model for fetal health classification
- **Maternal Risk Assessment**: Custom decision tree model for maternal health risk prediction
- **Real-time Predictions**: REST API for health assessments

## Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Node.js, Express.js, MongoDB, Mongoose
- **ML Service**: Python, Flask, scikit-learn, pandas
- **Deployment**:
  - Frontend: Vercel (static hosting)
  - Backend: Render (Node.js web service)
  - ML Service: Render (Python/Docker web service)
- **Authentication**: JWT, bcrypt
- **Styling**: Custom CSS with theme support

## Project Structure

```
pregnancy_app/
├── public/                    # Static frontend files
│   ├── index.html            # Home page
│   ├── patient.html          # Patient dashboard
│   ├── doctor.html           # Doctor portal
│   ├── health-monitoring.html
│   ├── fetal-development.html
│   ├── nutrition.html
│   ├── exercise.html
│   ├── mental-health.html
│   ├── kick-counter.html
│   ├── emergency-access.html
│   ├── styles.css            # Main stylesheet
│   └── theme.js              # Theme management
├── server/                   # Backend application
│   ├── src/
│   │   ├── index.js          # Main server file
│   │   ├── middleware/
│   │   │   └── auth.js       # Authentication middleware
│   │   ├── models/           # MongoDB models
│   │   │   ├── User.js
│   │   │   ├── PatientProfile.js
│   │   │   ├── DoctorProfile.js
│   │   │   └── QuestionnaireResponse.js
│   │   └── routes/           # API routes
│   │       ├── auth.js
│   │       ├── patient.js
│   │       └── doctor.js
│   ├── ml_service/           # ML prediction service
│   │   ├── app.py            # Flask application
│   │   ├── requirements.txt
│   │   ├── Dockerfile
│   │   ├── Procfile
│   │   └── ML/               # ML models and data
│   │       ├── fetal/
│   │       │   ├── fetal_health.csv
│   │       │   └── gaussian_naive_final.py
│   │       └── mother/
│   │           ├── Maternal Health Risk Data Set.csv
│   │           └── custom_trees.py
│   ├── public/               # Static files (copy)
│   ├── package.json
│   ├── Dockerfile
│   └── Procfile
├── ML/                       # ML source files (copy)
├── vercel.json               # Vercel deployment config
├── package.json              # Root package config
└── README.md
```

## Prerequisites

- Node.js (v16+)
- Python (v3.8+)
- MongoDB (local or cloud instance)
- Git

## Local Development Setup

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/pregnancy-app.git
cd pregnancy-app
```

### 2. Backend Setup
```bash
cd server
npm install
```

Create a `.env` file in `server/`:
```
MONGO_URI=mongodb://localhost:27017/pregnancy_app
JWT_SECRET=your_jwt_secret_here
ML_SERVICE_URL=http://localhost:5001
PORT=5000
```

Start the backend:
```bash
npm run dev  # For development with nodemon
# or
npm start    # For production
```

### 3. ML Service Setup
```bash
cd server/ml_service
pip install -r requirements.txt
python app.py
```

The ML service runs on `http://localhost:5001`

### 4. Frontend Setup
The frontend is static and served from the `public/` folder. For local development:

- Use a local server like Live Server in VS Code
- Or serve with Python: `python -m http.server 3000` from the root directory
- Access at `http://localhost:3000`

## API Documentation

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login

### Patient Routes
- `GET /api/patient/profile` - Get patient profile
- `PUT /api/patient/profile` - Update patient profile
- `POST /api/patient/maternal-assessment` - Submit maternal health assessment
- `GET /api/patient/questionnaire-responses` - Get questionnaire history

### Doctor Routes
- `GET /api/doctor/patients` - Get assigned patients
- `GET /api/doctor/patient/:id` - Get specific patient details
- `POST /api/doctor/assessment` - Submit doctor assessment

### ML Service
- `POST /api/predict/fetal` - Fetal health prediction
- `POST /api/predict/maternal` - Maternal risk prediction

## Deployment

### Frontend (Vercel)
1. Connect GitHub repo to Vercel
2. Deploy automatically (static files from `public/`)
3. URL: `https://your-app.vercel.app`

### Backend (Render)
1. Create Web Service on Render
2. Root Directory: `server`
3. Runtime: Node.js
4. Environment Variables:
   - `MONGO_URI`
   - `JWT_SECRET`
   - `ML_SERVICE_URL` (set after ML deployment)
5. URL: `https://your-backend.onrender.com`

### ML Service (Render)
1. Create Web Service on Render
2. Root Directory: `server/ml_service`
3. Runtime: Docker or Python
4. URL: `https://your-ml.onrender.com`

## Environment Variables

### Backend (.env)
```
MONGO_URI=mongodb://localhost:27017/pregnancy_app
JWT_SECRET=your_secure_jwt_secret
ML_SERVICE_URL=http://localhost:5001
PORT=5000
```

### ML Service
No environment variables required for local development.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support or questions, please open an issue on GitHub.

## Acknowledgments

- Fetal health dataset from Kaggle
- Maternal health risk dataset from UCI Machine Learning Repository
- Icons and design inspiration from various open-source projects
