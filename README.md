# Archi CI

This is a CI-only project for building the [ArchimateTool/Archi](https://github.com/archimatetool/Archi) project.

## Purpose

This repository contains CI/CD configurations for building the Archi project:
- **GitHub Actions** workflow (`.github/workflows/build.yml`)
- **GitLab CI/CD** pipeline (`.gitlab-ci.yml`)

Both configurations:
- Check out the Archi project from GitHub
- Build the project using Maven with Java 21
- Run tests
- Upload build artifacts for download
- **Do NOT publish** releases (unlike the original integration-build workflow)

## CI Platforms

### GitHub Actions

Triggered by:
- Manual workflow dispatch
- Push to main/master branches
- Pull requests to main/master branches

### GitLab CI/CD

Triggered by:
- Manual pipeline run
- Push to main/master branches
- Merge requests

## Build Process

Both pipelines perform the following steps:
1. Check out the Archi repository (master branch) from GitHub
2. Set up Java 21 (OpenJDK/Temurin)
3. Set up Maven 3.9.12
4. Run the build with tests and product profile: `mvn clean verify -P tests,product`
5. Upload build artifacts (repository zip and product builds) for 1 day

## Based On

These workflows are simplified versions of the [integration-build.yml](https://github.com/archimatetool/Archi/blob/master/.github/workflows/integration-build.yml) from the original Archi project, with the deployment/publishing steps removed.

## Usage

### GitHub Actions

To trigger the build manually:
1. Go to the Actions tab in this repository
2. Select "Archi CI Build" workflow
3. Click "Run workflow"

**Downloading Artifacts:**
1. Go to the Actions tab
2. Click on the completed workflow run
3. Scroll down to the "Artifacts" section
4. Download `archi-build-artifacts`

### GitLab CI/CD

To trigger the pipeline manually:
1. Go to CI/CD → Pipelines in your GitLab project
2. Click "Run pipeline"
3. Select the branch and click "Run pipeline"

**Downloading Artifacts:**
1. Go to CI/CD → Pipelines
2. Click on the completed pipeline
3. Click on the job name (e.g., "build-archi")
4. Click "Browse" or "Download" in the artifacts section

## Artifacts Contents

Both pipelines produce the same artifacts:
- `com.archimatetool.editor.site-*.zip` - Repository archive
- `Archi-*` product builds for various platforms (Windows, macOS, Linux)

## Original Project

- **Archi**: https://github.com/archimatetool/Archi
- **Website**: https://www.archimatetool.com/
- **License**: MIT
