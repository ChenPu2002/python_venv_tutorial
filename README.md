# 🐍 Python Virtual Environment Management Guide

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/yourusername/repo/graphs/commit-activity)

> A comprehensive guide to managing Python virtual environments using **Conda**, **Poetry**, and **uv** - three powerful tools for dependency management and environment isolation.

## 📚 Table of Contents

- [🎯 Overview](#-overview)
- [🔧 Tool Comparison](#-tool-comparison)
- [🐍 Conda](#-conda)
  - [Installation](#installation)
  - [Environment Management](#environment-management)
  - [Package Management](#package-management)
- [📝 Poetry](#-poetry)
  - [Installation](#installation-1)
  - [Project Management](#project-management)
  - [Dependency Management](#dependency-management)
- [⚡ uv](#-uv)
  - [Installation](#installation-2)
  - [Project Setup](#project-setup)
  - [Package Management](#package-management-1)
- [❓ FAQ](#-faq)
- [📖 Additional Resources](#-additional-resources)

## 🎯 Overview

Virtual environments are essential for Python development, allowing you to:
- 🔒 **Isolate dependencies** between projects
- 🎯 **Manage different Python versions**
- 📦 **Ensure reproducible builds**
- 🚀 **Avoid dependency conflicts**

This guide covers three popular tools: **Conda** (scientific computing), **Poetry** (modern dependency management), and **uv** (ultra-fast package manager).

## 🔧 Tool Comparison

| Feature | Conda | Poetry | uv |
|---------|--------|---------|-----|
| **Speed** | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Python Version Management** | ✅ | ❌ | ✅ |
| **Non-Python Packages** | ✅ | ❌ | ❌ |
| **Lock Files** | ❌ | ✅ | ✅ |
| **Scientific Computing** | ✅ | ⭐⭐ | ⭐⭐ |
| **Learning Curve** | Easy | Medium | Easy |
| **Cross-platform** | ✅ | ✅ | ✅ |

## 🐍 Conda

Conda is a powerful package and environment management tool, particularly popular in scientific computing and data science.

### Installation

Choose between two distributions:

#### 📦 Anaconda (Full Distribution)
- **Size**: ~3GB
- **Includes**: 250+ pre-installed packages
- **Best for**: Data science, machine learning
- **Download**: [Anaconda Downloads](https://www.anaconda.com/products/distribution)

#### 📦 Miniconda (Minimal Distribution)
- **Size**: ~400MB
- **Includes**: Only Conda and Python
- **Best for**: Custom installations, minimal footprint
- **Download**: [Miniconda Downloads](https://docs.conda.io/en/latest/miniconda.html)

#### Installation Steps

1. **Download the installer** from the links above
2. **Run the installer**:
   ```bash
   # Windows
   # Double-click the .exe file
   
   # macOS/Linux
   bash Anaconda3-latest-Linux-x86_64.sh
   # or
   bash Miniconda3-latest-Linux-x86_64.sh
   ```
3. **Restart your terminal** or run:
   ```bash
   source ~/.bashrc  # Linux
   source ~/.zshrc   # macOS with zsh
   ```

### Environment Management

#### 🆕 Creating Environments

```bash
# Create with specific Python version
conda create --name myproject python=3.9

# Create with multiple packages
conda create --name datascience python=3.9 numpy pandas matplotlib

# Create from environment file
conda env create -f environment.yml
```

#### 📋 Listing Environments

```bash
# List all environments
conda env list

# Alternative command
conda info --envs
```

#### 🔄 Activating/Deactivating

```bash
# Activate environment
conda activate myproject

# Deactivate current environment
conda deactivate
```

#### 🗑️ Removing Environments

```bash
# Remove environment
conda env remove --name myproject

# Remove environment and all packages
conda remove --name myproject --all
```

#### 📤 Exporting Environments

```bash
# Export to YAML file
conda env export > environment.yml

# Export only explicitly installed packages
conda env export --from-history > environment.yml
```

### Package Management

#### 📦 Installing Packages

```bash
# Install single package
conda install numpy

# Install multiple packages
conda install numpy pandas matplotlib

# Install from specific channel
conda install -c conda-forge scikit-learn

# Install specific version
conda install numpy=1.21.0
```

#### 📋 Package Information

```bash
# List installed packages
conda list

# Search for packages
conda search numpy

# Show package info
conda info numpy
```

#### 🔄 Updating Packages

```bash
# Update specific package
conda update numpy

# Update all packages
conda update --all

# Update conda itself
conda update conda
```

#### 🗑️ Removing Packages

```bash
# Remove package
conda remove numpy

# Remove multiple packages
conda remove numpy pandas matplotlib
```

## 📝 Poetry

Poetry is a modern dependency management and packaging tool that aims to bring the best of all packaging worlds to the Python community.

### Installation

#### 📥 Official Installer (Recommended)

```bash
# Unix/macOS
curl -sSL https://install.python-poetry.org | python3 -

# Windows (PowerShell)
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -
```

#### 📦 Alternative Methods

```bash
# Using pip (not recommended for global installation)
pip install poetry

# Using conda
conda install poetry

# Using homebrew (macOS)
brew install poetry
```

#### ⚙️ Configuration

```bash
# Configure Poetry to create virtual environments in project directory
poetry config virtualenvs.in-project true

# Check configuration
poetry config --list
```

### Project Management

#### 🆕 Creating New Projects

```bash
# Create new project
poetry new my-project

# Initialize existing project
cd existing-project
poetry init
```

#### 📁 Project Structure

```
my-project/
├── pyproject.toml      # Project configuration
├── README.md
├── my_project/         # Source code
│   └── __init__.py
└── tests/              # Tests
    └── __init__.py
```

#### 🔄 Environment Management

```bash
# Create virtual environment and install dependencies
poetry install

# Activate virtual environment
poetry shell

# Run commands in virtual environment
poetry run python script.py
poetry run pytest
```

### Dependency Management

#### 📦 Adding Dependencies

```bash
# Add production dependency
poetry add requests

# Add development dependency
poetry add --group dev pytest

# Add with version constraint
poetry add "django>=3.2,<4.0"

# Add from git repository
poetry add git+https://github.com/user/repo.git
```

#### 📋 Dependency Information

```bash
# Show dependencies
poetry show

# Show dependency tree
poetry show --tree

# Show outdated packages
poetry show --outdated
```

#### 🔄 Updating Dependencies

```bash
# Update all dependencies
poetry update

# Update specific package
poetry update requests

# Update within constraints
poetry update --dry-run
```

#### 🗑️ Removing Dependencies

```bash
# Remove dependency
poetry remove requests

# Remove development dependency
poetry remove --group dev pytest
```

#### 🔒 Lock File Management

```bash
# Generate lock file
poetry lock

# Install from lock file
poetry install --frozen

# Export requirements.txt
poetry export -f requirements.txt --output requirements.txt
```

## ⚡ uv

uv is an extremely fast Python package manager and project manager written in Rust, designed as a drop-in replacement for pip, pip-tools, pipx, poetry, pyenv, and more.

### Installation

#### 📥 Quick Installation

```bash
# Unix/macOS/Windows (WSL)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# Using pip
pip install uv

# Using homebrew (macOS)
brew install uv

# Using conda
conda install -c conda-forge uv
```

#### ✅ Verify Installation

```bash
uv --version
```

### Project Setup

#### 🆕 Creating Projects

```bash
# Initialize new project
uv init my-project
cd my-project

# Initialize in existing directory
uv init

# Initialize with specific Python version
uv init --python 3.11
```

#### 📁 Project Structure

```
my-project/
├── pyproject.toml      # Project configuration
├── uv.lock            # Lock file
├── README.md
├── src/
│   └── my_project/
│       └── __init__.py
└── tests/
```

#### 🐍 Python Version Management

```bash
# Install Python version
uv python install 3.11

# List available Python versions
uv python list

# Use specific Python version
uv python use 3.11
```

### Package Management

#### 📦 Adding Dependencies

```bash
# Add package
uv add requests

# Add development dependency
uv add --dev pytest

# Add with version constraint
uv add "django>=3.2,<4.0"

# Add from git
uv add git+https://github.com/user/repo.git

# Add from PyPI with extras
uv add "fastapi[all]"
```

#### 📋 Package Information

```bash
# List dependencies
uv tree

# Show installed packages
uv pip list

# Check for outdated packages
uv pip list --outdated
```

#### 🔄 Dependency Management

```bash
# Update all dependencies
uv lock --upgrade

# Sync environment with lock file
uv sync

# Install dependencies
uv pip install -r pyproject.toml
```

#### 🗑️ Removing Dependencies

```bash
# Remove package
uv remove requests

# Remove development dependency
uv remove --dev pytest
```

#### 🚀 Running Commands

```bash
# Run Python script
uv run python script.py

# Run module
uv run -m pytest

# Run with specific Python version
uv run --python 3.11 python script.py

# Execute one-off commands
uvx ruff check
uvx black .
uvx mypy src/
```

#### 🔒 Lock File Operations

```bash
# Generate lock file
uv lock

# Update lock file
uv lock --upgrade

# Install from lock file
uv sync --frozen
```

## ❓ FAQ

### General Questions

<details>
<summary><strong>Which tool should I choose?</strong></summary>

- **Choose Conda if**: You work with scientific computing, need non-Python packages, or want an all-in-one solution
- **Choose Poetry if**: You want modern Python packaging with excellent dependency resolution and lock files
- **Choose uv if**: You prioritize speed and want a modern, fast alternative to traditional tools

</details>

<details>
<summary><strong>Can I use multiple tools together?</strong></summary>

Yes, but be careful:
- Conda + Poetry: Use conda for environment, poetry for dependency management
- uv + Poetry: Not recommended as both manage dependencies
- Always activate the correct environment before using tools

</details>

<details>
<summary><strong>How do I migrate between tools?</strong></summary>

**From Conda to Poetry**:
```bash
conda env export > environment.yml
poetry init
# Manually add dependencies from environment.yml
```

**From Poetry to uv**:
```bash
uv init
uv add $(poetry show --only=main | awk '{print $1}')
```

**From requirements.txt to any tool**:
```bash
# Conda
conda create --name myenv --file requirements.txt

# Poetry
poetry add $(cat requirements.txt)

# uv
uv add -r requirements.txt
```

</details>

### Conda Specific

<details>
<summary><strong>Conda is slow. How can I speed it up?</strong></summary>

1. **Use mamba** (faster conda replacement):
   ```bash
   conda install mamba -c conda-forge
   mamba install package_name
   ```

2. **Use libmamba solver**:
   ```bash
   conda install -n base conda-libmamba-solver
   conda config --set solver libmamba
   ```

3. **Configure channels**:
   ```bash
   conda config --add channels conda-forge
   conda config --set channel_priority strict
   ```

</details>

<details>
<summary><strong>How do I fix conda environment activation issues?</strong></summary>

```bash
# Re-initialize conda
conda init

# Fix PATH issues
echo 'export PATH="$HOME/anaconda3/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# Reset conda configuration
conda config --remove-key channels
```

</details>

### Poetry Specific

<details>
<summary><strong>Poetry install is hanging. What should I do?</strong></summary>

1. **Clear cache**:
   ```bash
   poetry cache clear pypi --all
   ```

2. **Use different installer**:
   ```bash
   poetry config installer.modern-installation false
   ```

3. **Increase timeout**:
   ```bash
   poetry config installer.timeout 600
   ```

</details>

<details>
<summary><strong>How do I use Poetry with different Python versions?</strong></summary>

```bash
# Specify Python version in pyproject.toml
[tool.poetry.dependencies]
python = "^3.9"

# Use with pyenv
poetry env use $(pyenv which python)

# Use specific Python executable
poetry env use /usr/bin/python3.9
```

</details>

### uv Specific

<details>
<summary><strong>How do I use uv with existing projects?</strong></summary>

```bash
# In project with requirements.txt
uv init
uv add -r requirements.txt

# In project with setup.py
uv init
uv add -e .

# In Poetry project
uv init
# Copy dependencies from pyproject.toml manually
```

</details>

<details>
<summary><strong>uv is not finding my Python installation. What should I do?</strong></summary>

```bash
# Install Python through uv
uv python install 3.11

# List available Python installations
uv python list

# Use specific Python
uv python use 3.11

# Set Python explicitly
uv init --python /usr/bin/python3.11
```

</details>

## 📖 Additional Resources

### Official Documentation
- 📚 [Conda Documentation](https://docs.conda.io/projects/conda/en/latest/)
- 📚 [Poetry Documentation](https://python-poetry.org/docs/)
- 📚 [uv Documentation](https://docs.astral.sh/uv/)

### Cheat Sheets
- 📋 [Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
- 📋 [Poetry Commands Reference](https://python-poetry.org/docs/cli/)
- 📋 [uv Command Reference](https://docs.astral.sh/uv/reference/)

### Community Resources
- 💬 [Python Packaging Discord](https://discord.gg/python)
- 💬 [Conda Community](https://community.anaconda.cloud/)
- 🐛 [Poetry Issues](https://github.com/python-poetry/poetry/issues)
- 🐛 [uv Issues](https://github.com/astral-sh/uv/issues)

### Best Practices
- 🎯 [Python Packaging Best Practices](https://packaging.python.org/guides/)
- 🎯 [Virtual Environment Best Practices](https://docs.python.org/3/tutorial/venv.html)
- 🎯 [Dependency Management Strategies](https://realpython.com/dependency-management-python/)

---

<div align="center">

**Happy Python Development! 🐍✨**

*Found this guide helpful? Give it a ⭐ and share with fellow developers!*

</div>