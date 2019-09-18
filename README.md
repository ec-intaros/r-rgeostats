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
sudo conda install r-rgeostats
```

### <a name="testing">Testing 

* Export the proper environment variables:

```
export PATH=/opt/anaconda/bin:$PATH
export LD_LIBRARY_PATH=/opt/glibc-2.14/lib:${LD_LIBRARY_PATH}
```

* Type:

```
R -e "library('RGeostats')"
```

### <a name="upgrade">Upgrade

To upgrade this package to newer version of Rgeostats proceed as follows:

* Login on a Ellip Workflows VM,
* Clone the repo:

```
git clone https://github.com/ec-intaros/r-rgeostats.git
cd r-rgeostats/conda.recipe
```

* Edit the `meta.yaml` file to update the following information:

``` 
version
md5
```

* Install `conda-build` with:

```
sudo conda install conda-build
```
 
* Build the package with:

```
sudo conda build .
```
 
* Commit and push the local changes to the remote repository 
