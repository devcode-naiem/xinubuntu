<div align="center">
<h1> XINUBUNTU </h1>
</div>

<div align="center">

![Xinubuntu](https://i.ibb.co.com/0y5RjZvg/xinubuntu.png)

*Transform your Xinu OS development experience with Docker*

[![Docker Pulls](https://img.shields.io/docker/pulls/devcodenaiem/xinubuntu?style=for-the-badge&logo=docker&color=0db7ed&logoColor=white)](https://hub.docker.com/r/devcodenaiem/xinubuntu)
[![GitHub Stars](https://img.shields.io/github/stars/devcode-naiem/xinubuntu?style=for-the-badge&logo=github&color=yellow&logoColor=white)](https://github.com/devcode-naiem/xinubuntu)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](LICENSE)
[![Windows Support](https://img.shields.io/badge/Windows-Tested-blue?style=for-the-badge&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
[![VS Code](https://img.shields.io/badge/VS_Code-Ready-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white)](https://code.visualstudio.com/)

---

**[Installation](#installation) • 
[Development](#development) • 
[Documentation](#documentation) • 
[Support](#support)**

</div>

## 🚀 Introduction

Xinubuntu revolutionizes Xinu Operating System development by providing a streamlined, Docker-based environment. Say goodbye to complex virtual machine setups and hello to instant development readiness.

### Why Choose Xinubuntu?

| Traditional Approach | Xinubuntu Solution |
|---------------------|-------------------|
| 10+ GB Virtual Machine | ~2 GB Docker Container |
| Hours of Setup Time | Minutes to Start |
| Complex Configuration | Single Command |
| Platform Dependencies | Consistent Environment |
| Resource Intensive | Lightweight Solution |

## 💻 Quick Start

```bash
# Start your development environment
docker run -it devcode-naiem/xinubuntu:latest
```

## 📋 Prerequisites

### System Requirements

- **OS**: Windows 10/11 64-bit
- **RAM**: 8GB minimum (16GB recommended)
- **Storage**: 10GB free space
- **Processor**: Intel/AMD with virtualization support
- **WSL2**: Enabled

### Required Software

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Remote Development Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

## 🛠️ Development Setup

### 1. Environment Initialization

```bash
# Pull the latest image
docker pull devcode-naiem/xinubuntu:latest

# Create development container
docker run -it --name xinu-dev devcode-naiem/xinubuntu:latest
```

### 2. VS Code Integration

1. Open VS Code
2. Press `F1` or `Ctrl+Shift+P`
3. Select "Dev Containers: Attach to Running Container"
4. Choose "xinu-dev"

### 3. Project Structure

```
xinu-x86-gui/
├── 📁 compile/        # Build system & configuration
├── 📁 include/        # Header files & definitions
├── 📁 shell/         # Shell commands & implementations
└── 📁 system/        # Core system files
```

## 🔧 Development Workflow

### Building Xinu

```bash
# Navigate to compile directory
cd /xinu-x86-gui/compile

# Clean and build
make clean && make

# Run in QEMU
make run-qemu
```

### QEMU Controls

| Action | Keys | Description |
|--------|------|-------------|
| Exit | `Ctrl+A`, `X` | Clean shutdown |
| Reset | `Ctrl+A`, `C` | System reset |
| Help | `Ctrl+A`, `H` | Show commands |

## 📚 Documentation

### Core Components

<table>
<tr>
<th width="140">Component</th>
<th>Description</th>
</tr>
<tr>
<td><b>🔨 Build System</b></td>
<td>Located in <code>compile/</code>, manages system compilation and configuration</td>
</tr>
<tr>
<td><b>📄 Shell Commands</b></td>
<td>Custom commands in <code>shell/</code> for system interaction</td>
</tr>
<tr>
<td><b>⚙️ System Core</b></td>
<td>Core functionality in <code>system/</code> directory</td>
</tr>
<tr>
<td><b>📚 Headers</b></td>
<td>System definitions and prototypes in <code>include/</code></td>
</tr>
</table>

## ⚠️ Troubleshooting

### Common Issues

<details>
<summary><b>Docker Connection Issues</b></summary>

```bash
# Restart Docker Desktop
1. End Docker Desktop process
2. Start Docker Desktop
3. Wait for complete initialization
```
</details>

<details>
<summary><b>Build Failures</b></summary>

```bash
# Clean build environment
cd /xinu-x86-gui/compile
make clean
make
```
</details>

## 🌟 Platform Support

| Platform | Status | Testing | Notes |
|----------|---------|---------|--------|
| Windows 11 | ✅ | Full | Primary platform |
| Windows 10 | ✅ | Full | WSL2 required |
| Linux | ⚠️ | None | May work |
| macOS | ❌ | None | Not supported |

## 👥 Credits

### Project Contributors

- **Original Xinu OS**
  - Douglas Comer, Purdue University
  - [Xinu Project Page](https://xinu.cs.purdue.edu)

- **Xinu x86 GUI**
  - Rafael Ignacio Zurita
  - [Source Repository](https://github.com/zrafa/xinu-x86-gui)

- **Xinubuntu Container**
  - Devcode Naiem
  - [GitHub Profile](https://github.com/devcode-naiem)

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Engineered with precision by [Devcode Naiem](https://github.com/devcode-naiem)**

⭐ If you find this project valuable, consider giving it a star!

[Report Bug](https://github.com/devcode-naiem/xinubuntu/issues) • 
[Request Feature](https://github.com/devcode-naiem/xinubuntu/issues) • 
[Get Support](https://github.com/devcode-naiem/xinubuntu/discussions)

</div>
