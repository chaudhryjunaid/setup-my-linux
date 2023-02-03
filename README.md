# setup-fedora-workstation
An collection of ansible playbooks for setting up your favorite linux distribution.

## Requirements
- ansible
- ssh key setup with github


## Setting up pre-requisites
* Install ansible:
  ```
  sudo dnf install ansible
  OR
  sudo apt install ansible
  ```

* Create an ssh keypair if you don't have one already and ensure that the public key is uploaded to github

* Clone this repo:
  ```
  cd ~
  git clone git@github.com:chaudhryjunaid/setup-my-linux.git
  ```

## Running the playbook

* For a fresh machine, run the complete playbook:
  ```
      cd setup-my-linux
      time ansible-playbook setup-my-linux.yml -K -v
  ```
  The playbook will ask for sudo password and prompt for other information as well in some roles. Please keep an eye on the progress to see if any input is required.
  The -K flag is required so that the playbook asks for sudo password which is required for many tasks.

* If you already have a setup and want to execute/reset only part of the configuration done by this repo, please use the `--tags` or `--skip-tags` options:
  ```
      cd setup-my-linux
      time ansible-playbook setup-my-linux.yml -K --verbose --tags "zsh,settings"
  ```

* Following tags are supported:
  * apps
  * zsh
  * dotfiles
  * vim
  * settings
  * nodejs

## Additional manual configuration required

* If you use nvim, please execute the following to install specified plugins:
  ```
  nvim +PlugInstall +qall
  nvim '+PlugClean!' +qall
  ```
  Please note that neovim is the preferred editor in the installed setup.


* Additionally, you will need to set your terminal font to a powerline font for vim to display special characters nicely.

## Further setup required
* TODO: If you use docker or podman for running containers on linux, this is not setup using this playbook. This is a deliberate omission to allow you to select your container tools yourself.

* TODO: This playbook does not yet setup Slack and Zoom applications whose setup is left to be manual. 

## Feedback
* Please create an issue in this repository if you encounter a bug and I will try to fix it or get back to you soon enough.
