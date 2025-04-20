# ComfyUI Workflows

This repository aims to be a curated collection of awesome ComfyUI workflows that serve two main purposes:

1. Help people learn ComfyUI through practical examples
2. Provide immediately reproducible workflows with complete API formats and dependencies

Each workflow is stored as a JSON file and includes all necessary configurations, making it easy to:

- Understand how different ComfyUI nodes work together
- Learn best practices for workflow design
- Deploy workflows instantly with **ComfyDeploy**
- Share and reproduce complex AI image generation pipelines

## Directory Structure

Workflows are organized by category:

- `workflows/stable-diffusion/`: Stable Diffusion related workflows
- `workflows/controlnet/`: controlnet related workflows

### Available Workflow Templates

| Preview                                              | Category                      | Description                       |
| ---------------------------------------------------- | ----------------------------- | --------------------------------- |
| ![](<workflows\flux\GhibliStyleGenerator(flux).png>) | `flux/ghibli_img2img.json`    | Ghibli-style image transformation |
| ![](<workflows\flux\PixelArtGenerator(flux).png>)    | `flux/pixelart_text2img.json` | Pixel art image from text prompt  |

## Standardization

This repository hopes to follows standardization guidelines to ensure workflows work across different cloud providers:

- Environment variables for **API keys** and **endpoints**
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

## API-Compatible Workflow Preview

ComfyDeploy supports exposing parameters from a ComfyUI workflow as editable input fields in the web interface. This allows users to run workflows without editing the graph directly.

### 🔧 Wan_img2vdo Workflow Template

[🚀 Run it on ComfyDeploy](https://app.comfydeploy.com/share/comfy-deploy/5PZzf7jAg0XmJPPp)

A video generation ComfyUI workflow using external parameter nodes, allowing users to adjust values like prompt, resolution, and frame count directly from the ComfyDeploy UI or via API.

| Preview                            | Category               | Description                      |
| ---------------------------------- | ---------------------- | -------------------------------- |
| ![](workflows/wan/wan_img2vdo.gif) | `wan/wan_img2vid.json` | Pixel art image from text prompt |

![UI Preview](./assets/Screenshot_01.png)

| Type   | Field             | Description                                             |
| ------ | ----------------- | ------------------------------------------------------- |
| image  | **`input_image`** | Upload an image or paste a URL as the base frame        |
| string | **`prompt`**      | (Optional) Add a prompt to guide the style or effects   |
| toggle | **`HD`**          | Enables high-resolution output (slower, uses more VRAM) |
| int    | **`resize`**      | Target width/height of each frame (e.g. 512, 768)       |
| int    | **`frame`**       | Total number of frames to generate (e.g. 24)            |
| int    | **`fps`**         | Frames per second (e.g. 12 fps = 2-second video)        |
| toggle | **`image_crop`**  | Toggle on to auto-crop the input image into a square    |

---

The following ComfyUI node types are used to define UI parameters:

- **`ComfyUIDeployExternalImage`** : image upload or URL input
- **`ComfyUIDeployExternalText`** : string inputs such as prompts
- **`ComfyUIDeployExternalNumber`** : numeric inputs (int/float)
- **`ComfyUIDeployExternalBool`** : toggle switches (true/false)

[🔗 ComfyUI Deploy Node Documentation](https://github.com/BennyKok/comfyui-deploy)
