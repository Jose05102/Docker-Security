
# Docker_security

## Overview

The "Docker_security" project aims to establish a robust Docker environment for an application known as "todo-app." This setup is specifically designed to run with a non-root user inside the Docker containers. Utilizing a non-root user is a fundamental security best practice, as it helps mitigate the risks associated with containerized applications by preventing potential attackers from gaining excessive privileges. This security measure is crucial because even if an attacker manages to exploit vulnerabilities within the container, their ability to perform malicious activities is significantly constrained.

## Project Goals

- **Enhanced Security:** By configuring the application to run with a non-root user, we adhere to security best practices that limit the impact of potential security breaches.
- **Reduced Privileges:** Running processes with minimal privileges reduces the risk of unauthorized access and damage.
- **Improved Container Management:** Ensuring proper setup and configuration of Docker containers enhances the overall stability and security of the application.

## Configuration Instructions

### 1. Modifying the `.env` File

To begin, you need to configure the environment variables for the Docker containers. Follow these steps:

1. Locate the `.env` file in the root directory of your project.
2. Find the `MY_user` variable in the `.env` file.
3. Change the value of `MY_user` to the desired username that you want to use inside the Docker container. For instance, if you choose `myuser`, update the variable accordingly:

   ```env
   MY_user=myuser
   ```

### 2. Updating Configuration in `src/persistence/sqlite.js`

Next, you need to ensure that the SQLite configuration aligns with the username specified in the `.env` file:

1. Open the `sqlite.js` file, which is located in the `src/persistence/` directory.
2. Locate the line that specifies the file path for SQLite, which is typically found around line 3:

   ```javascript
   const dbPath = '/home/myuser/app/todos/todo.db';
   ```

3. Update the file path to reflect the username you set in the `.env` file. If you used `newuser` as the username, the updated path should be:

   ```javascript
   const dbPath = '/home/newuser/app/todos/todo.db';
   ```

## Building and Running the Docker Containers

With your configurations in place, you can now build and deploy the Docker containers. Use the following command:

```bash
docker-compose up --build
```

This command will:

- **Build the Docker Image:** Follow the instructions defined in the `Dockerfile` to create the Docker image.
- **Start the Containers:** Deploy the containers as specified in the `docker-compose.yml` file.

## Accessing the Application

After the Docker containers are up and running, you can access the "todo-app" application through your web browser. Navigate to the following URL:

[http://localhost:3000](http://localhost:3000)

This URL will take you to the "todo-app" application, which is now operational within the Docker containers you have configured.

## Additional Considerations

- **Verify Configurations:** Ensure that all file paths and environment variables are correctly configured to prevent any issues during the container setup.
- **Keep Docker Updated:** Regularly update Docker and Docker Compose to leverage the latest features and security updates.
- **Implement Further Security Measures:** Consider additional security practices such as network segmentation and container scanning. These measures can enhance the protection of your application and infrastructure, ensuring a secure and reliable environment.

## Best Practices for Docker Security

To maximize security, adhere to the following best practices:

- **Run Containers with Least Privilege:** Always use a non-root user for running applications inside containers.
- **Regularly Update Images:** Keep your Docker images up to date to incorporate security patches and improvements.
- **Limit Container Capabilities:** Use Docker's security options to restrict the capabilities and resources of containers.

By following these practices, you ensure that your containerized application remains secure, efficient, and resilient against potential threats.
```

Este `README.md` incluye una explicación más detallada sobre la configuración, la construcción, y la seguridad de los contenedores Docker, además de sugerencias para mantener la aplicación segura y actualizada.
