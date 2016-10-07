**Disclaimer:** *This wiki page is temporary documentation for QIIME 2 while we're in our alpha release phase. These are primarily geared toward QIIME developers or users who are interested in experimenting with an alpha version of QIIME 2. Our documentation will move to qiime.org when we transition to our beta release phase, and installation will be much simpler. These instructions currently will not work on Windows.*

# Installing and Using QIIME 2

This document describes how to install the QIIME 2 framework and some QIIME 2 interfaces and plugins. It then illustrates how to use the system to do a basic analysis on test data files using [q2cli](https://github.com/qiime2/q2cli), a QIIME 2 command line interface. To run this demo, you'll need to install [Miniconda](http://conda.pydata.org/miniconda.html) if you don't already have it installed.

## Create a working directory and download example QIIME 2 artifact files

Start by creating a directory to work in and changing to that directory:

```bash
mkdir qiime2-test
cd qiime2-test
```

Next, download these demo ``.qza`` (QIIME zipped artifact) files to that directory:
 * [`feature-table-frequency.qza`](https://dl.dropboxusercontent.com/u/2868868/data/qiime2/feature-table-frequency.qza)
 * [`phylogeny.qza`](https://dl.dropboxusercontent.com/u/2868868/data/qiime2/phylogeny.qza)
 * [`q2-demo-sample-md.tsv`](https://dl.dropboxusercontent.com/u/2868868/q2-demo-sample-md.tsv)

(with `curl`):
 ```bash
curl -sO https://dl.dropboxusercontent.com/u/2868868/data/qiime2/feature-table-frequency.qza
curl -sO https://dl.dropboxusercontent.com/u/2868868/data/qiime2/phylogeny.qza
curl -sO https://dl.dropboxusercontent.com/u/2868868/q2-demo-sample-md.tsv
 ```

## Install QIIME 2 framework and command line interface

First we'll install ``qiime``, which is the QIIME 2 framework, and ``q2cli``, which is a QIIME 2 command line interface, in a new Python 3 conda environment.

```bash
conda create -n q2test -c qiime2 python=3.5 qiime q2cli
source activate q2test
```

You can now run ``qiime --help`` to see the available commands. You can discover what plugins you currently have installed (there aren't any installed yet), as well as other information about your QIIME installation, by running ``qiime info``.

```bash
qiime --help
qiime info
```

There's not much to do without some plugins, so install the ``q2-types`` and ``q2-feature-table`` plugins and execute the ``qiime info`` command again.

```bash
conda install -c qiime2 -c biocore q2-types q2-feature-table
qiime info
```

All installed plugins will be listed here, so you should now see that you have two plugins installed.

If you call ``qiime --help`` again, you'll see that you now have a new command available, corresponding to the `q2-feature-table` plugin (the `q2-types` plugin does not have any actions to perform so it is not listed as a subcommand). To see what subcommands the ``q2-feature-table`` plugin defines, call it with ``--help``:

```bash
qiime feature-table --help
```

You also see some other information about the plugin here, including its website, how it should be cited, and how users can get technical support with the plugin.

Install the ``q2-diversity`` plugin as well. You'll then have three plugins installed.

```bash
conda install -c qiime2 q2-diversity
qiime info
qiime diversity --help
```

Now you're ready to run a command that performs an analysis. The ``qiime diversity core-metrics`` *method* is a good one for this. This takes a feature table (a BIOM table, in QIIME 1 terminology), a phylogenetic tree, and a rarefaction depth as input. It will rarefy the feature table to the requested rarefaction depth, then compute two alpha diversity metrics (Faith's PD and observed OTUs), four beta diversity metrics (Jaccard, Bray-Curtis, unweighted UniFrac, and weighted UniFrac), and then run principal coordinate analysis (PCoA) on the resulting beta diversity distance matrices.

```bash
qiime diversity core-metrics --i-table feature-table-frequency.qza --i-phylogeny phylogeny.qza --p-counts-per-sample 100 --o-faith-pd-vector pd --o-unweighted-unifrac-pcoa-results uu-pc.qza --output-dir cm-output
```

At this stage you will have generated data as QIIME Zipped Artifact (``.qza``) files. The `pd.qza` and `uu-pc.qza` files, which we explicitly specified the names for, will be written to your current working directory, and the eight remaining output files will be placed in your `cm-output` directory that was created by using `q2cli`'s optional `--output-dir` option. File paths for all output artifacts and visualizations (i.e., parameters beginning with ``--o-``) are optional: you can specify them if you'd like explicit control over the path they will be written to, or you can not specify them and they will be written to the directory specified by ``--output-dir`` with a default name. We had `pd.qza` and `uu-pc.qza` be written in the current directory, for convenience of use later in this tutorial.

QIIME plugins also provide *visualizers* to help with interpretation of these data. We'll apply two visualizers here, and then learn how to interact with them directly. First, we'll install the [Emperor](http://biocore.github.io/emperor/) QIIME plugin:

```bash
conda install -c qiime2 -c biocore q2-emperor
```

You can call the Emperor plugin with its ``--help`` option to see what actions it can perform (i.e., what its subcommands are). Note that the help also includes the reference that users should cite if they use this plugin.

```bash
qiime emperor --help
```

We'll next generate one alpha diversity visualization, and one beta diversity ordination visualization:

```bash
qiime diversity alpha-compare --i-alpha-diversity pd.qza --m-metadata-file q2-demo-sample-md.tsv --m-metadata-category SampleType --o-visualization pd-compare
qiime emperor plot --i-pcoa uu-pc.qza --m-sample-metadata-file q2-demo-sample-md.tsv --o-visualization uu-emperor
```

Each of these will create a QIIME Zipped Visualization (``.qzv``) file. Different interfaces will provide support for interacting with these in their own ways, but on their own, these are simply zip files. They can be unzipped with graphical or command line zip tools (e.g., ``unzip``). You can view these using the command line interface as follows:

```bash
qiime tools view uu-emperor.qzv
qiime tools view pd-compare.qzv
```

## Working with other QIIME 2 interfaces

As a next step in exploring QIIME 2, you should work with other interfaces. In the same way that QIIME 2 plugins can be added or removed to change the functionality of QIIME, you can also change interfaces. In this tutorial we explored the command line interface, but unlike QIIME 1, the command line is only one possible interface for QIIME 2. You can next explore [[QIIME-Studio]], the first graphical user interface for QIIME 2, and the [[Artifact-API]], an *Application Programmer Interface* that is optimized for users working in [Jupyter Notebooks](http://jupyter.org).
