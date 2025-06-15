# duarte-blue &nbsp; [![bluebuild build badge](https://github.com/tduarte/duarte-blue/actions/workflows/build.yml/badge.svg)](https://github.com/tduarte/duarte-blue/actions/workflows/build.yml)

## About

**duarte-blue** is a gaming-focused Universal Blue image that delivers the ultimate Linux gaming and desktop experience out of the box. Built on top of Bluefin (Intel/AMD) or Bazzite GNOME (NVIDIA), this custom image comes in two variants and is designed for gamers and users who want a visually stunning, high-performance system without the hassle of manual configuration.

### What's Included

🎮 **Gaming Ready**
- Steam and Lutris pre-configured for gaming
- GPU drivers (NVIDIA or Intel/AMD depending on variant)
- And all other improvements provided by Bazzite

🌐 **Modern Applications**
- Zen Browser (replaces Firefox)
- Native Discord with hardware acceleration
- Native 1Password for better system integration
- Native Zed editor for development work and terminal support

✨ **Visual Polish**
- Bibata Modern Ice cursor theme
- WhiteSur Purple icon theme
- Organized app folders and favorites

## Installation

> [!WARNING]
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

Choose the appropriate variant for your hardware:

### Rebase

To rebase an existing atomic Fedora installation to the Intel/AMD build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/tduarte/duarte-blue:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/tduarte/duarte-blue:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

### NVIDIA variant

To rebase an existing atomic Fedora installation to the NVIDIA build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/tduarte/duarte-blue-nvidia:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/tduarte/duarte-blue-nvidia:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in the respective `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
# For Intel/AMD variant
cosign verify --key cosign.pub ghcr.io/tduarte/duarte-blue

# For NVIDIA variant
cosign verify --key cosign.pub ghcr.io/tduarte/duarte-blue-nvidia
```
