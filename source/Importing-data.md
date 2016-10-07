*This page assumes that you have already run through the [Installing and using QIIME 2](https://github.com/qiime2/qiime2/wiki/Installing-and-using-QIIME-2) documentation.*

# Importing Data

In order to use QIIME 2, we require input data to be wrapped in `Artifacts`. This is what enables distributed, automatic, provenance tracking, and semantic type validation. Because your initial data will not start out as an Artifact we need to *import* the data into something the QIIME 2 framework can understand.

This is simple with `q2cli`, first let's download an example `biom` table:
```bash
curl -sO https://dl.dropboxusercontent.com/u/2868868/data/qiime2/feature-table.biom
```

Next we will use the import command from `qiime tools`, it requires a type, input-path, and output-path:
```bash
qiime tools import --help
```
```
Usage: qiime tools import [OPTIONS]

  Import data to create a new QIIME Artifact. See
  http://2.qiime.org/Importing-data for usage examples and details on the
  file types and associated semantic types that can be imported.

Options:
  --type TEXT         The semantic type of the new artifact.  [required]
  --input-path PATH   Path to file or directory that should be imported.
                      [required]
  --output-path PATH  Path where output artifact should be written.
                      [required]
  --help              Show this message and exit.
```

Providing the following arguments will import a `FeatureTable[Frequency]` Artifact:
```bash
qiime tools import --type "FeatureTable[Frequency]" --input-path feature-table.biom --output-path ft-freqs
```
Because we were dealing with a `biom` table of counts, we chose the semantic type of `FeatureTable[Frequency]`.
Now we have a QIIME 2 Artifact called `ft-freqs.qza` that we can start using!

We can view a summary of that table as follows:

```bash
qiime feature-table summarize --i-table ft-freqs.qza --o-visualization ft-freqs-summary
qiime tools view ft-freqs-summary.qzv

To see what semantic types are available in QIIME 2 and to learn more about them, see the [Semantic Types](https://github.com/qiime2/qiime2/wiki/Semantic-types) section of our documentation.
