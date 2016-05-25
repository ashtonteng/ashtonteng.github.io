---
layout: post
title:  "Functional Network Organization of the Human Brain"
date:   2016-05-24
source: http://www.sciencedirect.com/science/article/pii/S0896627311007926
description: This study applies graph theory to the analysis of resting state functional connectivity MRI (rs-fcMRI) brain networks. Graph theory is used to analyze rs-fcMRI data because it can adequately describe the brain as a complex network, and model properties at the level of the entire graph, subgraphs, or individual nodes.The paper tries to solve one problem in using graph theory to study functional brain organization - the difficulty of defining individual nodes that make up a brain network.
categories: papers
---

This study applies `graph theory` to the analysis of `resting state functional connectivity MRI (rs-fcMRI)` brain networks. In a graph theory model, there are nodes, ties (relationships between nodes), and collections of nodes and ties which are called graphs or networks. Graph theory is used to analyze rs-fcMRI data because it can adequately describe the brain as a complex network, and model properties at the level of the entire graph, subgraphs, or individual nodes. Graph theory can also quantify hierarchy and substructure within a graph, identify hubs and critical nodes, determine how easily traffic flows in different portions at different scales of a network, and estimate the controllability of a system.

The paper tries to solve one problem in using graph theory to study functional brain organization - *the difficulty of defining individual nodes that make up a brain network*. Researchers came up with two novel node definitions, and compared the results with two older, standard definitions.

- standard definition 1:
    - parcel-based graph formed using the 90-parcel AAL atlas, dividing cortical and subcortical structures into parcels based on anatomical landmarks.
    - Each parcel is a node
- standard definition 2:
    - voxel-based graph using all nodes in the AAL atlas (n = 40,100)
    - each voxel is a node, and all pairs are connected with a tie
- novel definition 1:
    - a task-based, functional definition
    - from a large fMRI data set, identified regions of interest (ROIs) that were reliably and significantly modulated when certain behaviors were demanded
    - the centers of ROIs, modeled as 10mm diameter spheres, were chosen as nodes (n = 264)
    - ties were formed between each pair of nodes, except those that were less than 20mm apart (to avoid possible shared signal between nearby nodes)
- novel definition 2:
    - modification of voxelwise network (standard definition 2)
    - all short-distance ties less than 20mm were excluded (nearby voxels share nonbiological signals due to procedures in data processing, as well as spurious augmentation by subject motion)

Researchers evaluated how well each definition’s graph described actual brain networks by comparing the subgraphs of each graph to functional groups within the brain that coactive during certain types of task (e.g. the dorsal attention system). A subgraph is a set of highly related nodes that are more densely connected to one another than to the rest of the graph. The hypothesis is that specific patterns of high correlation within functional systems would be reflected as subgraphs in an accurate brain-wide rs-fcMRI network. Therefore, the presence of subgraphs that correspond to functional systems is a good indicator for how accurate the graph models features of brain organization. Results indeed shows that the two novel definitions of nodes produced graphs that have much more realistic subgraphs than the two standard definitions of nodes.

After establishing useful graphs to represent brain networks, researchers then analyzed the identities of the subgraphs, which corresponded to pre-established functional networks, as well as some novel, unexplained functional networks. These networks include:

1. default network (red)
2. fronto-parietal task control network (yellow)
3. dorsal attention network (green)
4. ventral attention network (teal)

![Networks 1]({{site.baseurl}}/images/2016-05-15-Functional Network Organization of the Human Brain/1.png "Networks")

image above:

- First column: pre-established functional areas from other studies
- Second column: subgraphs from novel definition 1 (spheres), and novel definition 2
- Third column: subgraph from standard definition 1
- Fourth column: subgraph from standard definition 2

![Networks 2]({{site.baseurl}}/images/2016-05-15-Functional Network Organization of the Human Brain/2.png "Networks")

5. visual system (blue) (including most of occipital cortex, with a small portion of superior parietal cortex and the postero-lateral thalamus, potentially LGN)
6. dorsal somatosensory-motor (SSM) cortex (S1, M1) (cyan)
7. ventral somatosensory-motor (SSM) cortex (orange)
    - the division of dorsal/ventral SSM corresponds to the separation between the face (ventral) and the rest of the body (dorsal)
    - the correlation between the auditory region and the face region is higher than that of the auditory region and the body region, perhaps reflecting the history of coactivation of these areas as a function of oral language.
8. auditory system (pink) (emerges from cingulo-opercular network at high thresholds) (threshold is defined in terms of the correlation coefficient between nodes)
9. two cingulo-opercular networks (black and purple)
    - black subgraph is most likely the “salience system” (Seeley et al. 2007)
    - purple subgraph is most likely the “core” of a task performance system (Dosenbach et al. 2006)
10. unknown subgraph 1 (salmon)
11. unknown subgraph 2 (light blue)
    - it is suggested that these unknown regions are related to memory retrieval

After analyzing individual subgraphs, researchers examined collections of subgraphs and their relationships to one another.

`“Task-Positive” and “Task-Negative” Systems`

- Fox et al. (2005) proposed a task-positive network that is broadly activated across tasks, and a task-negative network that is broadly inactivated across tasks. Fox et al. found this through seed map analyses, measuring the relationships between a seed ROI and other brain regions (usually voxels). Seed timecourses demonstrated that rs-fcMRI signal in one network tended to rise as the signal in the other network fell.
- Results from this study suggests that three separate subgraphs, the dorsal attention system (green), the fronto-parietal task control system (yellow), and the cingulo-opercular task control system (purple) all correspond to the “Task-Positive System”.
- The default network (red), and possibly the memory retrieval (salmon) subgraph corresponds to the “Task-Negative System”.
- So what Fox et al. thought was a single task positive network is actually composed of 3 subgraphs in this study. The difference in results may be due to the different approaches used to analyze rs-fcMRI data. Seed maps only capture relationships between seeds and other brain regions, while the graph-based approach can also capture relationships between the other brain regions.

`The Default Network is Like Sensory and Motor Systems`

- According to classical models of cognitive control, subgraphs responsible for “control” should maintain a diverse set of relationships, while subgraphs responsible for “processing” should have compartmentalized sets of relationships
- compartmentalization and diversity of relationships in graphs are measured by local efficiency and the participation coefficient:
Local efficiency: measure of integration among neighbors of a node (high: node is embedded in richly connected environment. low: neighbors are sparsely connected to one another)
Participation coefficient: extent to which a node connects to subgraphs other than its own (high: node connected to many subgraphs. low: nodes are confined to interactions within their own subgraphs)
- Results show that the visual (blue), hand (SSM) and the default network (red) have high local efficiency and low participation coefficients. This makes sense for visual and SSM, but not for default network, which is supposed to be “control”!
- Front-parietal task control has low local efficiency and high participant coefficient, as predicted.

`Thoughts`

The findings of this paper seems to have one fundamental flaw - the use of ROIs from known functional systems to form nodes of the graph would obviously produce consistent results with known functional systems! The use of rs-fcMRI should be used as an alternate method for investigating brain functional networks, as perhaps a “check” to see if localizer and task-specific studies are accurate, and hence should not be based on task-specific studies themselves. Although researchers also used the modified voxelwise network and have found that the subgraphs produced are quite similar, they admitted that most of the conclusions were based on the ROI map (as there are many issues with analyzing the voxelwise graph). However, the use of graph theory to analyze rs-fcMRI data is definitely an ingenious approach, and is a great way to validate existing data, as well as discover new properties about functional brain networks!