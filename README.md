# ComfyUI Workflows

This repository aims to be a curated collection of awesome ComfyUI workflows that serve two main purposes:
1. Help people learn ComfyUI through practical examples
2. Provide immediately reproducible workflows with complete API formats and dependencies

Each workflow is stored as a JSON file and includes all necessary configurations, making it easy to:
- Understand how different ComfyUI nodes work together
- Learn best practices for workflow design
- Deploy workflows instantly with ComfyUI Deploy
- Share and reproduce complex AI image generation pipelines

## Directory Structure

Workflows are organized by category:
- `workflows/florence2/`: Florence2 model related workflows
- `workflows/stable-diffusion/`: Stable Diffusion related workflows
- `workflows/controlnet/`: ControlNet related workflows

## Standardization

This repository hopes to follows standardization guidelines to ensure workflows work across different cloud providers:
- Environment variables for API keys and endpoints
- Standardized model download paths
- Consistent node naming conventions
- Version-locked dependencies
- Cloud-agnostic storage paths

## Roadmap

### Short-term Goals
- [ ] Add more example workflows for common use cases
- [ ] Implement automated workflow testing
- [ ] Create workflow documentation templates
- [ ] Add model validation checks
- [ ] Support for more cloud providers

## Contributing

When adding new workflows:
1. Create a new JSON file in the appropriate category directory
2. Follow the established format for nodes and connections
3. Include all necessary environment configurations
4. Test the workflow before committing
5. Add model information and hashes
6. Follow standardization guidelines

## Technical Details

### Workflow Format

A workflow JSON file consists of several main sections:

### 1. Basic Structure
```json
{
    "extra": {},
    "links": [...],
    "nodes": [...],
    "config": {},
    "groups": [],
    "version": float,
    "last_link_id": int,
    "last_node_id": int,
    "workflow_api": {...},  // Contains the API configuration for the workflow
    "environment": {...}    // Specifies runtime requirements and dependencies
}
```

### 2. Key Components

#### Environment
The environment section specifies runtime requirements:
- `comfyui_version`: Version of ComfyUI
- `gpu`: Required GPU type
- `docker_command_steps`: Custom node installations
- `python_version`: Required Python version