<p align="center">
  <img src="assets/ic_launcher-playstore.png" alt="DressMe.AI Logo" width="200"/>
</p>

<h1 align="center">Awesome DressMe.AI</h1>

<p align="center">
  <em>A curated collection of repositories powering the DressMe.AI app — an intelligent outfit recommendation system using VLM/LLM/ML pipelines for personalization.</em>
</p>

---

## Overview

**DressMe.AI** is an Android-based outfit recommendation app that personalizes clothing suggestions based on user preferences and visual attributes. It combines computer vision, LLMs, and mobile deployment for an end-to-end intelligent wardrobe experience.

This collection includes the app frontend, machine learning pipelines, annotation tools, and infrastructure code that make DressMe.AI modular, extensible, and production-ready.

---

## Repositories

### Frontend

- [`dressme-app`](https://github.com/DressMe-AI/dressme-app) – Main Android app with TensorFlow Lite model integration. Supports on-device outfit pairing and user feedback collection.

### Machine Learning

- [`dressme-ml-sagemaker`](https://github.com/DressMe-AI/dressme-ml-sagemaker) – Backend ML pipeline for training preference models using SageMaker.
- [`dressme-vlm`](https://github.com/DressMe-AI/dressme-vlm) – Vision-language model (ViT + LLM) for extracting structured clothing attributes from images.

### User Feedback / Annotation

- [`dressme-annotate`](https://github.com/DressMe-AI/dressme-annotate) – Jupyter notebooks for collecting and labeling user preferences to train the matching model.

### Infrastructure

- [`dressme-agentic`](https://github.com/DressMe-AI/dressme-agentic) – *(Private)* Agentic interface to personalize recommendations via LLM-based reasoning.
- [`dressme-ec2`](https://github.com/DressMe-AI/dressme-ec2) – *(Private)* EC2 setup and deployment infrastructure for inference and annotation hosting.

---

## Architecture Summary
```mermaid
flowchart TD
    A[Image Upload: Wardrobe stored locally] --> B[ViT + LLM Extraction: Attribute mapping]
    A --> C[User Feedback: Like/dislike random pairs]
    B --> D[Structured Input Vectors]
    C --> E[User Preference Labels]
    D --> F[Train Model on SageMaker]
    E --> F
    F --> G[Export to .tflite on S3]
    G --> H[Android App (Kotlin)]
    H --> I1[Mode 1: Auto Pairing]
    H --> I2[Mode 2: User-Guided Selection]
    H --> I3[Mode 3: Prompt-Based Recommendation]
    I3 --> J[Remote Agent (EC2)]
    J --> K[Retrieve Similar Items]
    K --> L[Filtered Wardrobe Items]
    L --> M[TFLite Inference in App]

