# AutoFirma Flatpak

This repository can build AutoFirma for Flatpak, the electronic signature application from the Spanish Government.

> [!WARNING]
> This is a community package and is **not officially supported by the Spanish Government**.

[Leer en español](README.es.md)


## Objective

The primary goal of this project is to package AutoFirma for Linux as a Flatpak, with the ultimate objective of **submitting it to [Flathub][flathub]** for easy distribution and installation.


## Prerequisites

To build this Flatpak, you need to have `flatpak` and `flatpak-builder` installed on your system.

The command `bsdunzip` must also be available. It might be provided by `libarchive` in your distribution.


### Install the Freedesktop Runtime and SDK

This application uses the Freedesktop 25.08 runtime. Add the Flathub repository and install the required runtime and SDK with the following commands:

```bash
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install --user flathub org.freedesktop.Platform//25.08 org.freedesktop.Sdk//25.08
```


## Local Installation

Once the prerequisites are met, you can build and install the Flatpak locally.

**Clone this repository:**
```bash
git clone https://github.com/ivangj/autofirma-flatpak.git
cd autofirma-flatpak
```

**Build and install the application**. Use `flatpak-builder` to build the application and install it for the current user.
```bash
flatpak-builder --force-clean --user --install build-dir es.gob.AutofirmaClient.yaml
```

**Run the application**. You can now run AutoFirma using
```bash
flatpak run es.gob.AutofirmaClient
```


## Future Improvements & To-Do List

This is an ongoing project. Help with the following tasks is greatly appreciated:

- **Build from Source:** Currently, the package extracts a pre-compiled official `.deb` file. The goal is to compile AutoFirma from source instead. A good reference is the [work done by user 'aruiz' on GitHub][aruiz-repo].
- **Improved Icon:** Replace the icon contained in the official `.deb` with a higher quality version.
- **Manifest Cleanup:** Review the build manifest for any potential cleanup operations or optimizations.
- **Metainfo Translations:** Translate the `metainfo.xml` file to make the app description available in English, Spanish, Catalan, Galician, Basque, and potentially Esperanto.
- Install Huella Digital plugin


## Fun Ideas to Explore

- **Automated Releases:** Set up automated GitHub Actions to build and publish the [`flatpak` single-file bundle][flatpak-bundles].


## Links and References

- [**Official Autofirma website**][official-website]
- [**Official AutoFirma Client Repository**][official-repo]
- [**Unofficial Build Attempt**][aruiz-repo]
- [**Flatpak Documentation**][flatpak-docs]
- [**Flathub**][flathub]

[official-website]: https://firmaelectronica.gob.es
[official-repo]: https://github.com/ctt-gob-es/clienteafirma
[aruiz-repo]: https://github.com/aruiz/autofirma-flatpak
[flatpak-docs]: https://docs.flatpak.org
[flathub]: https://flathub.org
[flatpak-bundles]: https://docs.flatpak.org/en/latest/single-file-bundles.html
