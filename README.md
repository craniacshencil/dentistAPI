# Dentist API

The Dentist API is a robust backend system for a dental clinic, built with Django. It provides a comprehensive set of functionalities to manage various aspects of clinic operations.

[![Python Version](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/release/python-312/)
[![Django Version](https://img.shields.io/badge/django-5.1.5-green.svg)](https://www.djangoproject.com/)

## Features

- **User Roles and Permissions:** Differentiates between patient, dentist, and admin roles with appropriate access controls.
- **Secure Authentication:** Implements JWT for token-based authentication and bcrypt for password hashing.
- **Comprehensive Patient Data:** Stores detailed patient information, including medical history and personal details.
- **Clinical Workflow Management:** Manages patient complaints, diagnoses, treatments, and follow-up appointments.
- **Prescription Generation:** Allows dentists to prescribe medications and treatments with dosage and duration.
- **PDF Prescription Generation:** Creates downloadable PDF prescriptions for patients.
- **WhatsApp Integration:** Includes basic setup for sending WhatsApp messages via an API.
- **Background Task Processing:** Utilizes Celery for asynchronous task execution (e.g., sending WhatsApp messages).

## Tech Stack

- **Backend Framework:** Django
- **Database:** PostgreSQL
- **API:** Django REST framework
- **Authentication:** JWT (PyJWT), bcrypt
- **Task Queue:** Celery, django-celery-beat
- **ORM:** Django ORM
- **Libraries:** python-dotenv, psycopg2-binary, django-filter, markdown, django-cors-headers, django-extensions, requests, reportlab
- **Languages:** Python

## Setup

- Check out `SETUP.md`

## API Reference 🔍

This API follows RESTful principles. Key endpoints include:

- **Authentication (`/auth/`)**
  - `POST /auth/signup/`: Patient signup.
  - `POST /auth/login/`: Patient login.
  - `POST /auth/password/`: Password reset/reprompt.
  - `POST /auth/phonenumber/`: Change phonenumber.

- **Patient (`/p/`)**
  - `GET /p/details/`: Get logged-in patient's details.
  - `POST /p/details/`: Admin/Dentist register a new patient.
  - `GET /p/medical_details/`: Get logged-in patient's medical details.
  - `POST /p/medical_details/`: Admin/Dentist add/update patient's medical details.
  - `GET /p/complaints/`: Get today's complaints (for dashboard).
  - `POST /p/complaints/`: Register a new complaint.
  - `GET /p/diagnosis/<complaint_id>/`: Get diagnoses for a complaint.
  - `POST /p/diagnosis/`: Add a new diagnosis.
  - `PUT /p/diagnosis/`: Update an existing diagnosis.
  - `DELETE /p/diagnosis/delete/<id>/`: Delete a diagnosis.
  - `GET /p/followup/`: Get today's followups.
  - `GET /p/followup/<complaint_id>/`: Get all followups for a complaint.
  - `GET /p/followup/<date>/`: Get followups for a specific date.
  - `POST /p/followup/`: Add a new followup.
  - `PUT /p/followup/`: Update a followup.
  - `DELETE /p/followup/delete/<followup_id>/`: Delete a followup.
  - `GET /p/prescription/<complaint_id>/<sitting>/`: Get prescriptions for a sitting.
  - `POST /p/prescription/`: Add a patient prescription.
  - `PUT /p/prescription/`: Update a patient prescription.
  - `DELETE /p/prescription/delete/<patient_prescription_id>/`: Delete a patient prescription.
  - `GET /p/prescription/pdf/<complaint_id>/<sitting>/`: Generate PDF prescription.
  - `GET /p/bill/discount/<complaint_id>/`: Get discount for a complaint.
  - `POST /p/bill/discount/`: Add/update discount.
  - `POST /p/bill/consultation/`: Add consultation charge.
  - `GET /p/history/<patient_id>/`: Get patient's history (by admin/dentist).
  - `GET /p/history/`: Get logged-in patient's history.
  - `GET /p/<phonenumber>/`: Search patients by phonenumber.
  - `GET /p/<name>/`: Search patients by name.
  - `GET /p/<phonenumber>/<name>/`: Search patients by phonenumber and name.

- **Doctor (`/doc/`)**
  - `GET /doc/treatment/`: Get all treatments.
  - `POST /doc/treatment/`: Add a new treatment.
  - `PUT /doc/treatment/<uuid:treatment_id>/`: Update a treatment.
  - `DELETE /doc/treatment/<uuid:treatment_id>/`: Delete a treatment.
  - `GET /doc/prescription/`: Get structured prescriptions.
  - `POST /doc/prescription/`: Add a new prescription.
  - `PUT /doc/prescription/<uuid:prescription_id>/`: Update a prescription.
  - `DELETE /doc/prescription/<uuid:prescription_id>/`: Delete a prescription.
