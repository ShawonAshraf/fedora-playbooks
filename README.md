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


## What's not covered

| Topic | Reason |
|---|---|
| CUDA Toolkit installation | CUDA Toolkit installation. Check [RPMFusion/Howto/CUDA](https://rpmfusion.org/Howto/CUDA) and [Nvidia CUDA Toolkit Downloads](https://developer.nvidia.com/cuda-downloads). Also ensure that you install a compatible gcc compiler since the system version is always ahead by a version or two. |
| Secure Boot Setup | Secure Boot Setup. Check [RPMFusion/Howto/Secureboot](https://rpmfusion.org/Howto/Secure%20Boot). |
| Gnome shell extensions | Gnome shell extensions. Use your own. |
| VPNs and other email clients | VPNs and other email clients. Same as above. |


> [!NOTE]
> If you're using a new gen Thinkpad (e.g. P1 Gen 7 or newer), read [OMGLinux guide](https://www.omglinux.com/boot-linux-modern-lenovo-thinkpads-bios-setting/) on how to enable secure boot for non-Microsoft operating systems in the bios.
