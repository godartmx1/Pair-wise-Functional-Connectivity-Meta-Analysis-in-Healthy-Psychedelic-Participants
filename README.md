Overview

This repository contains the code and data processing pipeline used for a master's thesis examining the effects of classic serotonergic psychedelics on resting-state functional connectivity in healthy human participants.

The goal of the project was to synthesize findings across heterogeneous resting-state fMRI studies of psychedelics (e.g., psilocybin, LSD, DMT, ayahuasca) by mapping reported connectivity changes onto a common large-scale brain network framework.

Because studies used different parcellation schemes, atlases, and analytical approaches, all reported connections were re-parcellated into the seven canonical functional networks described by the Yeo 7-Network Atlas:

Visual (VIS)
Somatomotor (SMN)
Dorsal Attention (DAN)
Ventral Attention / Salience (SAL)
Limbic (LIM)
Frontoparietal Control (FPN)
Default Mode Network (DMN)

A vote-counting meta-analytic approach was then used to quantify the consistency and direction of connectivity changes across studies.

Study Objective

The primary objective was to identify:

Which large-scale brain networks show the most consistent psychedelic-induced changes in functional connectivity.
Whether connectivity changes tend to occur within networks or between networks.
Whether findings converge across studies despite methodological differences.

Workflow

The analysis pipeline consisted of four major steps:

Step 1: Re-parcellation to Yeo-7 Networks

Regions from each study's original atlas were assigned to Yeo-7 networks using spatial overlap methods.

Different procedures were used depending on the original atlas:

Harvard-Oxford Atlas
AAL Atlas
Smith 2009 RSN Atlas
HCP ICA Components
Brodmann Areas
Native Yeo-7 studies
MNI seed coordinates / spherical ROIs

Assignments were based primarily on Dice coefficient overlap with the Yeo-7 atlas.

Step 2: Extraction of Connectivity Findings

Reported pairwise functional connectivity changes were extracted from each publication.

Each reported edge included:

Source region/network
Target region/network
Direction of effect

Step 3: Calculation of Possible Edges

To account for differences in atlas resolution across studies, the total number of possible connections between network pairs was calculated.

For inter-network connections:

Possible Edges = nA × nB

For intra-network connections:

Possible Edges = n(n−1)/2

where:

nA = number of regions in Network A
nB = number of regions in Network B

This allowed connectivity findings to be weighted relative to the number of possible opportunities for observing a connection.

Step 4: Vote Counting and Weighting

Two meta-analytic matrices were generated.

Unweighted Vote Matrix

Each study contributed:

+1 = increased connectivity
-1 = decreased connectivity

for each reported network pair.

Weighted Vote Matrix

Each vote was weighted by:

1 / Possible Edges

This reduces bias from studies using coarse parcellations while preserving the contribution of studies with finer network resolution.

Outputs:

Raw vote-count matrix
Weighted vote-count matrix
Heatmaps

Included Studies

The analysis includes resting-state fMRI studies of classic serotonergic psychedelics conducted in healthy participants.

Substances include:

Psilocybin
LSD
DMT
Ayahuasca

Studies using seed-based connectivity, ICA, ROI-to-ROI connectivity, and related resting-state functional connectivity approaches were eligible.

Citation

If using this code or methodology, please cite:

Godart, M. (2026). The Effect of Serotonergic Psychedelics on Human Brain Function: A Meta-Analysis of Resting-State Functional Connectivity Studies. Master's Thesis, New York University.

Author

Maxime Godart
M.A. Psychology (Clinical Neuroscience)
New York University
