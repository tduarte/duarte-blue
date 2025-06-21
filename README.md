# duarte-blue &nbsp; [![bluebuild build badge](https://github.com/tduarte/duarte-blue/actions/workflows/build.yml/badge.svg)](https://github.com/tduarte/duarte-blue/actions/workflows/build.yml)

## About

**duarte-blue** is a gaming-focused Universal Blue image that delivers the ultimate Linux gaming and desktop experience out of the box. Built on top of Bluefin, this custom image comes in two variants and is designed for gamers and users who want a visually stunning, high-performance system without the hassle of manual configuration.

### What's Included

🌐 **Applications & Development**
- [Zen Browser](https://flathub.org/apps/app.zen_browser.zen) (Browser with vertical tabs, based on Firefox)
- Native [Discord](https://discord.com/) with hardware acceleration
- [1Password](https://1password.com/)
- [Zed Editor](https://zed.dev/)
- [Ghostty Terminal](https://ghostty.org/)
- [Alpaca AI](https://flathub.org/apps/com.jeffser.Alpaca) (with [AMD plugin](https://flathub.org/apps/com.jeffser.Alpaca.Plugins.AMD) support)
- [Flatseal](https://flathub.org/apps/com.github.tchx84.Flatseal) for Flatpak permissions
- [GearLever](https://flathub.org/apps/it.mijorus.gearlever) for AppImages

🎮 **Gaming & Entertainment**
- [Steam](https://flathub.org/apps/com.valvesoftware.Steam) and [Lutris](https://flathub.org/apps/net.lutris.Lutris) pre-configured for gaming
- [Heroic Games Launcher](https://flathub.org/apps/com.heroicgameslauncher.hgl) for Epic Games Store integration
- [Cartridges](https://flathub.org/apps/page.kramo.Cartridges) for managing game libraries
- [ProtonPlus](https://flathub.org/apps/com.vysp3r.ProtonPlus) for managing Proton versions
- [AdwSteamGtk](https://flathub.org/apps/io.github.Foldex.AdwSteamGtk) for Steam GTK theming
- [GPU Screen Recorder](https://flathub.org/apps/com.dec05eba.gpu_screen_recorder) (Shadowplay like app)

🛠️ **System Tools & Utilities**
- [Extension Manager](https://flathub.org/apps/com.mattjakeman.ExtensionManager)
- [Blanket](https://flathub.org/apps/com.rafaelmardojai.Blanket)
- [Fragments](https://flathub.org/apps/de.haeckerfelix.Fragments)
- [HandBrake](https://flathub.org/apps/fr.handbrake.ghb)
- [Camera Controls](https://flathub.org/apps/hu.irl.cameractrls)
- [BoxBuddy](https://flathub.org/apps/io.github.dvlv.boxbuddyrs)
- [Resources](https://flathub.org/apps/net.nokyan.Resources)
- [Pods](https://flathub.org/apps/com.github.marhkb.Pods)
- [Refine](https://flathub.org/apps/page.tesk.Refine)
- GPU drivers (NVIDIA or Intel/AMD depending on variant)

🎨 **Visual & Desktop Experience**
- [Bibata cursor themes](https://github.com/ful1e5/Bibata_Cursor)
- [WhiteSur Icons](https://github.com/vinceliuice/WhiteSur-icon-theme)
- GNOME extensions:
  - [Night Theme Switcher](https://extensions.gnome.org/extension/2236/night-theme-switcher/)
  - [Blur my Shell](https://extensions.gnome.org/extension/3193/blur-my-shell/)
  - [AppIndicator and KStatusNotifierItem Support](https://extensions.gnome.org/extension/615/appindicator-support/)
  - [Alphabetical App Grid](https://extensions.gnome.org/extension/4269/alphabetical-app-grid/)
  - [Desktop Icons NG (DING)](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)
  - [Hot Edge](https://extensions.gnome.org/extension/4222/hot-edge/)
  - [Tiling Shell](https://extensions.gnome.org/extension/7065/tiling-shell/)
  - [Gnome 4x UI Improvements](https://extensions.gnome.org/extension/4158/gnome-40-ui-improvements/)
  - [Just Perfection](https://extensions.gnome.org/extension/3843/just-perfection/)

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
