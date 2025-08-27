# fedora-playbooks

Fedora post installation steps automated with ansible.

## playbooks

The repository ships a set of focused Ansible playbooks; use the table below to see each playbook's purpose.

| playbook | function |
|---|---|
| `playbook.yml` | Top-level aggregator that imports and runs the other playbooks. |
| `playbook-starter.yml` | Initial system setup: tweak dnf settings, update the system, and add RPM Fusion repositories and codec support. |
| `playbook-nvidia.yml` | Installs NVIDIA drivers, CUDA-related runtime libraries from RPM Fusion, and GPU monitoring tools. |
| `playbook-utils.yml` | Installs common utilities and tools (power management, system monitors, fetch utilities, font manager, clipboard/tree tools). |
| `playbook-devtools.yml` | Installs development packages and tools, container runtimes (Docker), VS Code, Node/Rust/Python toolchains, and user-level developer utilities. |
| `playbook-flatpaks.yml` | Adds the Flathub remote and installs a curated list of Flatpak applications for the target user. |
| `playbook-media.yml` | Installs multimedia libraries and applications (multimedia group, VLC, MPV, HandBrake). |
| `playbook-gaming.yml` | Installs gaming packages and overlays (Steam, Lutris, MangoHud, gamemode, etc.). |
| `playbook-brave.yml` | Installs the Brave web browser via the Brave install script. |
| `playbook-openbangla.yml` | Installs the OpenBangla keyboard using its install script. |

> [!NOTE]
> If you don't need specific playbooks you can comment them out in the `playbook.yml` file.

## Usage

First install ansible via pip

```bash
sudo dnf install python3-pip python3-libdnf5 -y
pip install ansible
````

Then run the playbooks.

> [!IMPORTANT]
> Currently the `target_user` variable inside the playbook is hardcoded, 
> so you'll have to replace it with your username.

```bash
# will ask you for your password to become sudo
ansible-playbook -i localhost, --connection=local -K playbook.yml
```

## what's not covered

| Topic | Reason |
|---|---|
| CUDA Toolkit installation | Check [RPMFusion/Howto/CUDA](https://rpmfusion.org/Howto/CUDA) and [Nvidia CUDA Toolkit Downloads](https://developer.nvidia.com/cuda-downloads). Also ensure that you install a compatible gcc compiler since the system version is always ahead by a version or two. |
| Secure Boot Setup | Check [RPMFusion/Howto/Secureboot](https://rpmfusion.org/Howto/Secure%20Boot). |
| Gnome shell extensions | Install based on your preferences. |
| VPNs and other email clients | Same as above. |

> [!TIP]
> If you're using a new gen Thinkpad (e.g. P1 Gen 7 or newer), read the [OMGLinux guide](https://www.omglinux.com/boot-linux-modern-lenovo-thinkpads-bios-setting/) on how to enable secure boot for non-Microsoft operating systems in the bios.


> [!TIP]
> If you've a dual gpu laptop (iGPU+dGPU), use the following as the launcher command to run games on the dGPU: `%command% -graphicsadapter=0`




## misc

In Gnome 48 on fedora 42, two finger swipe is enabled in Chrome*, and Firefox. If you use Brave, you will have to edit the `.desktop` entry. 

> [!NOTE]
> Gestures work only in Wayland

```bash
sudo nano /usr/share/applications/brave-browser.desktop

# add the following at the end of each Exec command
--enable-features=TouchpadOverscrollHistoryNavigation 
```


