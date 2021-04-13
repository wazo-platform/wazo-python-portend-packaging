# wazo-python-portend-packaging

Debian packaging for [portend](https://github.com/jaraco/portend) used in Wazo.

## Upgrading

To upgrade portend:

* Update the version number in the `VERSION` file
* Update the changelog using `dch -i` to the matching version
* Refresh patches
* Push the changes

## Building Locally

To build on a test environment before submitting a change to production the following procedure can be used.

```sh
make -f debian/rules get-orig-source
tar -xvf ../wazo-python-portend-packaging_*.orig.tar.gz  --strip 1
dpkg-buildpackage -us -uc
```
The `.deb` will be located in the parent directory.

# Add patches

To add patches:

```sh
make -f debian/rules get-orig-source
tar -xvf ../wazo-python-portend-packaging_*.orig.tar.gz  --strip 1
vim <filename.py>
dpkg-source --commit
dpkg-buildpackage -us -uc

