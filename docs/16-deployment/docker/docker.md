---
title: Docker
parent: Deployment
has_children: true
nav_order: 1
---

# Docker
**Docker** is an open source platform that “provides the ability to package and run an
application in a loosely isolated environment called a container”

The **Docker server** contains the Docker daemon, a background process responsible for creating and managing Docker
objects like images, containers, volumes, and networks. The machine where the
Docker server runs is called the Docker host. Each machine where you want to run con-
tainers should be a Docker host, so it should have a Docker daemon running. The
portability of containers is made possible by the daemon process itself.

The **Docker daemon** exposes an API you can use to send instructions, such as to
run a container or create a volume. The Docker client talks to the daemon through that
API. The client is command-line based and can be used to interact with the Docker
daemon either through scripting (for example, Docker Compose) or through the
Docker CLI directly.

Next figure shows how the Docker client, Docker server,and container registry interact.
![The Docker Engine has a client/server architecture, and it interacts with a registry.](image.png)

A **container image** (or, simply, an image) is a lightweight executable package that
includes everything needed to run the application inside. The Docker image format is
the most used one for creating container images, and it has been standardized by the
OCI project (in the OCI Image Specification). OCI images can be created from
scratch by defining instructions in a Dockerfile, a text-based file containing all the
steps to generate the image. 

Container images follow common naming conventions, which are adopted by OCI-
compliant container registries: <container_registry>/<namespace>/<name>[:<tag>]:
* Container registry—The hostname for the container registry where the image is
stored. When using Docker Hub, the hostname is docker.io and it’s usually
omitted. The Docker Engine will implicitly prepend the image name with
docker.io if you don’t specify a registry. When using GitHub Container Regis-
try, the hostname is ghcr.io and must be explicit.
* Namespace—When using Docker Hub or GitHub Container Registry, the name-
space will be your Docker/GitHub username written all in lowercase. In other
registries, it might be the path to the repository.
* Name and tag—The image name represents the repository (or package) that con-
tains all the versions of your image. It’s optionally followed by a tag for selecting
a specific version. If no tag is defined, the latest tag will be used by default.

Official images like ubuntu or postgresql can be downloaded by specifying the name
only, which is implicitly converted to fully qualified names like docker.io/library/
ubuntu or docker.io/library/postgres.
 When uploading your images to GitHub Container Registry, you are required
to use fully qualified names, according to the ghcr.io/<your_github_username>/
<image_name> format.

A **container** is a runnable instance of a container image. You can manage the con-
tainer life cycle from the Docker CLI or Docker Compose: you can start, stop, update,
and delete containers. Containers are defined by the image on which they are based
and the configuration provided at startup time (for example, environment variables
used to customize the container). By default, containers are isolated from each other
and the host machine, but you can make them expose services to the outside world
through specific ports with a process called port forwarding or port mapping. Containers
can have any name. If you don’t specify one, the Docker server will assign a random
one, like bazinga_schrodinger. 