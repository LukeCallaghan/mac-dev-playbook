# Customiesd Mac Development Ansible Playbook

Thanks to Jeef Geerling for his original work in creating this.

This playbook installs and configures most of the software I use on my Mac. I still have a few manual installation steps, but at least it's all documented here so that I can remember how to set up my system when I get a new one, or blow away my current one.

## Prepare the system

  1. Ensure Apple's command line tools are installed - `xcode-select --install`
  2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html):

     1. Run the following command to add Python 3 to your $PATH: `export PATH="$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"`
     2. Upgrade Pip: `sudo pip3 install --upgrade pip`
     3. Install Ansible: `pip3 install ansible`

  3. Copy SSH and GPG keys from backup.

     1. Ensure permissions are set correctly for SSH keys - `chmod 600 ~/.ssh/id*`
     2. Ensure permissions are set correctly for GPG keys - `chown -R $(whoami) ~/.gnupg/ && chmod 600 ~/.gnupg/* && chmod 700 ~/.gnupg`

## Installation

  1. Clone or download this repository to your local drive.
  2. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
  3. Run `ansible-playbook main.yml --ask-become-pass` inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.

### Things that still need to be done manually

It's my hope that I can get the rest of these things wrapped up into Ansible playbooks soon, but for now, these steps need to be completed manually (assuming you already have Xcode and Ansible installed, and have run this playbook).

  1. Installation of OhMyZSH - `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
  2. Installation of OneDrive
  3. Sync of SharePoint Online

## Author

This project was forked from [Jeff Geerling](https://www.jeffgeerling.com/) (originally inspired by [MWGriffin/ansible-playbooks](https://github.com/MWGriffin/ansible-playbooks)).