# Glossary

This document is currently a work in progress for a QIIME 2 terminology glossary.

**``Action``**: The general case of a ``Method`` or ``Visualizer``.

**``Artifact``**: Data that can be used as input to a QIIME ``Method`` or ``Visualizer``, or that can be generated as output from a QIIME ``Method``.

**``Method``**: an ``Action`` that takes some combination of ``Artifacts`` and ``Parameters`` as input, and produces one or more ``Artifacts`` as output. These output ``Artifacts`` could subsequently be used as input to other QIIME 2 ``Methods`` or ``Visualizers``. ``Methods`` can produce intermediate or terminal outputs in a QIIME analysis.

**``Parameter``**: a primitive (i.e., non-``Artifact``) input to a function.

**``Plugin``**: a Python 3 library that instantiates ``qiime.plugin.Plugin``, and registers ``Actions``, ``DataLayouts``, and/or ``SemanticTypes``. QIIME 2 plugins provide all of the microbiome (i.e. domain-specific) functionality that is accessible to users, and can be developed and distributed by anyone.

**``Pipeline``**: a combination of ``Actions``. This is not yet implemented.

**``QIIME 2``**: Quantitative Insights Into Microbial Ecology 2, an extensible microbiome analysis framework that is super-cool.

**``Result``**: The general case of an ``Artifact`` or ``Visualization``.

**``Visualizer``**: an ``Action`` that takes some combination of ``Artifacts`` and ``Parameters`` as input, and produces exactly one ``Visualization`` as output. Output ``Visualizations``, by definition, cannot be used as input to other QIIME 2 ``Methods`` or ``Visualizers``. ``Visualizers`` can only produce terminal output in a QIIME analysis.

**``Visualization``**: Data that can be generated as output from a QIIME ``Visualizer``.
