# 🧠 ATP-CLIP

### A Few-Shot Vision–Language Framework for Automated Atypical Behavior Analysis in Autism Spectrum Disorder

<p align="center">
  <b>Few-Shot Learning · Vision-Language Modeling · Video Understanding · ASD Behavior Analysis</b>
</p>

---

## 📌 Overview

<div align="justify">

**ATP-CLIP** is a vision–language framework for automated atypical behavior analysis in **Autism Spectrum Disorder (ASD)**. It is designed for scenarios where labeled behavioral data are limited, while the target behaviors are subtle, temporally complex, and clinically meaningful.

Different from conventional approaches that primarily focus on short and pre-segmented video clips, ATP-CLIP supports **few-shot behavior recognition** and **cross-modal retrieval** in more realistic behavioral analysis scenarios. By jointly modeling visual evidence and structured textual descriptions, the framework establishes a semantically meaningful connection between observed behavioral patterns and their corresponding descriptions.

In addition to the ATP-CLIP framework, this work introduces **MVLASD**, a multimodal vision–language dataset designed for long-form atypical behavior analysis in ASD.

</div>

---

## ✨ Key Features

<div align="justify">

🎥 **Vision–Language Learning for ASD Analysis**  
ATP-CLIP jointly models video content and behavior-related textual descriptions to establish a shared visual–semantic representation for atypical behavior understanding.

⏱️ **Temporal Attention Pooling (TAP)**  
The Temporal Attention Pooling module dynamically aggregates informative temporal cues from video sequences and emphasizes behaviorally relevant moments.

📝 **Hierarchical Text Prompting**  
Behavior semantics are represented through multiple levels of textual descriptions, allowing the model to align visual observations with category-level, behavioral, and clinically related semantic information.

🧩 **Few-Shot Adaptation**  
A prototype-based transfer strategy enables the framework to recognize novel behavior categories using only a limited number of labeled examples.

🔎 **Cross-Modal Retrieval**  
ATP-CLIP supports both video-to-text and text-to-video retrieval, enabling semantic search and behavioral episode retrieval across visual and textual modalities.

🏥 **Clinically Grounded Behavior Representation**  
The framework incorporates structured behavioral descriptions to provide semantically interpretable representations that are relevant to ASD behavior analysis.

</div>

---

## 🏗️ Framework

<p align="center">
  <img src="figures/framework.png" alt="ATP-CLIP Framework" width="100%">
</p>

<div align="justify">

The overall architecture of **ATP-CLIP** is illustrated above. The framework contains two parallel vision and language processing branches that are subsequently aligned in a shared embedding space for behavior classification and cross-modal retrieval.

</div>

### 📝 Hierarchical Text Prompt Module

<div align="justify">

The textual branch represents each atypical behavior using hierarchical descriptions with progressively richer semantic information. Instead of relying only on behavior category names, the framework constructs three levels of prompts corresponding to the behavior class, descriptive behavioral characteristics, and clinically related descriptions.

These prompts are encoded using the CLIP text encoder and subsequently adapted through lightweight **W-Adapters**. The resulting textual representations preserve the general semantic knowledge of the pretrained vision–language model while introducing task-specific behavioral information.

</div>

### 🎞️ Temporal Attention Pooling Module

<div align="justify">

The visual branch processes sampled video frames using a pretrained CLIP visual encoder. The resulting frame-wise features are passed to the **Temporal Attention Pooling (TAP)** module, which dynamically estimates the importance of different temporal observations.

TAP combines local temporal information with broader frame-level relationships, allowing the model to emphasize behaviorally informative moments while suppressing less relevant visual content. The aggregated representation forms the final visual embedding used for cross-modal alignment.

</div>

### 🔗 Vision–Language Alignment

<div align="justify">

The visual and textual embeddings are projected into a shared semantic space, where their correspondence is optimized through similarity-based learning. This joint representation allows ATP-CLIP to associate observed behavioral patterns with different levels of textual semantics.

The learned embedding space is subsequently used for both **behavior classification** and **cross-modal retrieval**, enabling a unified framework for recognizing atypical behaviors and retrieving semantically related behavioral information.

</div>

---

## 📚 MVLASD Dataset

<div align="justify">

This work introduces **MVLASD**, a multimodal vision–language dataset for atypical behavior analysis in ASD. The dataset is collected from naturalistic parent–child interaction sessions and contains long-form video recordings together with clinician-validated temporal annotations and behavioral descriptions.

Unlike conventional ASD video datasets that primarily consist of short and pre-segmented clips, MVLASD preserves longer interaction contexts and provides multimodal semantic information suitable for both classification and retrieval tasks.

</div>

### Dataset Characteristics

<div align="justify">

- 👦 Naturalistic parent–child interaction scenarios
- 🎥 Long-form behavioral video recordings
- 🏷️ Episode-level temporal annotations
- 👩‍⚕️ Clinician-involved behavioral annotation
- 📝 Behavioral descriptions aligned with video episodes
- 🔎 Support for both classification and retrieval tasks

</div>

### Behavior Categories

<div align="justify">

MVLASD contains five categories of atypical behaviors:

- **Tantrum**
- **Spinning**
- **Arm Flapping**
- **Hand Action**
- **Head Banging**

</div>

> ⚠️ **Privacy Notice**
>
> <div align="justify">
> MVLASD contains video recordings of minors and therefore cannot be publicly released. Research access may be considered upon reasonable request and is subject to institutional ethical approval and applicable data-protection requirements.
> </div>

---

## 🎯 Tasks

### 🎯 Atypical Behavior Classification

<div align="justify">

Given an input behavioral video, ATP-CLIP maps the visual representation into the learned vision–language embedding space and predicts the corresponding atypical behavior category.

The framework supports both conventional classification and few-shot transfer settings, allowing previously unseen behavior categories to be recognized using a limited support set.

</div>

### 🔎 Cross-Modal Retrieval

<div align="justify">

ATP-CLIP additionally supports bidirectional retrieval between behavioral videos and textual descriptions.

**Video-to-Text (V2T)** retrieves relevant behavioral or clinical descriptions using a video query, while **Text-to-Video (T2V)** retrieves relevant behavioral video segments using textual descriptions as queries.

This capability enables semantic navigation of behavioral recordings and facilitates the identification of video segments associated with specific behavioral descriptions.

</div>
