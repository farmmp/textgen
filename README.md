# TextGen

A fork of [oobabooga/text-generation-webui](https://github.com/oobabooga/text-generation-webui) with additional features and improvements.

## Features

- Web UI for running Large Language Models
- Support for multiple model backends (llama.cpp, ExLlamaV2, Transformers, etc.)
- OpenAI-compatible API
- Character/persona support
- Extensions system
- Portable releases for Windows, Linux, and macOS

## Installation

### Portable Release (Recommended)

Download the latest release from the [Releases](../../releases) page for your platform:

- `textgen-windows-cuda.zip` — Windows with NVIDIA GPU
- `textgen-linux-cuda.zip` — Linux with NVIDIA GPU
- `textgen-cpu.zip` — CPU-only (Windows/Linux)

Extract and run `start_windows.bat` (Windows) or `start_linux.sh` (Linux).

### Manual Installation

#### Prerequisites

- Python 3.11+
- CUDA 12.1+ (for GPU support)
- Git

#### Steps

```bash
git clone https://github.com/your-org/textgen
cd textgen
pip install -r requirements.txt
python server.py
```

#### GPU (CUDA)

```bash
pip install -r requirements.txt
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
python server.py
```

## Usage

```bash
# Start with default settings
python server.py

# Start with a specific model
python server.py --model my-model

# Enable API
python server.py --api

# Listen on all interfaces
python server.py --listen

# Use a specific port
python server.py --port 7860
```

## API

When started with `--api`, TextGen exposes an OpenAI-compatible REST API at `http://localhost:5000/v1`.

See the [API documentation](docs/API.md) for details.

## Extensions

Extensions can be loaded with `--extensions extension_name`. See the `extensions/` directory for available extensions and the [extension guide](docs/Extensions.md) for writing your own.

## My Setup

I run this locally on an RTX 3080 with the following command:

```bash
python server.py --model mistral-7b-instruct --api --listen --port 7860 --n-gpu-layers 35
```

> Note: `--n-gpu-layers 35` offloads 35 layers to the GPU which works well for my 10GB VRAM budget with mistral-7b.

## Contributing

Pull requests are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting.

## License

AGPL-3.0. See [LICENSE](LICENSE) for details.
