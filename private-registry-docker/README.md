# Private Registry Docker Template

This template creates a Coder workspace using a Docker image from a private registry.

## Prerequisites

- Coder server running
- Docker installed on the Coder host
- Access to the private Docker registry (registry.example.com)
- Valid credentials for the private registry

## Usage

1. Create the template in Coder:

```bash
coder templates create private-registry-docker
```

2. When creating a workspace from this template, you'll need to provide:
   - `config_file_content`: Update "SecretPassword" from ~/.docker/config.json for your registry.

   You can get it by running `docker login https://registry.example.com` and `cat ~/.docker/config.json`.

## Features

- Pulls the `example:0.0.1` image from registry.example.com
- Authenticates with the private registry using provided credentials
- Persists home directory using Docker volumes
- Includes code-server (VS Code in browser)
- Supports JetBrains Gateway
- Supports Cursor editor
- Supports dotfiles and personalization
- Automatically clones Git repositories

## Configuration

The template uses the following variables:

- `docker_socket`: (Optional) Docker socket URI
- `registry_username`: Username for the private Docker registry
- `registry_password`: Password for the private Docker registry
- `repo`: Repository to automatically clone
- `custom_repo_url`: Custom repository URL if "Custom" is selected

## Security Notes

- Registry credentials are marked as sensitive and won't be displayed in logs
- Authentication is handled securely through the Docker provider
- Credentials are not stored in the container image

## Troubleshooting

If you encounter issues with pulling the image:

1. Verify your registry credentials are correct
2. Ensure the Coder host has network access to registry.example.com
3. Check that the image tag exists in the registry
4. Verify Docker is properly configured on the Coder host

For more information, see:
- [Coder Documentation](https://coder.com/docs/v2/latest)
- [Docker Provider Documentation](https://registry.terraform.io/providers/kreuzwerker/docker/latest/docs) 