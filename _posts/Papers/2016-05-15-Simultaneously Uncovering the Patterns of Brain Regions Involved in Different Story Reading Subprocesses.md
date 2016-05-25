---
layout: post
title:  "Simultaneously Uncovering the Patterns of Brain Regions Involved in Different Story Reading Subprocesses"
date:   2016-05-15
source: http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0112575
description: Many language studies in Cognitive Neuroscience focus on a specific feature of language (syntactic role, part of speech, etc), and try to design artificial stimuli that only varies in that specific feature, and trying to decipher which part of the brain is responsible for the varied response. However, these approaches risks not being very ecologically valid, and it is unclear how the results fit into how natural language works in the brain. This study tries to find a comprehensive model of language in the brain with regards to natural language stimuli.
categories: papers
---

`Motivation of research`: Many language studies in Cognitive Neuroscience focus on a specific feature of language (syntactic role, part of speech, etc), and try to design artificial stimuli that only varies in that specific feature, and trying to decipher which part of the brain is responsible for the varied response. However, these approaches risks not being very ecologically valid, and it is unclear how the results fit into how natural language works in the brain. This study tries to find a comprehensive model of language in the brain with regards to natural language stimuli.

`Method`: Researchers trained a model which mapped a set of 195 language features onto fMRI time series of participants’ brain activity when reading (using Rapid Serial Visual Presentation RSVP) from a passage of Harry Potter. Language features include the number of letters in an individual word, the part of speech, its syntactic role, etc. After inputting training data, the model is able to predict the hemodynamic responses from each voxel given the 195-row feature vector, and then it is used to classify which of two new unseen passages are read, with 74% accuracy.

`Model`: Input of text was labelled as a vector time series with 195 story features whose values change every 0.5s
the model predicts neural activity at each voxel independently. It assumes that each time a particular story feature f_j occurs, it will generate the same response signature in voxel v, weighted by that feature’s value.
The signal in a particular voxel at a particular time is modeled as:

![Equation]({{site.baseurl}}/images/2016-05-15-Simultaneously Uncovering the Patterns of Brain Regions Involved in Different Story Reading Subprocesses/equation.png "Equation")

![Graph]({{site.baseurl}}/images/2016-05-15-Simultaneously Uncovering the Patterns of Brain Regions Involved in Different Story Reading Subprocesses/graph.png "Graph")

where `j = 1:F (F=195)` loops through the rows of the feature vector

`k = 1:4` loops through the four time points in which the model assumes different

`w` is a weight that modulates how much a previous feature (from time t-2, t-4, t-6) from a previous vector should affect the current signal at time t

f<sub>j</sub>(t-k) is the value of the jth feature in the t-k’th vector

*my own example to help my understanding*:

![Table]({{site.baseurl}}/images/2016-05-15-Simultaneously Uncovering the Patterns of Brain Regions Involved in Different Story Reading Subprocesses/table.png "Table")

At voxel X, t = 3,
F=1, k=1,
f<sub>1</sub>(3 - 1) = 0 is the value of the first entry of the vector at time t = 2, and w<sup>1</sup><sub>X3</sub> is the weight (a learned parameter) that determines how much the first feature at the previous time point affects the current signal. By summing up k = 1 through 4, the signal at each time point is the linear combination of the signal contributions (about the same feature) from 4 previous time points, with older time points contributing less (as weighted by w).

In order to discover where each story feature is represented in the brain, researchers annotated the text with one feature at a time, and did the above classification process. The predictions were limited to 15x15x15mm Searchlight cubes centered at one voxel location. This method searches for regions with high accuracy across subjects while allowing for small anatomical variations among their brains. By successively testing every type of feature j at each cube location r, they determined in which brain regions each type of feature yields high classification accuracy.

annotate story with feature into a vector indexed with time —> run through the signal model to get predicted signal of story 1 at each voxel at each time —> actually get the fMRI data from participants’ reading story 1 —> see if predicted vs. real is correct / determine classification accuracy —> try to improve accuracy by adjusting weights —> if the accuracy does not improve at particular voxels, then perhaps that voxel is not associated with this feature.

`Results` showed that the areas of the brain that represent features often agree with existing publications that study these features in isolation. Some other interesting results:
1) semantics and syntax seems to have a great overlap in brain areas. Syntax and semantics are just too fundamental to language, and the semantic and syntactic properties of words are often closely linked together, but this could also be because the features are themselves representing information at the intersection of semantics and syntax.
2) the presence of dialog among story characters activates the right temporo-parietal junction, a key theory of mind region.

`Thoughts`
the use of a model-based classification approach is definitely an interesting alternative to a controlled setting in which one variable is varied to see the effect on brain activity. This approach’s benefits include 1) high reusability of the data for different analyses and experiments 2) identifying individual differences (in say, the language system) to potential diagnose disorders (how does the whole brain of an aphasic person differ from a non-aphasic person when doing a language task)?
