# Coder Custom Templates

This repository contains custom Terraform templates for creating development environments with [Coder](https://coder.com/). These templates provide different configurations for setting up workspaces tailored to various development needs.

## Available Templates

### 1. Custom Dockerfile with Docker

Located in `custom-dockerfile-docker/`, this template:
- Uses a custom Docker image built from a Dockerfile
- Provides code-server (VS Code in browser)
- Supports JetBrains Gateway IDEs
- Includes Cursor AI coding assistant
- Supports automatic repository cloning
- Includes dotfiles and personalization modules

### 2. Devcontainer Template

Located in `dot-devcontainer/`, this template:
- Uses the devcontainer specification to build environments
- Automatically detects and builds devcontainers from repositories
- Supports caching built images in a container registry
- Provides code-server and JetBrains Gateway
- Includes Cursor AI coding assistant
- Supports dotfiles and personalization

### 3. Custom Dockerfile with Devcontainer

Located in `custom-dockerfile-devcontainer/`, this template:
- Combines custom Dockerfile capabilities with devcontainer support
- Allows switching between custom Dockerfile and base image
- Provides code-server (VS Code in browser)
- Supports JetBrains Gateway IDEs
- Includes Cursor AI coding assistant
- Supports dotfiles and personalization

### 4. Docker Template

Located in `dot-docker/`, this template:
- Provides a simpler Docker-based development environment
- Uses a pre-built Docker image
- Includes code-server (VS Code in browser)
- Persistent home directory using Docker volumes
- Lightweight alternative to the more feature-rich templates

## Getting Started

### Prerequisites

1. [Coder](https://coder.com/) server installed and running
2. [Terraform](https://www.terraform.io/downloads.html) CLI installed (v1.0+)
3. Docker installed (for local development)

### Using the Templates

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/coder-templates.git
   cd coder-templates
   ```

2. Create a template in your Coder deployment:
   ```bash
   coder templates create --directory ./custom-dockerfile-docker
   # OR
   coder templates create --directory ./dot-devcontainer
   # OR
   coder templates create --directory ./custom-dockerfile-devcontainer
   # OR
   coder templates create --directory ./dot-docker
   ```

3. Create a workspace using your template:
   ```bash
   coder create --template=<template-name> my-workspace
   ```

## Developing Templates

### Local Development Workflow

```
cd <template-directory>
```

1. Make changes to the template files (main.tf, etc.)

2. Initialize the Terraform working directory:
   ```bash
   terraform init
   ```

3. Validate your Terraform configuration:
   ```bash
   terraform validate
   ```

4. Format your Terraform files:
   ```bash
   terraform fmt
   ```

5. Plan the changes:
   ```bash
   terraform plan
   ```

6. Test the template with Coder:
   ```bash
   coder templates create --directory ./<template-directory> --test
   ```

7. Create a test workspace:
   ```bash
   coder create --template=<template-name> test-workspace
   ```

8. After testing, clean up:
   ```bash
   coder delete test-workspace
   ```

### Customizing Templates

#### Custom Dockerfile Template

1. Modify the `build/Dockerfile` to customize the development environment
2. Update `main.tf` to add/remove modules or change configuration parameters
3. Add repository options in the `coder_parameter.repo` resource

#### Devcontainer Template

1. Update repository options in the `coder_parameter.repo` resource
2. Modify cache settings if using a container registry
3. Update module versions or add new modules as needed

#### Custom Dockerfile with Devcontainer

1. Toggle between using a custom Dockerfile or a base image
2. Customize the `.devcontainer` directory for devcontainer settings
3. Modify parameters in `main.tf` to adjust workspace configuration

#### Docker Template

1. Change the base image in the `docker_image` resource
2. Modify the startup script in the `coder_agent` resource
3. Adjust volume settings for persistence needs

## Template Features

### Git Repository Integration

Most templates support automatic repository cloning. You can:
- Select from predefined repositories
- Specify a custom repository URL
- Choose not to clone any repository

### IDE Support

The templates provide multiple IDE options:
- Code Server (VS Code in browser)
- JetBrains Gateway (IntelliJ, PyCharm, WebStorm, etc.)
- Cursor (AI-assisted coding)

### Personalization

Templates support various personalization options:
- Dotfiles repositories for personalization
- Git configuration using workspace owner information
- Workspace statistics for monitoring resource usage

## Troubleshooting

### Common Issues

1. **Docker connection issues**:
   - Ensure Docker is running
   - Check the `docker_socket` variable if using a non-standard Docker socket

2. **Repository cloning fails**:
   - Verify the repository URL is correct
   - Ensure the workspace has internet access
   - Check if authentication is required for private repositories

3. **Module errors**:
   - Verify module versions are compatible with your Coder version
   - Check for typos in module source URLs

4. **Devcontainer detection issues**:
   - Ensure the repository has a valid `.devcontainer` directory
   - Check that the devcontainer configuration is properly formatted

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

[MIT License](LICENSE) 