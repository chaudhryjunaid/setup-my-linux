# setup-fedora-workstation
An ansible playbook for setting up a development environment on Fedora Workstation

## Requirements
Tested on Fedora 35

## Setting up pre-requisites
* Install ansible:
  ```
  sudo dnf install ansible
  ```

* Clone this repo:
  ```
  cd ~
  git clone https://github.com/chaudhryjunaid/setup-fedora-workstation.git
  ```

## Running the playbook

* For a fresh machine, run the complete playbook:
  ```
      cd setup-fedora-workstation
      time ansible-playbook fedora-setup.yml -K -v
  ```
  The playbook will ask for sudo password and prompt for other information as well in some roles. Please keep an eye on the progress to see if any input is required.
  The -K flag is required so that the playbook asks for sudo password which is required for many tasks.

* If you already have a setup and want to execute/reset only part of the configuration done by this repo, please use the `--tags` or `--skip-tags` options:
  ```
      cd setup-fedora-workstation
      time ansible-playbook fedora-setup.yml -K --verbose --tags "zsh,system"
  ```
* Following tags are supported:
  * dnf
  * zsh
  * dotfiles
  * vim
  * system
  * folders
  * ssh
  * nodejs

## Additional manual configuration required

* If you use vim, you will need to execute the following commands at the command-line:
  ```
  vim +PlugInstall +qall
  vim '+PlugClean!' +qall
  ```

* If you use nvim, please execute the following to install completion servers:
  ```
  nvim +'CocInstall' +qall
  ```

* Additionally, you will need to set your terminal font to a powerline font for vim to display special characters nicely.

## Further setup required
* TODO: If you use docker or podman for running containers on linux, this is not setup using this playbook. This is a deliberate omission to allow you to select your container tools yourself.

* TODO: This playbook does not yet setup Slack and Zoom applications whose setup is left to be manual. 

## Feedback
* Please create an issue in this repository if you encounter a bug and I will try to fix it or get back to you soon enough.
