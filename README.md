# Django Project with Docker

This is a simple Django project named `core` that runs inside a Docker container. The project serves an `index.html` page after successful execution.

## Prerequisites

Ensure you have the following installed:
- Docker
- Python 3.10 (for local development, if needed)

## Project Structure
```
core/
│   Dockerfile
│   manage.py
│   requirements.txt
│   index.html
│   ... (other Django project files)
```

## Docker Setup

### Build the Docker Image
Run the following command to build the Docker image:
```sh
docker build --tag python-django .
```

### Run the Docker Container
Run the container and expose port 8000:
```sh
docker run --publish 8000:8000 python-django
```

## Dockerfile
```dockerfile
FROM python:3.10-slim-buster

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

## Accessing the Application
Once the container is running, access the application at:
```
http://localhost:8000/
```

## Stopping the Container
To stop the running container, find its container ID using:
```sh
docker ps
```
Then stop it using:
```sh
docker stop <container_id>
```

## Notes
- No Django app has been created in this project.
- The `index.html` page is routed manually.
- Ensure the `requirements.txt` file contains the necessary dependencies (such as `Django`).
- Modify the `CMD` command if using additional Django settings or a different host/port.

## Future Improvements
- Create Django apps for better structuring.
- Use environment variables for configurations.
- Add database support (PostgreSQL, MySQL, etc.).


