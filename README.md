## Instructions and notes for end to end data science project with deployment 


reference: https://github.com/krishnaik06/mlproject/tree/main 

resource: https://www.youtube.com/playlist?list=PLZoTAELRMXVPS-dOaVbAux22vzqdgoGhG

Here's a summary of the key steps discussed in the provided sources, presented in bullet points:


*   **GitHub Setup and Synchronization**:
    *   **Create a new GitHub repository** (e.g., "mlprojects") and keep it public for sharing.

    *   **Initialize a Git repository** in your local project folder by opening a terminal in VS Code and typing `git init`.
    *   **Create a `README.md` file** in your project directory to describe the project.
    *   **Add the `README.md` file to Git** using `git add README.md`.
    *   **Commit the `README.md` file** with a message like "first commit" using `git commit -m "first commit"`.
    *   **Check out your branch to `main`** using `git branch -M main`.
    *   **Add the remote origin** to link your local repository with the GitHub repository using `git remote add origin <GitHub_repository_URL>`.
    *   **Configure your Git global settings** (username and email) if doing this for the first time, using `git config --global user.email "your_email@example.com"` and `git config --global user.name "Your Name"`.
    *   **Push the committed changes to GitHub** using `git push -u origin main`.
    *   **Create a `.gitignore` file** (e.g., for Python) to prevent certain files (like environment files, e.g., `venv`) from being committed to GitHub.
    *   **Pull updates from GitHub** (e.g., after committing `.gitignore` from the GitHub UI) using `git pull` to sync your local repository.

*   **New Environment Creation**:
    *   From the Anaconda prompt or VS Code terminal, create a **new environment within your project folder** using `conda create -p venv python=3.8 -y`.
    *   **Activate the newly created environment** using `conda activate venv`. This isolates your project's packages within its folder, which is good practice.
    
*   **Setting up `setup.py` and `requirements.txt`**:
    *   Create two new files in the root of your project: **`setup.py`** and **`requirements.txt`**.
    *   **`requirements.txt`** will list all necessary packages for your project (e.g., `pandas`, `numpy`, `seaborn`), with one package per line.
    *   **`setup.py`** is crucial for **building your machine learning application as a package** that can be installed (e.g., via `pip install`) and even deployed to platforms like PyPI.
    *   **Inside `setup.py`**:
        *   Import `find_packages` and `setup` from `setuptools`.
        *   Define metadata for your project using the `setup()` function, including `name` (e.g., `mlproject`), `version` (e.g., `0.0.1`), `author`, `author_email`.
        *   Use `find_packages()` to automatically discover all packages within your project.
        *   Specify `install_requires` to list the packages needed, though this will be dynamically populated from `requirements.txt`.
        *   Define a helper function `get_requirements(file_path: str) -> list[str]` to read packages from `requirements.txt`. This function handles newline characters (`\n`) and **removes the `-e .` entry** before returning the list of requirements.
    *   **Package Structure (`__init__.py`)**: To make a folder (e.g., `src` for source code) behave as a package that `find_packages` can discover, create an **`__init__.py` file inside it** (e.g., `src/__init__.py`). Any new sub-folders that should also behave as packages will need their own `__init__.py` file.
*   **Installation and Package Building**:
    *   Add **`-e .`** to your `requirements.txt` file. This tells `pip install` to **trigger `setup.py` and install your project in "editable" mode**, meaning changes to your source code are immediately reflected without reinstallation.
    *   Run `pip install -r requirements.txt` in your activated environment. This will install all listed packages and, due to `-e .`, also build your ML project as a package. You'll see an `mlproject.egg-info` folder indicating successful package installation.
*   **Final Git Commit and Push**:
    *   Add all new files (e.g., `setup.py`, `requirements.txt`, `src` folder) to Git using `git add .`.
    *   Commit the changes with a descriptive message like "setup.py and requirement setup" using `git commit -m "setup.py and requirement setup"`.
    *   Push the committed changes to the GitHub main branch using `git push -u origin main`.

    after installing requimrements.txt a folder will be created that includes the package documents in my case its called Test_repo.egg-info .. this is due to the setup.py file. 
    we can deploy these packages anywhere if we deploy it in pip




   
