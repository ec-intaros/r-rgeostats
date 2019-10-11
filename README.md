# r-rgeostats

r-rgeostats is an Anaconda package which provides RGeostats.
RGeostats is the Geostatistical Package (under R platform) developed by the Geostatistical Team of the Geosciences Research Center of MINES ParisTech. More information at http://rgeostats.free.fr

## License

* http://rgeostats.free.fr/LICENSE


### Quick link

* [Installation](#installation)
* [Testing](#testing)
* [Upgrade](#upgrade)

### <a name="installation">Installation 

* Login on a [Ellip Workflows VM](https://docs.terradue.com/ellip/solutions/workflows/index.html),
* Install the dependencies:

```
sudo yum install -y glibc-2.14 miniconda
```

* Install the R package:

```
sudo conda update conda 
sudo conda install r-rgeostats
```

### <a name="testing">Testing 

* Type:

```
LD_LIBRARY_PATH=/opt/glibc-2.14/lib:${LD_LIBRARY_PATH} /opt/anaconda/bin/R -e "library('RGeostats')"
```

### <a name="upgrade">Upgrade

To upgrade this package to newer version of Rgeostats proceed as follows:

* Login on a Ellip Workflows VM,
* Install the required dependencies:

```
sudo yum install -y glibc-2.14 miniconda
sudo conda update -y conda
sudo conda install -y conda-build
```

* Clone the repo:

```
git clone https://github.com/ec-intaros/r-rgeostats.git
cd r-rgeostats/conda.recipe
git checkout develop
```

* Edit the `meta.yaml` file to update the following information:

``` 
version (first line)
sha256
```
 
* Build the package with:

```
sudo conda build . --no-test
```

#### Local Test

* Perform a local test:

```
sudo conda install -y --use-local r-rgeostats
LD_LIBRARY_PATH=/opt/glibc-2.14/lib:${LD_LIBRARY_PATH} /opt/anaconda/bin/R -e "library('RGeostats')"
```

#### Release and deployment to production

* Commit and push the local changes to the remote repository:

```
git commit -am "Set new version"
```

* Initialise [git flow](https://danielkummer.github.io/git-flow-cheatsheet/):

```
git flow init -d
export GIT_MERGE_AUTOEDIT=no
``` 

* Perform the release:

```
version=<your version number>
git flow release start ${version}
git flow release finish -m "${version}" ${version}
```

* Push the changes on the remote repository

```
git config --global push.default matching
git push && git push --tags
```

The command *git push* triggers a build process on https://build.terradue.com, which produces an Anaconda package for the new version and stores it under https://anaconda.org/Terradue/r-rgeostats.
