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
    A[🧥 Image Upload<br/>Wardrobe items selected by user and stored locally] --> B[🔍 ViT + LLM Attribute Extraction<br/>OpenAI API extracts user-relevant attributes and maps to model input]
    A --> C[🤖 User Feedback<br/>Random outfit pairs shown for like/dislike labeling]
    B --> D[🔢 Structured Input Vectors]
    C --> E[❤️ User Preference Labels]

    D & E --> F[🧠 Train Deep Learning Model<br/>on AWS SageMaker using attributes and preferences]

    F --> G[💾 Export TFLite Model<br/>Model uploaded to S3 for app use]
    G --> H[📱 Android App (Kotlin)]

    H --> I1[🔁 Recommendation (Default Mode)<br/>Random pairing, first liked result shown]
    H --> I2[🧭 User-Driven Recommendation<br/>User selects item, paired until liked combo found]
    H --> I3[💬 Prompt-Based Recommendation<br/>User enters free-form prompt]

    I3 --> J[🛰️ Server-side Agent (AWS EC2)<br/>Classifies prompt and fetches relevant clothing]
    J --> K[📦 Filter Wardrobe for Relevant Items<br/>Based on similarity-matched embeddings]

    K --> H
