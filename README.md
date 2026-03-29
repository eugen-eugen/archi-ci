# Archi CI

This is a CI-only project for building the [ArchimateTool/Archi](https://github.com/archimatetool/Archi) project.

## Purpose

This repository contains a simplified GitHub Actions workflow that:
- Checks out the Archi project from GitHub
- Builds the project using Maven
- Runs tests
- **Does NOT publish** the build artifacts (unlike the original integration-build workflow)

## Workflow

The workflow is triggered by:
- Manual workflow dispatch
- Push to main/master branches
- Pull requests to main/master branches

## Build Process

The workflow performs the following steps:
1. Checks out the Archi repository (master branch)
2. Sets up Java 21 (Temurin distribution)
3. Sets up Maven 3.9.12
4. Runs the build with tests and product profile: `mvn clean verify -P tests,product`

## Based On

This workflow is a simplified version of the [integration-build.yml](https://github.com/archimatetool/Archi/blob/master/.github/workflows/integration-build.yml) from the original Archi project, with the deployment/publishing steps removed.

## Usage

To trigger the build manually:
1. Go to the Actions tab in this repository
2. Select "Archi CI Build" workflow
3. Click "Run workflow"

## Original Project

- **Archi**: https://github.com/archimatetool/Archi
- **Website**: https://www.archimatetool.com/
- **License**: MIT
