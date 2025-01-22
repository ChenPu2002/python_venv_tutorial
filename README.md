## A Guide to Using Python Venv (including conda, poetry, pipenv and uv)

Conda is a popular package and environment management tool widely used in scientific computing and data science, particularly for handling Python projects. Here's a basic guide on how to use Conda.

## Conda

Conda can be installed as part of the Anaconda or Miniconda distributions:

- **Anaconda**: Includes Conda, Python, and a large collection of pre-installed packages suited for scientific applications.
- **Miniconda**: Includes only Conda and Python, allowing for a lighter installation with the flexibility to install only the packages you need.

### Installation Steps

1. **Download the installer**:
   - For Anaconda, visit [Anaconda Downloads](https://www.anaconda.com/products/distribution)
   - For Miniconda, visit [Miniconda Downloads](https://docs.conda.io/en/latest/miniconda.html)
2. **Run the installer**:
   - On Windows, double-click the downloaded `.exe` file.
   - On macOS and Linux, open a terminal and run the downloaded `.sh` file by typing `bash <filename>.sh`.
3. **Follow the on-screen instructions** to complete the installation.

## Managing Environments

Conda allows you to create isolated environments to manage different project dependencies separately.

### Creating an Environment
```bash
conda create --name myenv python=3.8
```
Creating from yaml file:
```bash
conda env create -f environment.yml
```

### Deleting an Environment

```bash
conda env remove --name gpt
```

### Activating an Environment

```bash
conda activate myenv
```

### Deactivating an Environment

```bash
conda deactivate
```

## Managing Packages

Conda can install, update, and remove packages within an environment.

### Installing a Package

```bash
conda install numpy
```

### Listing Installed Packages

```bash
conda list
```

### Updating a Package

```bash
conda update numpy
```

### Removing a Package

```bash
conda remove numpy
```

## Under Development
## Poetry
## Pipenv
## uv
## FAQ

## Additional Resources

- [Conda Official Documentation](https://docs.conda.io/projects/conda/en/latest/)
- [Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)

Using Conda effectively can simplify package management and help maintain reproducibility of scientific computations. Explore the official documentation for more in-depth information.
