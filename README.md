# Healthcare Management System API

A REST API for managing hospital operations built with FastAPI and MySQL, featuring role-based access control for Patients, Doctors, and Admins.

## How It Works
1. Register as a Patient or Doctor with full profile details
2. Login with role-based access - Patients, Doctors and Admins see different options
3. Patients can book and modify appointments
4. Doctors can view their appointments and patient details
5. Admins have full access to all records
6. All database operations use MySQL stored procedures for performance and security

## Tech Stack
- **Backend**: Python, FastAPI, Uvicorn
- **Database**: MySQL with Stored Procedures, Views, Triggers, Indexes
- **Validation**: Pydantic models
- **Auth**: Role-based access control (Patient, Doctor, Admin)
- **Security**: Environment variables for credentials, no hardcoded passwords

## API Endpoints
- `POST /register/patient` - Register a new patient
- `POST /register/doctor` - Register a new doctor
- `POST /login` - User authentication with role detection
- `POST /appointments` - Book an appointment (Patients only)
- `PUT /appointments/{id}` - Modify an appointment
- `GET /appointments` - View all appointments
- `GET /appointments/doctor/{name}` - Appointments by doctor
- `GET /patients/{name}/diagnosis` - Patient diagnosis details
- `GET /patients/{name}/history` - Full visit history
- `GET /patients/{name}/prescriptions` - Patient prescriptions

## Setup

```bash
pip install fastapi uvicorn mysql-connector-python python-dotenv

# Configure your database credentials in .env
DB_HOST=localhost
DB_NAME=your_database
DB_USER=root
DB_PASSWORD=your_password

# Run SQL files to set up stored procedures
# Then start the server
uvicorn main:app --reload
```

Visit `http://127.0.0.1:8000/docs` for interactive Swagger UI documentation.

## Database Features
- **Stored Procedures** - All CRUD operations via MySQL procedures
- **Views** - 5 pre-built views for appointments, diagnoses, prescriptions
- **Triggers** - Audit trail for all appointment changes
- **Indexes** - 10 optimized indexes for query performance

## Project Structure
```
healthcare-management-system/
├── main.py                  - FastAPI REST API
├── app_procedures.sql       - Appointment stored procedures
├── patient_procedures.sql   - Patient stored procedures
├── userprocedures.sql       - User auth and registration
├── views.sql                - Database views, triggers, indexes
└── README.md
```

## Current Limitations & Future Improvements
This is a basic version with core hospital management features. It can be significantly improved with:
- **JWT Authentication** - replace basic login with secure token-based auth
- **Password Hashing** - use bcrypt instead of plain text passwords
- **Appointment Scheduling** - calendar view with conflict detection
- **Billing System** - invoice generation and payment tracking
- **Medical Records** - upload and store patient documents and lab results
- **Email Notifications** - appointment reminders and confirmations
- **Frontend Dashboard** - React-based UI for patients and doctors
- **Real-time Updates** - WebSocket notifications for appointment changes
- **Cloud Deployment** - deploy on AWS RDS with auto-scaling
- **HIPAA Compliance** - encryption at rest and in transit for sensitive data