# The Unhealthy Comments Corpus (UCC)


The Unhealthy Comments Corpus (UCC) is corpus of 44355 comments intended to assist in research on identifying subtle attributes which contribute to unhealthy conversations online. 

Each comment is labelled as either 'healthy' or 'unhealthy', in addition to binary labels for the presence of six potentially 'unhealthy' sub-attributes: (1) hostile; (2) antagonistic, insulting, provocative or trolling; (3) dismissive; (4) condescending or patronising; (5) sarcastic; and/or (6) an unfair generalisation. Each label also has an associated confidence score.

For a detailed description of the annotation process, quality control procedures, summary statistics and baseline modelling results, see our [paper](https://arxiv.org/abs/2010.07410), to appear in the [Fourth Workshop on Online Abuse and Harms 2020](https://www.workshopononlineabuse.com/).

The UCC contributes further high quality data on  attributes  like  sarcasm,  hostility,  and  condescension, adding to existing datasets on these and related attributes, and provides (to the best of our knowledge) the first dataset of this scale with labels for dismissiveness,  unfair generalisations,  antagonistic behavior, and overall assessments of whether those comments fall within 'healthy' conversation.

We hope that this dataset  can contribute to research on how to understand, monitor and deal with unhealthy online interactions to promote healthier conversations online.

## The data

The dataset is provided as three .csv files, `train.csv`, `test.csv`, and `val.csv`. In addition to labels and confidence scores for each of the above-mentioned attributes, each comment includes the number of trusted judgements which were aggregated to yield the results labels and confidence scores (see paper for details). 

We also provide the individual annotations of each comment in `unhealthy_full.csv`. This contains all individual judgements which were aggregated to create the final dataset. Each of these annotations includes the trustworthiness score of the annotator, allowing users to impose higher trustworthiness thresholds or apply different aggregation methods as desired.

The raw comments were taken from the [comments](https://github.com/sfu-discourse-lab/SOCC#comments) corpus within the [SFU Opinion and Comments Corpus](https://github.com/sfu-discourse-lab/SOCC). 

## Baseline classification

We provide notebooks to replicate our baseline classification results on this dataset in `UnhealthyConversations.ipynb`. Fine-tuning pre-trained BERT produces classifiers with modest performance compared to the state of the art for sequence classification. The best performing attributes, 'hostile' and 'antagonistic' are also those most similar to the types of attributes typically annotated in comment classification work. The other attributes seem to cluster together, with the ‘sarcastic’ label particularly noteworthy for its low performance.
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/conversationai/unhealthy-conversations/blob/master/notebooks/UnhealthyConversations.ipynb)


![Figure here](https://github.com/conversationai/unhealthy-conversations/blob/master/auc.pdf)

To give context to the model performance, we compare the performance with human workers. For each comment, we randomly hold out one annotator to act as our 'human model' and use the aggregated score of the other annotators as the ground truth to compute the ROC AUC (repeated 5 times then averaged). We use the same test sets to compute the ROC AUC of the trained BERT model and average those scores as well. As we can see, for all attributes other than 'sarcastic' the BERT model outperforms a randomly selected human annotator, indicating that it has sufficiently captured the semantic and syntactic structures for these attributes. For 'sarcastic', the gap between the BERT model and human annotators indicates a rich area for studying whether model performance can be improved.

| Attribute}  | Human AUC | BERT AUC |
|------------ |-----------|----------|
|Antagonistic |0.71       |  0.82    | 
|Condescending| 0.72      |    0.78  |
|Dismissive   | 0.68      | 0.82     |
|Generalisation | 0.73    | 0.74     |
|Hostile       |0.76      |0.84      |
|Sarcastic     |0.72      |0.64      |
|Unhealthy     | 0.62     | 0.69   |
 
Code for  this analysis is in `AUC_analysis.ipynb`.

_____


This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.
https://creativecommons.org/licenses/by-nc-sa/4.0/
