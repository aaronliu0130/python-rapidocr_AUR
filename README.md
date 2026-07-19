![fast guy with briffits delivering a RapidOCR package into the Arch of Arch](https://stardance.hackclub.com/rails/active_storage/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6MTQ3OTIwLCJwdXIiOiJibG9iX2lkIn19--54c026c4c0ee86989073b0d7c60339f05b2f9139/packaging%20rapidocr%20102x29_upscayl_4x_ultramix-balanced-4x_upscayl_4x_high-fidelity-4x.png)

# rapidOCR AUR package
PKGBUILD instructions to create a working installation of [RapidOCR](https://github.com/RapidAI/RapidOCR), easy Python bindings for popular OCR models in many different languages and backends.

See https://aur.archlinux.org/pkgbase/python-rapidocr for the AUR page,

To install, start with a clean (only pacman has touched `/usr`) Arch system and [from the AUR](https://wiki.archlinux.org/title/Arch_User_Repository) install `python-rapidocr`.

To meet Stardance requirements, this mirror and README was created. As AUR packages should minimize the amount of files that need to be cloned, this README is not included in the AUR package repository.

## Copied building notes from my pinned AUR comment

You may notice that the official repositories have yet to package python-installer 1.0.1+. We require that version due to a bug that blocks upgrades, related to symlinks.

To get this package to build, simply bump python-installer yourself:

1. Fetch the PKGBUILD for python-installer. You can do this through a helper (e.g. `paru -G python-installer`) or by simple cloning (`git clone https://gitlab.archlinux.org/archlinux/packaging/packages/python-installer.git`).
2. Open the PKGBUILD file and change line 8 to `pkgver=1.0.1`. Replace line 39 with `b2sums=('9101f90e108894c675b605123a372b45b43b4720fb1ac2eee18ea15d7759e8e1e0adeccc0da006fb3bba25e5094310158206182527ff82249a3aecacf08fcb39')` (or update the checksum yourself).
3. `cd` to the directory for python-installer's PKGBUILD and run `makepkg -si`.
