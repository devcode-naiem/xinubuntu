<div align="center">

# Xinubuntu
### Advanced Xinu Operating System Development Environment

<img src="https://i.ibb.co.com/0y5RjZvg/xinubuntu.png" alt="Xinubuntu" width="400">

[![Docker Pulls](https://img.shields.io/docker/pulls/devcodenaiem/xinubuntu.svg?style=for-the-badge&logo=docker&color=0db7ed)](https://hub.docker.com/r/devcode-naiem/xinubuntu)
[![GitHub Stars](https://img.shields.io/github/stars/devcode-naiem/xinubuntu.svg?style=for-the-badge&logo=github&color=yellow)](https://github.com/devcode-naiem/xinubuntu/stargazers)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](LICENSE)
[![Windows](https://img.shields.io/badge/Windows-Tested-blue.svg?style=for-the-badge&logo=windows&logoColor=white)](https://www.microsoft.com/windows)
[![Version](https://img.shields.io/badge/Version-1.0.0-green.svg?style=for-the-badge&logo=semver&logoColor=white)](https://github.com/devcode-naiem/xinubuntu/releases)

*A professionally engineered Docker container providing a streamlined development environment for the Xinu Operating System.*

[Installation Guide](#installation-guide) • 
[Documentation](#documentation) • 
[Development](#development) • 
[Contributing](#contributing)

---

</div>

## 📚 Comprehensive Documentation

### Table of Contents

1. [Introduction](#introduction)
2. [System Requirements](#system-requirements)
3. [Platform Compatibility](#platform-compatibility)
4. [Installation Guide](#installation-guide)
5. [Environment Setup](#environment-setup)
6. [Development Guide](#development-guide)
7. [Advanced Usage](#advanced-usage)
8. [Troubleshooting](#troubleshooting)
9. [Best Practices](#best-practices)
10. [Support](#support)
11. [Credits](#credits)
12. [License](#license)

## Introduction

### Why Xinubuntu?

Xinubuntu revolutionizes Xinu operating system development by providing a containerized environment that eliminates traditional setup complexities.

#### Traditional Development Challenges

<details>
<summary><strong>🔄 Complex Setup Process</strong></summary>

- Requires dual-boot configuration
- Manual installation of development tools
- Complex dependency management
- Platform-specific configuration issues
- Time-consuming environment setup
</details>

<details>
<summary><strong>💾 Resource Intensive</strong></summary>

- VirtualBox installation (10+ GB)
- Full Ubuntu desktop environment
- Significant disk space requirements
- Heavy system resource usage
- Slow development workflow
</details>

#### The Xinubuntu Solution

<table>
<tr>
<th>Feature</th>
<th>Benefit</th>
<th>Implementation</th>
</tr>
<tr>
<td>Containerized Environment</td>
<td>Isolated, consistent development space</td>
<td>Docker container (~2GB)</td>
</tr>
<tr>
<td>Pre-configured Tools</td>
<td>Immediate development start</td>
<td>All tools pre-installed and configured</td>
</tr>
<tr>
<td>Resource Efficient</td>
<td>Minimal system impact</td>
<td>Optimized container size</td>
</tr>
<tr>
<td>VS Code Integration</td>
<td>Modern development experience</td>
<td>Dev Containers support</td>
</tr>
<tr>
<td>Cross-platform Support*</td>
<td>Development flexibility</td>
<td>Docker-based compatibility</td>
</tr>
</table>

\* Currently tested only on Windows platforms

## System Requirements

### Hardware Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| Processor | Intel Core i3/AMD Ryzen 3 | Intel Core i5/AMD Ryzen 5 or better |
| Memory | 8GB RAM | 16GB RAM |
| Storage | 10GB free space | 20GB SSD space |
| Virtualization | VT-x/AMD-V support | VT-x/AMD-V with SLAT |
| Network | Stable internet connection | High-speed broadband |

### Software Requirements

| Software | Version | Purpose |
|----------|---------|----------|
| Windows | 10/11 (64-bit) | Host Operating System |
| Docker Desktop | Latest | Container Runtime |
| VS Code | Latest | Development Environment |
| WSL2 | Latest | Linux Subsystem Support |
| Git | Latest | Version Control |

## Platform Compatibility

### Tested Environments

| Platform | Version | Status | Notes |
|----------|---------|--------|--------|
| Windows 11 | 21H2+ | ✅ Fully Tested | Primary development platform |
| Windows 10 | 20H2+ | ✅ Fully Tested | Requires WSL2 |
| Windows Server | 2019+ | ⚠️ Limited Testing | May require additional setup |
| Linux | Various | ❓ Not Tested | May work but unsupported |
| macOS | Any | ❌ Not Supported | Not compatible currently |

## Installation Guide

### Step 1: Docker Desktop Installation

```powershell
# 1. Download Docker Desktop
Start-Process "https://www.docker.com/products/docker-desktop/"

# 2. Install Docker Desktop
# - Enable WSL2 features when prompted
# - Allow privileged access

# 3. Verify Installation
docker --version
docker run hello-world
```

### Step 2: VS Code and Extensions

```powershell
# 1. Install VS Code
Start-Process "https://code.visualstudio.com/"

# 2. Install Required Extensions
code --install-extension ms-vscode-remote.vscode-remote-extensionpack
code --install-extension ms-vscode.cpptools-extension-pack
code --install-extension ms-azuretools.vscode-docker
```

### Step 3: Pull Xinubuntu Image

Choose your preferred registry:

```bash
# Docker Hub
docker pull devcode-naiem/xinubuntu:latest

# GitHub Container Registry
docker pull ghcr.io/devcode-naiem/xinubuntu:latest
```

## Environment Setup

### Directory Structure

```plaintext
xinubuntu/
├── 📂 compile/
│   ├── 📄 Makefile
│   └── 📄 Configuration files
├── 📂 config/
│   └── 📄 System configurations
├── 📂 include/
│   ├── 📄 xinu.h
│   └── 📄 Header files
├── 📂 shell/
│   ├── 📄 shell.c
│   └── 📄 Command implementations
└── 📂 system/
    └── 📄 Core system files
```

### VS Code Integration

```bash
# 1. Start Container
docker run -it --name xinu-dev devcode-naiem/xinubuntu:latest

# 2. Open VS Code Command Palette (Ctrl+Shift+P)
# 3. Select: Dev Containers: Attach to Running Container
# 4. Choose: xinu-dev

# 5. Open Terminal in VS Code
cd /xinu-x86-gui/compile
```

## Development Guide

### Building Xinu

```bash
# Clean build
make clean

# Compile
make

# Run in QEMU
make run-qemu
```

### QEMU Controls

| Action | Keyboard Shortcut | Description |
|--------|------------------|-------------|
| Exit QEMU | Ctrl+A, X | Clean shutdown |
| Reset VM | Ctrl+A, C | Soft reset |
| Help | Ctrl+A, H | Show QEMU commands |

### Creating Custom Commands

1. Create Command File:
```c
// /xinu-x86-gui/shell/xsh_custom.c
#include <xinu.h>

shellcmd xsh_custom(int nargs, char *args[]) {
    if (nargs == 1) {
        kprintf("Custom command executed\n");
        return OK;
    } else {
        kprintf("Usage: %s\n", args[0]);
        return SYSERR;
    }
}
```

2. Register Command:
```c
// /xinu-x86-gui/shell/cmdtab.c
{"custom", FALSE, xsh_custom},
```

3. Add Prototype:
```c
// /xinu-x86-gui/include/shprototypes.h
extern shellcmd xsh_custom(int nargs, char *args[]);
```

## Advanced Usage

### Debugging

```bash
# Start GDB server in QEMU
make debug

# In another terminal
gdb xinu.elf
(gdb) target remote localhost:1234
```

### Performance Optimization

1. Container Resource Allocation:
```bash
docker run -it --cpus=2 --memory=4g devcode-naiem/xinubuntu:latest
```

2. QEMU Optimization:
```bash
# Enable KVM if available
make run-qemu QEMU_FLAGS="-enable-kvm"
```

## Troubleshooting

### Common Issues

<details>
<summary><strong>🔴 Docker Connection Issues</strong></summary>

```bash
# Reset Docker Desktop
1. Task Manager → End Docker Desktop
2. Delete %APPDATA%\Docker\settings.json
3. Restart Docker Desktop
```
</details>

<details>
<summary><strong>🔴 Build Failures</strong></summary>

```bash
# Clean environment
cd /xinu-x86-gui/compile
make clean
rm -rf test/
make
```
</details>

<details>
<summary><strong>🔴 QEMU Problems</strong></summary>

```bash
# If QEMU hangs
1. Ctrl+A, X
2. docker exec xinu-dev killall qemu-system-i386
3. docker restart xinu-dev
```
</details>

## Best Practices

1. **Version Control**
   - Maintain separate branches for features
   - Regular commits with meaningful messages
   - Use .gitignore for build artifacts

2. **Development Workflow**
   - Create feature branches
   - Test thoroughly before merging
   - Document changes properly

3. **Code Style**
   - Follow Xinu coding standards
   - Maintain consistent indentation
   - Add appropriate comments

## Support

- [Report Issues](https://github.com/devcode-naiem/xinubuntu/issues)
- [Request Features](https://github.com/devcode-naiem/xinubuntu/issues)
- [Documentation](https://github.com/devcode-naiem/xinubuntu/wiki)

## Credits

### Project Contributors

- **Original Xinu OS**
  - Prof. Douglas Comer and team at Purdue University
  - [Official Xinu Page](https://xinu.cs.purdue.edu)

- **Xinu x86 GUI**
  - Rafael Ignacio Zurita
  - [Source Repository](https://github.com/zrafa/xinu-x86-gui)

- **Xinubuntu Container**
  - Devcode Naiem
  - [GitHub Profile](https://github.com/devcode-naiem)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Engineered with precision by [Devcode Naiem](https://github.com/devcode-naiem)**

⭐ If you find this project valuable, please consider giving it a star!

[Report Bug](https://github.com/devcode-naiem/xinubuntu/issues) • 
[Request Feature](https://github.com/devcode-naiem/xinubuntu/issues) • 
[Get Support](https://github.com/devcode-naiem/xinubuntu/discussions)

</div>
