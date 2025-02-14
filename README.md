# C2SM Git Courses

## Git Course for Beginners
The folder [beginner](beginner) contains the exercises for the C2SM Git Workshop "Git for Beginners".

## Git Course for Advanced
The folder [advanced](advanced) contains the exercises for the C2SM Git Workshop "Git for Advanced".

## Getting Started

To run this course on your computer, the following things need to be set up:
1. [Git](#1-installing-git-on-your-computer)
2. [Python and JupyterLab](#2-creating-a-github-account-and-ssh-key) (only for beginner course)
4. [SSH key linked to your GitHub account](#3-installing-python-and-jupyterlab)


### 1. Installing Git on your Computer

> **_Important note:_**  You must have at least Git 2.28 (released 27 July 2020) installed.
> You can check your Git version by typing `git --version` in your terminal.

**Mac and Linux users:** To install Git on your computer, please follow the instructions to [Install Git on Mac](https://github.com/git-guides/install-git#install-git-on-mac) or [Install Git on Linux](https://github.com/git-guides/install-git#install-git-on-linux)

**Windows users:** We recommend you to follow the instructions below to install Ubuntu and then follow the [Install Git on Linux](https://github.com/git-guides/install-git#install-git-on-linux) instruction.
<details>
<summary>Instructions for Windows Users</summary>
<br>

We recommend to install the Windows Subsystem for Linux 2 (WSL2). Using Git with WSL2 provides a better terminal experience for Windows users. With WSL2, you can access a Linux terminal directly from Windows, which makes it easier to work with Git commands and other Linux-based tools. This also allows for more flexibility in managing and running scripts, as well as better compatibility with Linux-based workflows. Additionally, WSL2 provides a more secure environment for Git operations by isolating them from the Windows operating system.

#### Setting up WSL2

1. Enable the Windows Subsystem for Linux (WSL) feature on your Windows machine by following the steps [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
2. Install a Linux distribution of your choice from the Microsoft Store. We recommend using Ubuntu 22.04.2 LTS.
3. Open the Start menu and search for "Ubuntu" to launch the distribution.
4. Follow the prompts to set up a username and password for the Ubuntu distribution.

Congratulations! You have now an Ubuntu environment and can work in the same way as on a Linux machine.
</details>

### 2. Creating a GitHub Account and SSH key

Having a GitHub account allows you to collaborate on open-source projects and store your own code in the cloud. With an SSH key, you can securely connect to GitHub without having to enter your username and password every time you push or pull code, which makes the process faster and more convenient. It also adds an extra layer of security to protect your GitHub account from unauthorized access.

#### Instructions

- [Create your own GitHub account](https://github.com/) (if not yet available)
- [Generate an SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
- [Add your SSH key to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).


### 3. Installing Python and JupyterLab
To install Python, we recommend the [instructions from realpython](https://realpython.com/installing-python/),
but of course many other instructions will do as well.

For the beginners course, you also need some non-standard python packages, namely:
   - jupyterlab
   - bash_kernel

To install these two packages, run the following commands in your terminal:
```bash
# Clone this Git repository
git clone git@github.com:C2SM/git-course.git
```

```bash
# Navigate into the cloned repository
cd git-course
```

```bash
# Create a new Python virtual environment named "git-course_env"
python -m venv git-course_env
```

```bash
# Activate the newly created virtual environment
source git-course_env/bin/activate 
```

```bash
# Install the required Python packages specified in the "requirements.txt" file
pip install -r requirements.txt 
```

On some machines an extra step is required:
```bash
python -m bash_kernel.install
```

To be able to access directories outside of the *git-course* repository in JupyterLab, you need to navigate out of the repository BEFORE launching JupyterLab:
```
cd ..
```

Finally, you can start with the exercises by running:
```
jupyter lab
```
This command will open the JupyterLab interface in your browser.
If it does not open automatically, you will need to copy and paste the URL manually.
In this case, please follow the instructions on your terminal.

If you are note able to start JupyterLab for some reason, you can try to launch a Jupyter Notebook, which provides a simpler user interface:
```
jupyter notebook
```

**Have fun!**

