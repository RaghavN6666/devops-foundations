# Daily Learning Log

**Date:** 23/07/26

## Topic

Dockerfile Mastery

## Objectives

- Understand advanced Dockerfile instructions.
- Learn how Docker builds images efficiently using layers and cache.
- Understand the purpose of `.dockerignore`.
- Build and run a custom Docker image using a Python application.

## Activities Performed

- Reviewed the purpose of Dockerfiles and their role in building reusable Docker images.
- Learned the `COPY` instruction and how it copies files from the host machine into a Docker image during the build process.
- Explored the `WORKDIR` instruction and understood how it sets the default working directory for all subsequent Dockerfile instructions.
- Learned how the `ENV` instruction is used to define environment variables inside a Docker image and container.
- Studied the `EXPOSE` instruction and understood that it documents the port an application listens on but does not publish the port to the host.
- Learned the difference between `CMD` and `ENTRYPOINT`, including when each instruction should be used.
- Explored the purpose of `.dockerignore` and how it prevents unnecessary files from being included in the Docker build context, resulting in faster builds and smaller images.
- Learned how Docker creates image layers for each Dockerfile instruction and how these layers contribute to efficient image management.
- Understood Docker's build cache mechanism and how unchanged layers are reused to significantly reduce build times.
- Created a Python application and Dockerfile using `FROM`, `WORKDIR`, `COPY`, `ENV`, and `CMD`.
- Built a custom Docker image using `docker build`.
- Successfully ran the container and verified the application output.

## Commands Practiced

```bash
mkdir docker-mastery
cd docker-mastery

nano app.py
nano Dockerfile

docker build -t docker-mastery .
docker run docker-mastery
```

## Key Learning Points

- `COPY` transfers files from the host system into the Docker image.
- `WORKDIR` sets the default directory for subsequent instructions and when the container starts.
- `ENV` defines environment variables that applications can access at runtime.
- `EXPOSE` documents the port an application uses but does not expose it externally without port mapping.
- `ENTRYPOINT` defines the main executable for a container, while `CMD` provides the default command or arguments.
- `.dockerignore` excludes unnecessary files from the Docker build context, improving build performance and reducing image size.
- Docker builds images in layers, allowing unchanged layers to be reused during subsequent builds.
- Docker's build cache improves efficiency by rebuilding only the layers affected by changes.

## Reflection

Today's session helped me understand how professional Dockerfiles are structured and why each instruction exists. I also learned how Docker optimizes image creation using layers and caching, which makes the build process much more efficient.

## Summary

Successfully completed Dockerfile Mastery by learning advanced Dockerfile instructions, understanding image layers and build caching, and building a custom Docker image that executed a Python application successfully. This session strengthened my understanding of how Docker images are built and prepared me for containerizing a real-world application in the next session.