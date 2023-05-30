# **Ansible Development Environment Setup**
----

This Ansible role is used to pull a remote copy of an Ansible playbook on a managed node that installs the packages, features, and configuration files required for my development environment from a source repository. This setup inverts the default push architecture of Ansible into a pull architecture, which offers near-limitless scaling potential.

### **Features**
---
This Ansible playbook performs the following essential tasks:

Creating a New User and Granting Root Privileges: Enhance security and control by creating a new user and assigning it root privileges.

Keeping Apt Packages Up to Date: Ensure your system is up to date by updating and upgrading apt packages.

Configuring zsh as the Default Shell: Install and configure zsh as the default shell, providing advanced features and customization options.

Installing [oh-my-zsh](https://github.com/ohmyzsh/) Plugins and [P10K](https://github.com/romkatv/powerlevel10k) Theme: Enhance your shell experience by installing popular oh-my-zsh plugins and the visually appealing P10K theme.

Installing [pyenv](https://github.com/pyenv/pyenv) and pyenv-virtualenv Required Python Versions: Install pyenv, a flexible Python version management tool, and the specified Python interpreter versions.

Setting Global Environment with Python Versions: Set the global environment to use the selected Python interpreter versions for consistent Python development.

Managing Python Packages with pip: Install additional Python packages using the pip package manager.

Pulling the dotfile Repository from [GitHub](https://github.com/santiagopereda/dotfiles): Sync your configuration files by pulling the dotfile repository from GitHub.

Creating Symlinks to the ~/.config Directory: Organize your configuration files by creating symbolic links to the `~/.config` directory.

## **Requirements**
---
- [Ubuntu](https://www.ubuntu.com) or [Debian](https://www.debian.org) Linux
- Bash shell
- [Ansible](https://www.ansible.com) 2.8 or newer
- [Python](https://www.python.org/) 3.7 or newer as required by Ansible

### Ubuntu

This Ansible Playbook has been tested on the following Linux releases:

-  [Ubuntu 22.04.2 LTS](https://ubuntu.com/blog/ubuntu-22-04-lts-whats-new-linux-desktop)

### Ubuntu on WSL

I've used this playbook to install packages on Ubuntu running on Windows Subsystem for Linux on Windows 11.

## **Installation Instructions**
---
To run the playbook, ensure that you have the latest version of Ansible installed. Please follow the steps below:

###  Installing Ansible

Ansible is an agentless automation tool that you install on a single host (referred to as the control node). From the control node, Ansible can manage an entire fleet of machines and other devices (referred to as managed nodes) remotely with SSH, Powershell remoting, and numerous other transports, all from a simple command-line interface with no databases or daemons required.

To run the playbook, ensure that you have the latest version of Ansible installed. Please follow the steps below:

Update and Upgrade packages.

```bash
sudo apt update && sudo apt upgrade
```

Verify whether `pip` is already installed for your preferred Python.

```bash
python3 -m pip -V
```

If all is well, you should see something like the following:

```bash
python3 -m pip -V
pip 21.0.1 from /usr/lib/python3.9/site-packages/pip (python 3.9)
```

Use `pip` in your selected Python environment to install the Ansible package of your choice for the current user:

```bash
python3 -m pip install --user ansible
```

You can test that Ansible is installed correctly by checking the version:

```bash
ansible --version
```

If you see an error, See the Ansible documentation on [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) for more information.


##  Running the playbook

To install and update packages, execute the following command as the root user. This command will pull the Ansible playbook repository from GitHub and execute all the tasks in order:

```bash
sudo ansible-pull -U https://github.com/santiagopereda/ansible_desktop.git
```

This command performs a "pull" operation, retrieving the latest version of the Ansible playbook from the specified GitHub repository. It then applies the playbook locally, executing all the defined tasks sequentially. The playbook contains instructions to install and configure various packages, set up the development environment, and perform any necessary configurations.

Run the command with appropriate privileges,  administrative access is required to install and update packages.



## License
---
MIT

## Acknowledgments
---
The role used for installing pyenv and python versions were referenced from [markosamuli](https://github.com/markosamuli/ansible-pyenv) 

