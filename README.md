# fedora-playbooks

Fedora post installation steps automated with ansible. 

## Usage

First install ansible via pip

```bash
sudo dnf install python3-pip python3-libdnf5 -y
pip install ansible
````

Then run the playbooks.

> [!NOTE]
> Currently the `target_user` variable inside the playbook is hardcoded, 
> so you'll have to replace it with your username.

```bash
# will ask you for your password to become sudo
ansible-playbook -i localhost, --connection=local -K playbook.yml
```


