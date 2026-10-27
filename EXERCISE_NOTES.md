# CI/CD In-Class Docker Exercises

## Exercise 1.1 — Build and Inspect

**Commands completed:**

- `docker build -t python-example-project .`
- `docker images python-example-project`
- `docker history python-example-project`

**Results:**

I successfully built the Docker image using the Python 3.12 slim base image. Docker displayed the completed image and its history. The image showed approximately 200 MB of disk usage.
Most of the image's size comes from the Python base image and installed dependencies. The application itself adds relatively little.
The Dockerfile uses `WORKDIR` to set the working directory, `COPY` to add application files, `RUN` to install Flask, `EXPOSE` to document port 8000, and `CMD` to start the application.
The `.dockerignore` file prevents unnecessary files, such as local virtual environments, from being included in the build context.

## Exercise 1.2 — Run, Reach, and Stop

**Commands completed:**

- `docker run`
- `docker ps`
- `curl.exe`
- `docker logs`
- `docker stop`
- `docker rm`

**Results:**

I successfully started the application in a Docker container and accessed it using localhost:8000. The application returned HTTP 200 OK.

I inspected the container logs and confirmed that the Flask application was running.

After stopping and removing the original container, I restarted the application using the port mapping `8080:8000`. The application again returned HTTP 200 OK.

The left side of the port mapping represents the port on my computer, while the right side represents the port inside the container.

I also tested the application's login endpoint and received an authentication cookie.

**Authentication test results:**

- Without cookie: [Enter your HTTP status code]
- With cookie: [Enter your HTTP status code]

Running the container with `-d` allowed it to run in the background. Running it without `-d` kept the terminal attached to the application's output.

## Exercise 1.3 — Inspect Inside the Container

**Commands completed:**

- `docker exec app whoami`
- `docker exec app ls -la /usr/src/app`
- `docker exec app pip list`
- `docker exec -it app sh`

**Results:**
I inspected the running container and checked its user and application files.
The application was configured to run from `/usr/src/app`.

The Docker image installs Flask and its runtime dependencies. Keeping unnecessary testing tools out of a production image can reduce its size and complexity.
Running an application as root can increase security risks because a compromised application could have more permissions inside the container than necessary.
I also opened an interactive shell inside the container and used Linux commands to inspect its environment.

## Conclusion

These exercises helped me understand:
-Docker packages an application
-How port mappings working
-How to start and stop containers
-How to inspect a container's environment
I also practiced testing HTTP responses and authentication using PowerShell.