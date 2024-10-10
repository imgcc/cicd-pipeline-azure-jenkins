# CI/CD Pipeline with Jenkins and Azure DevOps

This project demonstrates how to build a CI/CD pipeline for a Node.js application using Jenkins, Docker, and Azure Kubernetes Service (AKS).

## Features

- Jenkins pipeline to build and deploy a Node.js application.
- Docker integration to containerize the application.
- Azure Container Registry (ACR) for storing Docker images.
- Azure Kubernetes Service (AKS) for deploying the application.
- Automated deployment using Kubernetes.

## Project Structure

cicd-pipeline-azure-jenkins/
<table>
  <tr>
    <th>File/Directory</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>Jenkinsfile</code></td>
    <td>Jenkins pipeline script</td>
  </tr>
  <tr>
    <td><code>Dockerfile</code></td>
    <td>Dockerfile for building the Node.js application</td>
  </tr>
  <tr>
    <td><code>k8s-deployment.yaml</code></td>
    <td>Kubernetes deployment manifest</td>
  </tr>
  <tr>
    <td><code>azure-pipeline.yml</code></td>
    <td>Azure DevOps pipeline configuration</td>
  </tr>
  <tr>
    <td><code>src/</code></td>
    <td>Source code for Node.js application</td>
  </tr>
  <tr>
    <td><code>README.md</code></td>
    <td>Project documentation</td>
  </tr>
</table>

## Requirements

- Jenkins server with Docker and Azure CLI installed.
- Azure Container Registry (ACR).
- Azure Kubernetes Service (AKS).