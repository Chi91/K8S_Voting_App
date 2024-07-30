# Voting App K8S

A simple distributed application running across multiple Docker containers.
This project involves migrating an existing voting application to Kubernetes. The Kubernetes setup includes deployments and services for PostgreSQL, Redis, Voting, and Worker components.

## Prerequisites

- [Kubernetes](https://kubernetes.io/docs/setup/) cluster set up and accessible
- [kubectl](https://kubernetes.io/docs/tasks/tools/) command-line tool installed and configured to interact with the Kubernetes cluster
- An existing voting application that includes components for PostgreSQL, Redis, Voting, and Worker
- Docker images for the Voting and Worker services, available in a container registry
- Kubernetes manifests (YAML files) for deploying and managing the PostgreSQL, Redis, Voting, and Worker services

## Architecture

![Architecture diagram](architecture.excalidraw.png)

* A front-end web app in [Python](/vote) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) which collects new votes
* A [.NET](/worker/) worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) database backed by a Docker volume
* A [Node.js](/result) web app which shows the results of the voting in real time

## Notes

The voting application only accepts one vote per client browser. It does not register additional votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple
example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to
deal with them in Docker at a basic level.

## Kubernetes Resources

- **PostgreSQL Deployment**: Deploys the PostgreSQL database required by the Voting app.
- **Redis Deployment**: Deploys the Redis cache used by the Voting app.
- **Voting Deployment**: Deploys the Voting application frontend.
- **Worker Deployment**: Deploys the background worker that processes votes.
- **Services**: Define the services for each deployment to enable communication between components and expose them as needed.

