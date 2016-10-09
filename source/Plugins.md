# Plugins

QIIME's analysis functionality comes in the form of plugins. As we progress through our alpha release phase we plan to develop a mechanism for allowing users to discover what plugins are available. Our initial draft of this is the [QIIME 2 Plugins spreadsheet](https://docs.google.com/spreadsheets/d/1KdgbooDDuh_aE-aCGlVLNgMCli513wU9E5_PgpL6tbY/pubhtml?gid=0&single=true).

The ``Status`` categories used in this spreadsheet are the following:
* ``Released`` : The plugin is currently installable with ``conda install -c qiime2``.
* ``Pre-release development`` : The plugin is currently under active development. See the *Estimated release date* for when this plugin is expected to be moved to ``Release`` status.
* ``Planning`` : The plugin is in the planning stage. Development has not officially started, but it is expected to start soon. Someone has already committed to working on this plugin. There may be ``Unmet dependencies`` that are blocking its transition to ``Pre-release development``.
* ``Needs developer`` : The plugin is in the early planning phase. It represents functionality that is needed or wanted, but no one has yet committed to working on this plugin. There may be ``Unmet dependencies`` that are blocking its transition to ``Planning`` or ``Pre-release development``.

If you'd like to develop a QIIME 2 plugin, get in touch on our Slack channel (details [here](Home.html#programming-with-qiime-2)) to request edit access to the spreadsheet.

If you're looking for documentation on plugin development, see [Creating a QIIME 2 plugin](Creating-a-QIIME-2-plugin.html).


other text
==========
## Programming with QIIME 2

A key design goal of QIIME 2 is to enable third-party developers to create new plugins and new interfaces for QIIME.

Plugins provide a way for microbiome bioinformatics developers to make their tools accessible to end users in their QIIME environment. A plugin will enable access to its functionality through any of QIIME's interfaces, including QIIME Studio. If you're interested in developing a QIIME 2 plugin, you should begin with [Creating a QIIME 2 plugin](Creating-a-QIIME-2-plugin.html). You should also refer to the QIIME 2 [Plugins](Plugins.html) page to see what plugins already exist or are being planned.

Interfaces provide a way for software engineers to build custom interfaces around QIIME, which can include embedding QIIME as a component in other systems (e.g., cloud-based bioinformatics platforms). We have not yet developed our interface developer documentation, but two examples are currently available: [q2cli](https://github.com/qiime2/q2cli) and [QIIME Studio](https://github.com/qiime2/qiime-studio). q2cli is a simpler starting point. We will have detailed interface developer documentation available soon.

**While QIIME 2 is in its alpha release stage, backward incompatible interface changes that impact plugins and interfaces can and will occur.** We will make every effort to minimize these, and we will always document these in the [QIIME 2 ChangeLog](https://github.com/qiime2/qiime2/blob/master/CHANGELOG.md).

**The QIIME 2 developers use Slack for instant message discussion of development topics.** If you're working on plugin or interface development and need help, you should [join our Slack team](http://qiime2-slackin.qiime.org) and then get in touch on the ``#developers`` channel at https://qiime2.slack.com. This will be more reliable than emailing one of the developers directly.
