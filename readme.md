# Homework 9: QR Code API with CI/CD Pipeline

This project implements a QR Code generation API using FastAPI, paired with a CI/CD pipeline that ensures high code quality and security. The API allows authenticated users to generate, list, and delete QR codes.

## Features

- **QR Code Management:** 
  - Create, list, and delete QR codes.
  - Secure operations with OAuth2 authentication.
- **CI/CD Pipeline:** 
  - Automated testing, Docker image builds, and vulnerability scans.
  - Integrated with GitHub Actions for seamless deployment.

## Fixes and Improvements

During development, several issues were resolved to ensure a stable and functional pipeline:
0. **Spellchecks Fix throughout the repo:**
   - Fixed bugs related to spellings for multiple files in the repo.

1. **Authentication in Test Cases:**
   - Fixed `401 Unauthorized` errors by properly setting and loading `ADMIN_USER` and `ADMIN_PASSWORD` environment variables in both test and production environments.

2. **QR Code Conflict Handling:**
   - Implemented logic to return `409 Conflict` if a QR code already exists, ensuring the create endpoint is idempotent.

3. **Correct Docker Configuration:**
   - Updated Docker image tagging to use the correct Docker Hub username and included the `docker.io` prefix for proper publishing.

4. **Trivy Integration Fixes:**
   - Solved Trivy failures due to rate limiting by adding `TRIVY_GITHUB_TOKEN` and ensuring database download during scans completes smoothly.

5. **Vulnerability Resolutions:**
   - Addressed CVEs by updating dependencies:
     - Upgraded `python-jose` to `3.4.0` and downgraded `pyasn1` to `0.4.8` for compatibility.
     - Locked `starlette` to `0.40.0` to ensure FastAPI compatibility.

## Prerequisites

- Python 3.10 or higher
- Docker installed and configured
- Optional: Trivy for local image scanning

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd homework9
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create necessary directories:
   ```bash
   mkdir -p qr_codes
   ```

5. Run the app:
   ```bash
   docker compose up --build
   ```

6. Run tests:
   ```bash
   pytest
   ```

7. View API docs:
   Visit [http://localhost/docs](http://localhost/docs)

## Author

Venkata Saikumar Kethala
