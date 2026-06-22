# 🚀 Jenkins-Based Continuous Integration (CI) Pipeline with Distributed Build Architecture on AWS

![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-red)
![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Maven](https://img.shields.io/badge/Maven-Build-blue)
![GitHub](https://img.shields.io/badge/GitHub-VersionControl-black)
![DevOps](https://img.shields.io/badge/DevOps-Automation-green)

## 📌 Project Overview

This project demonstrates the implementation of a *Continuous Integration (CI) pipeline using Jenkins on AWS*, designed to automate source code integration, build execution, testing, and artifact generation for a Java-based web application.

The pipeline was initially implemented as a traditional Jenkins build system and later extended into a *distributed build architecture using a dedicated Jenkins Agent deployed on AWS EC2*.

This setup simulates a real-world DevOps CI environment where build workloads are separated between a Jenkins Controller and multiple build Agents for improved scalability and performance.


## 🎯 Business Objective

To design and implement an automated Continuous Integration (CI) pipeline that:

- Integrates source code from GitHub
- Automates Maven-based build lifecycle
- Compiles and tests application code
- Generates deployable WAR artifacts
- Implements distributed build execution using Jenkins Agent architecture
- Demonstrates scalable, production-like CI/CD workflow on AWS infrastructure
