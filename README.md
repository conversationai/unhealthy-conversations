# The Unheatlhy Comments Corpus (UCC)


The Unhealthy Comments Corpus (UCC) is corpus of 44355 comments intended to assist in research on identifying subtle attributes which contirbute to unheatlhy conversaions online. 

Each comment is labelled as either 'healthy' or 'unhealthy', in addition to binary labels for the presence of six potentially 'unhealthy' sub-attributes: (1) hostile; (2) antagonistic, insulting, provocative or trolling; (3) dismissive; (4) condescending or patronising; (5) sarcastic; and/or (6) an unfair generalisation. Each label also has an associated confidence score.

For a detailed description of the annotation process, quality control procedures, summary statistics and baseline modelling results, see our [paper](to_add), to appear in the [Fourth Workshop on Online Abuse and Harms 2020](https://www.workshopononlineabuse.com/).

## The data

The dataset is provided as three .csv files, `train.csv`, `test.csv`, and `val.csv`. In addition to labels and confidence scores for each of the above-mentioned attributes, each comment includes the number of trusted judgements which were aggregated to yield the results labels and confidence scores (see paper for details). 

We also provide the individual annotations of each comment in `unhealthy_full.csv`. This contains all individual judgements which were aggregatted to create the final dataset. Each of these annotations includes the trustworthiness score of the annotator, allowing users to impose higher trustworthiness thresholds or apply different aggregation methods if they so wish.

## Baseline classification
