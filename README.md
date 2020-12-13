# setup-fedora-workstation
An ansible playbook for setting up a development environment on Fedora Workstation

## Requirements
Tested on Fedora 33

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
      time ansible-playbook fedora-setup.yml -v
  ```
  The playbook will ask for sudo password and prompt for other information as well in some roles. Please keep an eye on the progress to see if any input is required.

* If you already have a setup and want to execute/reset only part of the configuration done by this repo, please use the `--tags` or `--skip-tags` options:
  ```
      cd setup-fedora-workstation
      time ansible-playbook fedora-setup.yml --verbose --tags "zsh,terminal,system"
  ```
* Following tags are supported:
  * dnf
  * zsh
  * dotfiles
  * vim
  * system
  * terminal
  * folders
  * ssh
  * nodejs

## Additional manual configuration required

* If you use vim, you will need to execute the following commands at the command-line:
  ```
  vim +PlugInstall +qall
  vim '+PlugClean!' +qall
  ```

* Additionally, you will need to set your terminal font to a powerline font for vim to display special characters nicely.
