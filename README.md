# Infomaniak Manifold Pipeline for Open WebUI

This repository contains a pipeline implementation that allows you to use Infomaniak's LLM models within Open WebUI.

## Prerequisites

- An Infomaniak account
- An Infomaniak API key
- Open WebUI installed
- Open WebUI Pipelines installed and running

## Installation

### Method 1: Installing from GitHub URL

You can install this pipeline directly from your Open WebUI admin panel:

1. Go to Admin Settings > Pipelines tab
2. Add a new pipeline using this URL:
   ```
   https://raw.githubusercontent.com/marborlou/infomaniak-manifold-pipeline/main/infomaniak_manifold_pipeline.py
   ```

### Method 2: Docker Setup

If you're running Open WebUI Pipelines with Docker, you can set the environment variable:

```bash
docker run -d -p 9099:9099 \
  --add-host=host.docker.internal:host-gateway \
  -e PIPELINES_URLS="https://raw.githubusercontent.com/marborlou/infomaniak-manifold-pipeline/main/infomaniak_manifold_pipeline.py" \
  -v pipelines:/app/pipelines \
  --name pipelines \
  --restart always \
  ghcr.io/open-webui/pipelines:main
```

### Method 3: Manual Installation

1. Download the `infomaniak_manifold_pipeline.py` file from this repository
2. Place it in your Open WebUI Pipelines directory (usually `/pipelines`)
3. Restart your Pipelines server

## Configuration

After installation, you'll need to configure the pipeline in Open WebUI:

1. Go to Admin Settings > Pipelines tab
2. Find the "Infomaniak Manifold" pipeline
3. Update the following valve values:
   - `INFOMANIAK_API_KEY`: Your Infomaniak API key
   - `PRODUCT_ID`: (Optional) Your Infomaniak product ID (default: 1032)
   - `NAME_PREFIX`: (Optional) Prefix to be added before model names (default: "Infomaniak ")

## Model Context Lengths

For this proxy pipeline to work properly, you need to change the maximum context value in the model's advanced parameters:

- Set 32000 for mixtral
- Set 23000 for mixtral8x22b
- Set 8000 for llama3

See the Infomaniak API documentation for more details.

## Usage

Once configured, your Infomaniak models will appear in the model selection dropdown in Open WebUI. You can use them just like any other model.

## Credits

- Original code by Shayano
- Adapted for Open WebUI Pipelines
