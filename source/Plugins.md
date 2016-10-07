# Plugins

QIIME's analysis functionality comes in the form of plugins. As we progress through our alpha release phase we plan to develop a mechanism for allowing users to discover what plugins are available. Our initial draft of this is the [QIIME 2 Plugins spreadsheet](https://docs.google.com/spreadsheets/d/1KdgbooDDuh_aE-aCGlVLNgMCli513wU9E5_PgpL6tbY/pubhtml?gid=0&single=true).

The ``Status`` categories used in this spreadsheet are the following:
* ``Released`` : The plugin is currently installable with ``conda install -c qiime2``.
* ``Pre-release development`` : The plugin is currently under active development. See the *Estimated release date* for when this plugin is expected to be moved to ``Release`` status.
* ``Planning`` : The plugin is in the planning stage. Development has not officially started, but it is expected to start soon. Someone has already committed to working on this plugin. There may be ``Unmet dependencies`` that are blocking its transition to ``Pre-release development``.
* ``Needs developer`` : The plugin is in the early planning phase. It represents functionality that is needed or wanted, but no one has yet committed to working on this plugin. There may be ``Unmet dependencies`` that are blocking its transition to ``Planning`` or ``Pre-release development``.

If you'd like to develop a QIIME 2 plugin, get in touch on our Slack channel (details [here](Home.html#programming-with-qiime-2)) to request edit access to the spreadsheet.

If you're looking for documentation on plugin development, see [Creating a QIIME 2 plugin](Creating-a-QIIME-2-plugin.html).