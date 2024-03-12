# FinTrack - Infrastructure and DevOps README

Welcome to the Infrastructure and DevOps README for the FinTrack project. This document provides an in-depth overview of the infrastructure, network, and DevOps tools and practices used in our Spring project. It serves as a reference for team members and stakeholders to understand how we manage the software and infrastructure.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Infrastructure and Network](#infrastructure-and-network)
   - [Docker](#docker)
   - [Kubernetes](#kubernetes)
   - [ArgoCD](#argocd)
3. [Continuous Integration and Continuous Deployment](#continuous-integration-and-continuous-deployment)
   - [Jenkins](#jenkins)
   - [GitOps](#gitops)
4. [Code Quality and Security](#code-quality-and-security)
   - [SonarQube](#sonarqube)
5. [Configuration Management](#configuration-management)
   - [Ansible](#ansible)
6. [Monitoring and Metrics](#monitoring-and-metrics)
   - [Grafana](#grafana)
   - [Prometheus](#prometheus)
7. [High Availability](#high-availability)
8. [Notifications](#notifications)
9. [Automated Database Backup](#automated-database-backup)
10. [Network File Sharing](#network-file-sharing)
11. [Contact Information](#contact-information)

## Project Overview

The project focuses on providing advanced notification features and management, allowing to customize notification preferences and stay informed about various financial transactions and account changes.

These features are critical for ensuring efficient communication with users and providing timely updates on their financial activities. The project aims to enhance user experience and provide valuable financial information through push notifications.

## Infrastructure and Network

### Docker

We use Docker for containerization, allowing us to package our applications and their dependencies into isolated containers. These containers can run consistently across different environments. Docker simplifies application deployment and maintenance.

### Kubernetes

Kubernetes is our container orchestration platform. It helps manage and scale containerized applications, automates deployment, scaling, and management, and provides advanced features for containerized workloads.

k8s service:
+. add-ons
- ingress-nginx
- cert-manager
- ArgoCD
- Dashboard
+. third-parties
- Grafana, Alert Manager Dashboard and Prometheus using prometheus-operator
 

### ArgoCD

ArgoCD is our GitOps tool for managing Kubernetes resources. It keeps our Kubernetes clusters in sync with a Git repository, making it easier to maintain, audit, and control our infrastructure.

- We have deploy Fintrack-ui and setup with ingress and cert-manager(https): https://web-fintrack.kbaenak.tech/
- We have use GetOps to store config fie : https://github.com/ksga-11th-generation-advance-course/spring_microservcie_fin_track_infra.git

ArgoCD-server: https://34.87.126.74:31813
username: admin
password: #KSHRD2023

## Continuous Integration and Continuous Deployment

### Jenkins

Jenkins is our CI/CD server. It automates our software build, test, and deployment processes. We use Jenkins to ensure the quality of our code and to automate deployments to our Kubernetes clusters.

+ Jenkins server: http://34.124.186.14:8080/
- uername: admin
- password: #KSHRD2023

+ When codes are pushed to branch "deployment" the CI/CD will started and we also add webhook in github repo too.

+ we have built pipline that intergrate with :

Pipeline1:
- Telegram to alert notification: 
  telegram bot token: 6303010424:AAGq5uvAlsTgXc-YoYpdzUi5WQaYcJQo9Oo
  telegram group id: -4098383966
- SonarQube
- Dockerhub: https://hub.docker.com/repository/docker/kimheang68/ui-fintrack/general

Pipeline2:
- When docker image update success so we have set it to change docker image tag in GitOps repo
- After change tag success so Argocd will be start update the deployment
 
+ We also add 2 slaver nodes too.

### GitOps

GitOps is our approach to managing Kubernetes resources using version-controlled Git repositories. It enables us to maintain infrastructure as code and keep everything in sync with our Git repositories.

- Git repo : https://github.com/ksga-11th-generation-advance-course/spring_microservcie_fin_track_infra.git

## Code Quality and Security

### SonarQube

SonarQube is our code quality and security analysis tool. It helps us maintain code quality and security standards by identifying and reporting code issues.

- We have integrated it with pipeline Jenkins.

SonarQube-server: http://34.87.126.74:9000
username: admin
password: #KSHRD2023

## Configuration Management

### Ansible

We use Ansible for configuration management. Ansible allows us to automate the provisioning and configuration of servers and other infrastructure components. It helps maintain consistency and repeatability across environments.

## Monitoring and Metrics

### Grafana

Grafana is our monitoring and visualization tool. It provides a unified view of our applications and infrastructure performance, helping us spot issues quickly.

- we have setup it with prometheus to monitoring k8s.

Grafana server: http://34.87.126.74:31564/
username: admin
password: #KSHRD2023

### Prometheus

Prometheus is our monitoring and alerting tool. It collects metrics and provides alerts based on predefined conditions, ensuring the reliability and availability of our services.

Prometheus server: http://34.87.126.74:32435/graph

Alertmanager server: http://34.87.126.74:30786/#/alerts

## High Availability

We implement high availability strategies to ensure our services are always accessible and reliable. This includes load balancing, redundancy, and fault tolerance.

## Notifications

We have set up various notification channels, including email, Telegram, and others, to stay informed about the status of our applications and infrastructure.

## Automated Database Backup

We automatically backup our databases at regular intervals to prevent data loss and ensure data recovery in case of issues.

## Network File Sharing

We've configured network file sharing to facilitate collaboration and data sharing among team members.

## Contact Information

If you have questions or need assistance with our infrastructure and DevOps practices, please contact:

- [Ken Kimheang](mailto:kimheangken68@gmail.com)

Thank you for using this Infrastructure and DevOps README as a reference. We continuously strive to maintain the highest standards in our development and operations processes.

