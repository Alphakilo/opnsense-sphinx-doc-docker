# OPNsense doc builder
the easy-ish edition (c)

## What's this about?
So you want to contribute to the [OPNsense documentation](https://docs.opnsense.org/), and of course, you want a preview of whatever you're doing.\
The way to go would be to install python, python-pip, python-dev, python-setuptools and a bunch of other [python-y stuff](https://github.com/opnsense/docs/blob/master/requirements.txt).

That allows you to build HTML via [Sphinx](http://www.sphinx-doc.org/en/master/).

Now I personally don't want to clutter my system with boatloads of dependencies in order to get a HTML preview.\
So Docker to the rescue.

## Usage
Of course you need the opnsense-doc repository somewhere locally (and have Docker.io installed):
```bash
mkdir ~/src/
cd ~/src/
git clone https://github.com/opnsense/docs.git
```

Now run the following:
```bash
docker run --rm -v ~/src/docs:/docs alphakilo/opnsense-sphinx-doc:latest
```

Observe how the folder `docs/builds/html` now contains all the files necessary to view the docs :smile:

## Fair warning
### Versions
I'm unsure about a few things regarding the official Sphinx instance (i.e what python and sphinx versions they run).\
So there might be differences how the sources get parsed.

Right now I'm using the latest Python 3.6 and whatever Sphinx lies in the pip3 repository (currently 1.7.2).

### The build/ directory
Is not persistent. It get's wiped every time you run the Docker image (or: `/usr/bin/make clean && /usr/bin/make html`).\
This is due to the fact that I consider the build directory volatile. It should not contain artifacts from previous builds.

If you happen to think otherwise, tell me your reason via issue.