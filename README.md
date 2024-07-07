# Spring Petclinic CI/CD Pipeline

This repository contains the Spring Petclinic project configured with a GitLab CI/CD pipeline. The pipeline performs the following steps:

1. **Compile**: Compiles the code using Maven.
2. **Test**: Runs the tests using Maven.
3. **Build**: Packages the project as a runnable Docker image.
4. **Push**: Pushes the Docker image to the GitLab container registry.

## Prerequisites

- GitLab account
- Docker installed
- Maven installed
- Git installed

## Configuration

### `pom.xml`

The `pom.xml` file is configured to use JCenter for dependency resolution. Make sure the repositories section includes:

```xml
<repositories>
    <repository>
        <id>jcenter</id>
        <url>https://jcenter.bintray.com/</url>
        <snapshots>
            <enabled>false</enabled>
        </snapshots>
    </repository>
</repositories>

.gitlab-ci.yml

The .gitlab-ci.yml file defines the CI/CD pipeline for the project. The pipeline includes stages for compilation, testing, building, and pushing the Docker image.

Running the Project Locally

To run the project locally, follow these steps:

1.	Clone the repository: 
    git clone <repository_url>
    cd spring-petclinic

2. Build the project 
    mvn clean package

3. Build the Docker image
    docker build -t spring-petclinic:latest . 

4. Run the Docker container
    docker run -p 8080:8080 spring-petclinic: latest
The application will be accessible at http://localhost:8080

Running the CI/CD Pipeline

The CI/CD pipeline will automatically run when you push changes to the repository. The pipeline performs the following stages:

	1.	Compile: Compiles the code using Maven.
	2.	Test: Runs the tests using Maven.
	3.	Build: Packages the project as a Docker image.
	4.	Push: Pushes the Docker image to the GitLab container registry.

Ensure the following GitLab CI/CD variables are set in your project settings:

	•	CI_REGISTRY_USER: Your GitLab username
	•	CI_REGISTRY_PASSWORD: Your GitLab personal access token
	•	CI_REGISTRY: Set to registry.gitlab.com

Troubleshooting

If you encounter issues, ensure the following:

	•	Your personal access token has the correct scopes (read_registry, write_registry, api).
	•	The Docker daemon is running and accessible.
	•	The .gitlab-ci.yml file is correctly configured.

For further assistance, refer to the GitLab CI/CD documentation or contact the repository maintainers.
