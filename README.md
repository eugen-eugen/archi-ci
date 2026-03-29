# Archi CI

This is a CI-only project for building the [ArchimateTool/Archi](https://github.com/archimatetool/Archi) project.

## Purpose

This repository contains a simplified GitHub Actions workflow that:
- Checks out the Archi project from GitHub
- Builds the project using Maven
- Runs tests
- Uploads build artifacts for download
- **Does NOT publish** releases (unlike the original integration-build workflow)

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
5. Uploads build artifacts (repository zip and product builds) for 30 days
4. Runs the build with tests and product profile: `mvn clean verify -P tests,product`

## Based On

This workflow is a simplified version of the [integration-build.yml](https://github.com/archimatetool/Archi/blob/master/.github/workflows/integration-build.yml) from the original Archi project, with the deployment/publishing steps removed.

## Usage

To trigger the build manually:
1. Go to the Actions tab in this repository
2. Select "Archi CI Bui

## Downloading Build Artifacts

After a successful workflow run:
1. Go to the Actions tab
2. Click on the completed workflow run
3. Scroll down to the "Artifacts" section
4. Download `archi-build-artifacts` which contains:
   - `com.archimatetool.editor.site-*.zip` - Repository archive
   - `Archi-*` product builds for various platformsld" workflow
3. Click "Run workflow"

## Original Project

- **Archi**: https://github.com/archimatetool/Archi
- **Website**: https://www.archimatetool.com/
- **License**: MIT
