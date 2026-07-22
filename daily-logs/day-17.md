# Daily Learning Log

**Date:** 22/07/26

## Topic

Docker Fundamentals: Dockerfiles

## Objectives

- Understand the purpose of a Dockerfile.
- Learn the relationship between Dockerfiles, images, and containers.
- Create and build a custom Docker image.
- Understand how Docker rebuilds images from Dockerfiles.

## Activities Performed

- Reviewed the purpose of Dockerfiles and why they are used to automate image creation.
- Learned that a Dockerfile acts as a set of instructions (recipe) for building Docker images.
- Created a `Dockerfile` using Nano without a file extension.
- Explored the core Dockerfile instructions:
  - `FROM`
  - `RUN`
  - `CMD`
- Learned how `FROM` specifies the base image.
- Learned how `RUN` executes commands during the image build process.
- Learned how `CMD` defines the default command executed when a container starts.
- Built a custom Docker image using `docker build`.
- Discussed the concept of the Docker build context and the purpose of the `.` in the build command.
- Learned that Dockerfiles are not directly connected to containers; instead, they are used to build images.
- Understood that containers are created from images, not directly from Dockerfiles.
- Learned that updating a Dockerfile requires rebuilding the image before changes appear in new containers.
- Explored how a single Docker image can be reused to create multiple containers.
- Discussed real-world DevOps workflows where Dockerfiles are stored in Git repositories to ensure consistent application environments.

## Commands Practiced

```bash
nano Dockerfile
cat Dockerfile
ls
docker build -t dev-env .
docker run -it dev-env
```

## Key Learning Points

- A Dockerfile is a reusable set of instructions used to build Docker images.
- Docker follows the workflow: **Dockerfile → Image → Container**.
- Images are reusable and can create multiple containers.
- Containers do not automatically update when a Dockerfile changes.
- Rebuilding an image is required after modifying a Dockerfile.
- Dockerfiles improve consistency and reproducibility across different development environments.

## Reflection

Today's session helped me understand how Docker images are created instead of only using existing ones. I now understand the relationship between Dockerfiles, images, and containers, and why rebuilding an image is necessary after making changes to a Dockerfile.

## Summary

Successfully learned the fundamentals of Dockerfiles, including creating a Dockerfile, understanding its core instructions, building custom Docker images, and understanding the complete Docker workflow from Dockerfile to image to container. This knowledge provides the foundation for building and deploying custom containerized applications.