..
   # *******************************************************************************
   # Copyright (c) 2025 Contributors to the Eclipse Foundation
   #
   # See the NOTICE file(s) distributed with this work for additional
   # information regarding copyright ownership.
   #
   # This program and the accompanying materials are made available under the
   # terms of the Apache License Version 2.0 which is available at
   # https://www.apache.org/licenses/LICENSE-2.0
   #
   # SPDX-License-Identifier: Apache-2.0
   # *******************************************************************************
.. _concept:

Concept
=================

For the concept of the Trustable Software Framework (TSF), please refer to the `Eclipse Process Description <https://eclipse-score.github.io/process_description/main/trustable/index.html>`_.

Scoring
---------------------

The Trustable scores in the TSF are calculated recursively using the underlying graph structure.

Depending on whether the node is a leaf node (i.e., has no supporting statements) or a parent node (i.e., has supporting statements), the calculation of the trustability score differs.

**Leaf nodes**:
For the calculation of the scores of leaf nodes, several attributes come into play.
In particular, the existence or absence of a validator plays a crucial role in how the trustability scores of leaf nodes are determined.
The following table displays the possible scenarios for calculating the scores of leaf nodes, depending on the existence or values of its attributes:

+------------+----------------+--------------+--------------+--------------+------------------------------------------+
| normative_ | review-status_ | SME-score_   | validator_   | reference_   | Trustable-score_                         |
+============+================+==============+==============+==============+==========================================+
| ``false``  | ``*``          | ``*``        | ``*``        | ``*``        | no score                                 |
+------------+----------------+--------------+--------------+--------------+------------------------------------------+
| ``true``   | ``unreviewed`` | ``*``        | ``*``        | ``*``        | 0.0                                      |
+------------+----------------+--------------+--------------+--------------+------------------------------------------+
| ``true``   | ``reviewed``   | ``provided`` | ``excluded`` | ``excluded`` | 0.0                                      |
+------------+----------------+--------------+--------------+--------------+------------------------------------------+
| ``true``   | ``reviewed``   | ``provided`` | ``excluded`` | ``included`` | SME-score x 1                            |
+------------+----------------+--------------+--------------+--------------+------------------------------------------+
| ``true``   | ``reviewed``   | ``provided`` | ``included`` | ``*``        | SME-score × validator-score              |
+------------+----------------+--------------+--------------+--------------+------------------------------------------+


.. _normative: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/item.html#trudag.dotstop.core.item.BaseItem.normative
.. _review-status: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/graph/trustable_graph.html#trudag.dotstop.core.graph.trustable_graph.TrustableGraph.set_link_status
.. _SME-score: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/item.html#trudag.dotstop.core.item.BaseItem.sme_scores
.. _validator: https://codethinklabs.gitlab.io/trustable/trustable/trudag/usage.html#providing-evidence
.. _reference: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/item.html#trudag.dotstop.core.item.BaseItem.references
.. _Trustable-score: https://codethinklabs.gitlab.io/trustable/trustable/trudag/scoring-roadmap.html



**Parent nodes**:
The score for any parent node is then recursively calculated as the normalized weighted sum of the scores of its supporting statements.
Note that currently, TSF only supports equal weighting. 
In other words, the score of a parent node is the mean of the scores of its child nodes.
This behaviour is however likely to change in the future, to support different weighting schemes.
Any supporting statements with a suspect link are excluded from the calculation of the scores of parent nodes.
The following table displays the possible scenarios for calculating the scores of parent nodes:

+------------+----------------+--------------+----------------------------------------------------+
| normative_ | review-status_ | link-status_ | Trustable-score_                                   |
+============+================+==============+====================================================+
| ``false``  | ``*``          | ``*``        | no score                                           |
+------------+----------------+--------------+----------------------------------------------------+
| ``true``   | ``unreviewed`` | ``*``        | 0.0                                                |
+------------+----------------+--------------+----------------------------------------------------+
| ``true``   | ``reviewed``   | ``suspect``  | mean of supporting statements with no suspect links|
+------------+----------------+--------------+----------------------------------------------------+
| ``true``   | ``reviewed``   | ``linked``   | mean of all supporting statements                  |
+------------+----------------+--------------+----------------------------------------------------+

.. _normative: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/item.html#trudag.dotstop.core.item.BaseItem.normative
.. _review-status: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/graph/trustable_graph.html#trudag.dotstop.core.graph.trustable_graph.TrustableGraph.set_link_status
.. _link-status: https://codethinklabs.gitlab.io/trustable/trustable/reference/trudag/dotstop/core/graph/trustable_graph.html#trudag.dotstop.core.graph.trustable_graph.LinkStatus
.. _Trustable-score: https://codethinklabs.gitlab.io/trustable/trustable/trudag/scoring-roadmap.html


Terminology
~~~~~~~~~~~
- **normative**: Indicates whether the statement is normative (`true`) or not (`false`). If a statement is not normative, it does not contribute to the score calculation, and shall not be reviewed. This attribute is not to be set or changed by the SME reviewer.
- **review-status**: Indicates the current review status of the statement. A `false` means the statement needs to be reviewed or re-reviewed, and that the score is set to `0.0`. A `true` means the statement has been reviewed by a subject matter expert (SME).
- **SME-score**: A score reflecting the SME reviewer's confidence in the truth of the statement as a probability.
- **validator**: Automatic scripts that validate the correctness of a statement. Note that in the markdown files, validators are referred to as "evidence".
- **reference**: Supporting material for the SME reviewer to evaluate the statement.
- **link-status**: Indicates whether the statement has any suspect links. If suspect links exist, the score of a parent item is calculated based on child items without suspect links only.   
- **Trustable-score**: Shows how the TSF score is calculated.

Example scoring
~~~~~~~~~~~~~~~
This diagram illustrates an example of the scoring process in the TSF and how the score propagates upwards in the graph. 
Please note that the numbers shown in this graph are **example values only** and do not represent real assessments.

.. image:: score_calculation_example.svg
   :alt: Graph illustrating the scoring process in the Trustable Software Framework
   :align: center