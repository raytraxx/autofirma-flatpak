# AutoFirma Flatpak

Este repositorio permite construir AutoFirma para Flatpak, la aplicación de firma electrónica del Gobierno de España.

> [!WARNING]
> Este es un paquete comunitario y **no está soportado oficialmente por el Gobierno de España**.

[Read in English](README.md)


## Objetivo

El objetivo principal de este proyecto es empaquetar AutoFirma para Linux como Flatpak, con el objetivo final de **enviarlo a [Flathub][flathub]** para facilitar su distribución e instalación.


## Prerrequisitos

Para construir este Flatpak, necesitas tener `flatpak` y `flatpak-builder` instalados en tu sistema.

El comando `bsdunzip` también debe estar disponible. Podría estar incluido en `libarchive` en tu distribución.


### Instalar el Runtime y SDK de Freedesktop

Esta aplicación utiliza el runtime Freedesktop 25.08. Añade el repositorio de Flathub e instala el runtime y SDK requeridos con los siguientes comandos:

```bash
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install --user flathub org.freedesktop.Platform//25.08 org.freedesktop.Sdk//25.08
```


## Instalación Local

Una vez cumplidos los prerrequisitos, puedes construir e instalar el Flatpak localmente.

**Clona este repositorio:**
```bash
git clone https://github.com/ivangj/autofirma-flatpak.git
cd autofirma-flatpak
```

**Construye e instala la aplicación**. Usa `flatpak-builder` para construir la aplicación e instalarla para el usuario actual.
```bash
flatpak-builder --force-clean --user --install build-dir es.gob.AutofirmaClient.yaml
```

**Ejecuta la aplicación**. Ahora puedes ejecutar AutoFirma usando
```bash
flatpak run es.gob.AutofirmaClient
```


## Mejoras Futuras y Lista de Tareas

Este es un proyecto en curso. Se agradece enormemente la ayuda con las siguientes tareas:

- **Compilación desde Fuentes:** Actualmente, el paquete extrae un archivo `.deb` oficial precompilado. El objetivo es compilar AutoFirma desde las fuentes en su lugar. Una buena referencia es el [trabajo realizado por el usuario 'aruiz' en GitHub][aruiz-repo].
- **Icono Mejorado:** Reemplazar el icono contenido en el `.deb` oficial con una versión de mayor calidad.
- **Limpieza del Manifest:** Revisar el manifiesto de construcción para posibles operaciones de limpieza u optimizaciones.
- **Traducciones de Metainfo:** Traducir el archivo `metainfo.xml` para que la descripción de la aplicación esté disponible en inglés, español, catalán, gallego, euskera y potencialmente esperanto.
- Instalar el plugin de Huella Digital.


## Ideas Interesantes para Explorar

- **Lanzamientos Automatizados:** Configurar GitHub Actions automatizadas para construir y publicar el [paquete de archivo único `flatpak`][flatpak-bundles].


## Enlaces y Referencias

- [**Sitio web oficial de Autofirma**][official-website]
- [**Repositorio oficial del Cliente AutoFirma**][official-repo]
- [**Intento de construcción no oficial**][aruiz-repo]
- [**Documentación de Flatpak**][flatpak-docs]
- [**Flathub**][flathub]

[official-website]: https://firmaelectronica.gob.es
[official-repo]: https://github.com/ctt-gob-es/clienteafirma
[aruiz-repo]: https://github.com/aruiz/autofirma-flatpak
[flatpak-docs]: https://docs.flatpak.org
[flathub]: https://flathub.org
[flatpak-bundles]: https://docs.flatpak.org/en/latest/single-file-bundles.html
```
