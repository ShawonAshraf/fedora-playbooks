# fedora-playbooks

Fedora post installation steps automated with ansible. 

## Usage

First install ansible via pip

```bash
sudo dnf install python3-pip -y
pip install ansible
````

Then run the playbooks.

```bash
# will ask you for your password to become sudo
ansible-playbook -i localhost, --connection=local -K playbook.yml
```
