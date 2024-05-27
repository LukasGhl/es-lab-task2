



## Description
This repository contains the backend server for the Task Scheduling front-end. The backend is responsible for processing the logical model, running scheduling algorithms, and communicating with the frontend. It is built with FastAPI and provides a RESTful API for interaction with the [frontend](https://eslab2.pages.dev/).

## Table of Contents
- [Description](#description)
- [Technologies Used](#technologies-used)
- [Features](#features)
- [API Endpoints](#api-endpoints)
- [Input and Output Formats](#input-and-output-formats)
- [Running the Server](#running-the-server)
- [Components](#components)
- [Contributing](#contributing)


## Technologies Used
- Python 3
- FastAPI
- NetworkX (for graph processing)
- Uvicorn (ASGI server)
- CORS middleware for cross-origin requests

## Features
- **RESTful API**: Provides endpoints for scheduling tasks and retrieving schedules.
- **Multiple Scheduling Algorithms**: Implements LDF and EDF scheduling algorithms for task scheduling.
- **Input Validation**: Ensures valid data format for processing.
- **Configurable**: Backend server configuration can be adjusted through `config.json`.
- **Cross-Origin Resource Sharing (CORS)**: Enabled for specified origins.

## API Endpoints

- **POST /schedule_jobs**: Accepts a task graph in JSON format and returns the scheduled tasks using four different algorithms.
- **GET /get_jobs**: Endpoint for retrieving job schedules.
- **GET /**: Root endpoint to verify if the server is running.
- **GET /items/{item_id}**: Sample endpoint for retrieving item details.

## Input and Output Schemas for /schedule_jobs Endpoint

### Input Schema

The backend expects input in the following JSON format:

    ```json
    {
    "application": {
        "jobs": [
        {
            "id": <integer>,
            "wcet_fullspeed": <integer>,
            "mcet": <integer>,
            "deadline": <integer>
        },
        ...
        ],
        "messages": [
        {
            "id": <integer>,
            "sender": <integer>,
            "receiver": <integer>,
            "size": <integer>,
            "timetriggered": <boolean>
        },
        ...
        ]
    },
    "platform": {
        "nodes": [
        {
            "id": <integer>,
            "is_router": <boolean>
        },
        ...
        ],
        "links": [
        {
            "start": <integer>,
            "end": <integer>
        },
        ...
        ]
    }
    }
    ```

### Output Schema

The backend returns output in the following JSON format:
    ```json
    {
    "schedule1": [
        {
        "job_id": <integer>,
        "node_id": <integer>,
        "end_time": <integer>,
        "deadline": <integer>,
        "start_time": <integer>,
        "execution_time": <integer>
        },
        ...
    ],
    "schedule2": [
        {
        "job_id": <integer>,
        "node_id": <integer>,
        "end_time": <integer>,
        "deadline": <integer>,
        "start_time": <integer>,
        "execution_time": <integer>
        },
        ...
    ],
    "schedule3": [
        {
        "job_id": <integer>,
        "node_id": <integer>,
        "end_time": <integer>,
        "deadline": <integer>,
        "start_time": <integer>,
        "execution_time": <integer>
        },
        ...
    ],
    "schedule4": [
        {
        "job_id": <integer>,
        "node_id": <integer>,
        "end_time": <integer>,
        "deadline": <integer>,
        "start_time": <integer>,
        "execution_time": <integer>
        },
        ...
    ]
    }
    ```
    
## Running the Server

1. Clone the repository:
    git clone https://github.com/linem-davton/graphdraw-eslab-backend.git

2. Navigate to the project directory:
    cd graphdraw-eslab-backend

3. Install dependencies:
    pip install -r requirements.txt


4. Start the development server:
  python src/backend.py

5. Access the API:
   The backend server starts at http://localhost:8000.
  Verfiy the server is running by visiting http://localhost:8000 in a web browser, and you should see a message "{"Hello":"World"}".

## Components

- **backend.py**: Main entry point for the FastAPI backend server.
    - Handles API endpoints and routing.
    - Configures CORS middleware.
- **algorithms.py**: Contains the implementation of the scheduling algorithms (LDF, EDF).
    - ldf_algorithm: Implementation of the LDF scheduling algorithm.
    - edf_schedule: Implementation of the EDF scheduling algorithm.
    - ldf_singlecore: Implementation of the single-core LDF scheduling algorithm.
    - edf_singlecore: Implementation of the single-core EDF scheduling algorithm.
- **config.json**: Configuration file for backend settings.
- **requirements.txt**: File listing all the dependencies required for the project.

## Contributing
Contributions are welcome! Please follow these steps to contribute:

- Fork the repository.
- Create a new branch (git checkout -b feature/your-feature-name).
- Make your changes.
- Commit your changes (git commit -m 'Add some feature').
- Push to the branch (git push origin feature/your-feature-name).
- Create a new Pull Request.
