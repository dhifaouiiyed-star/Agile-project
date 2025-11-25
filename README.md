# Vulnerability Scanner API

This project implements a web-based vulnerability scanner using FastAPI. It allows users to initiate port scans and basic vulnerability checks against specified targets. The scan results provide information about open ports and potential vulnerabilities.

## Features

- **Port Scanning:** Scans for open ports on a target host.
- **Vulnerability Detection:** Identifies common vulnerabilities based on open ports.
- **Asynchronous Scans:** Scans run in the background, allowing for non-blocking API responses.
- **Scan Types:** Supports Quick, Standard, and Comprehensive scan types with varying port ranges.
- **RESTful API:** Provides clear endpoints for initiating scans and retrieving results.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Make sure you have Python 3.8+ and `pip` installed.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/Agile-project.git
   cd Agile-project
   ```

2. Create a virtual environment and activate it (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Application

To start the FastAPI server, run:
   ```bash
   uvicorn scan_server:app --host 0.0.0.0 --port 8000
   ```

The API will be accessible at `http://0.0.0.0:8000`.

## API Endpoints

### Initiate a Scan

- **POST** `/scan`
  - **Description:** Starts a new vulnerability scan.
  - **Request Body (JSON):**
    ```json
    {
      "target": "example.com",
      "scanType": "quick"  // or "standard", "comprehensive"
    }
    ```
  - **Response (JSON):** Returns the initial `Scan` object.

### Get Scan Status and Results

- **GET** `/scan/{scan_id}`
  - **Description:** Retrieves the status and results of a specific scan.
  - **Parameters:**
    - `scan_id` (path): The unique ID of the scan.
  - **Response (JSON):** Returns the `Scan` object with updated status, open ports, and vulnerabilities.

### Health Check

- **GET** `/health`
  - **Description:** Checks if the API is running.
  - **Response (JSON):** `{"status": "healthy"}`

### Root Endpoint

- **GET** `/`
  - **Description:** A simple welcome message.
  - **Response (JSON):** `{"message": "Our Agile-Project server is running"}`

## Project Structure

- `scan_server.py`: The main FastAPI application, containing API endpoints and scanning logic.
- `requirements.txt`: Lists all Python dependencies.
- `Dockerfile`: Used for containerizing the application.
- `ressources/wordlist.txt`: A wordlist resource (though not actively used in the current version of the scanner).

