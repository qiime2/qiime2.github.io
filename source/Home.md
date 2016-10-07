# General Information

**Disclaimer:** *These wiki pages serve as temporary documentation for QIIME&trade; 2 while we're in our alpha release phase. They are primarily geared toward QIIME developers or users who are interested in experimenting with an alpha version of QIIME 2. Our documentation will move to www.qiime.org when we transition to our beta release phase. The wiki instructions will currently will not work on Windows.*

See the [release notes](https://github.com/qiime2/qiime2/releases/tag/2.0.1) for details about the QIIME 2 alpha release.

## Using QIIME 2

QIIME 2 is ready for experimental use while it's in its alpha release stage. **It currently has limited microbiome analysis functionality** as we have focused our initial efforts on building the underlying framework. New functionality will regularly become available through QIIME 2 plugins. You can view a list of plugins, including those that are currently available, in development, or being planned on the QIIME 2 [Plugins](Plugins.html) page. Until the QIIME 2 microbiome analysis functionality has expanded, we recommend that you continue to use [QIIME 1](http://www.qiime.org) and [Qiita](http://qiita.microbio.me) for your microbiome analyses, as these will provide you with complete analysis solutions.

**Quickstart**: If you'd like to begin experimenting with QIIME 2, you should read [Installing and using QIIME 2](Installing-and-using-QIIME-2.html) which will show you how to install QIIME 2 and some plugins, and use it with q2cli (a command line interface). You should then read [QIIME Studio](QIIME-Studio.html), which will show you how to use QIIME 2 through a graphical user interface.

If there is specific functionality you'd like to see in QIIME 2, please post to the [QIIME 2 issue tracker](https://github.com/qiime2/qiime2/issues).

## Programming with QIIME 2

A key design goal of QIIME 2 is to enable third-party developers to create new plugins and new interfaces for QIIME.

Plugins provide a way for microbiome bioinformatics developers to make their tools accessible to end users in their QIIME environment. A plugin will enable access to its functionality through any of QIIME's interfaces, including QIIME Studio. If you're interested in developing a QIIME 2 plugin, you should begin with [Creating a QIIME 2 plugin](Creating-a-QIIME-2-plugin.html). You should also refer to the QIIME 2 [Plugins](Plugins.html) page to see what plugins already exist or are being planned.

Interfaces provide a way for software engineers to build custom interfaces around QIIME, which can include embedding QIIME as a component in other systems (e.g., cloud-based bioinformatics platforms). We have not yet developed our interface developer documentation, but two examples are currently available: [q2cli](https://github.com/qiime2/q2cli) and [QIIME Studio](https://github.com/qiime2/qiime-studio). q2cli is a simpler starting point. We will have detailed interface developer documentation available soon.

**While QIIME 2 is in its alpha release stage, backward incompatible interface changes that impact plugins and interfaces can and will occur.** We will make every effort to minimize these, and we will always document these in the [QIIME 2 ChangeLog](https://github.com/qiime2/qiime2/blob/master/CHANGELOG.md).

**The QIIME 2 developers use Slack for instant message discussion of development topics.** If you're working on plugin or interface development and need help, you should [join our Slack team](http://qiime2-slackin.qiime.org) and then get in touch on the ``#developers`` channel at https://qiime2.slack.com. This will be more reliable than emailing one of the developers directly.

## Getting updates

For updates on QIIME 2, you should [follow @qiime_ on twitter](https://twitter.com/qiime_).

To learn about where we're going with QIIME 2, see @gregcaporaso's blog post, [*QIIME 2 will revolutionize microbiome bioinformatics*](http://americangut.org/qiime-2-will-revolutionize-microbiome-bioinformatics/) (15 April 2016), and [SciPy 2016 presentation](https://www.youtube.com/watch?v=tLtGg21Yu9Q) (15 July 2016).
