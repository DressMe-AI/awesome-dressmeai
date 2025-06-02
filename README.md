# Awesome DressMe.AI

> A curated collection of repositories powering the DressMe.AI platform — an intelligent outfit recommendation system using vision-language models and deep learning.

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

```text
[Image] --(ViT + LLM)--> [Attribute JSON]
                          ↓
         [Annotated user choices / preferences]
                          ↓
                   [DNN Model Training]
                          ↓
               [TFLite Export + Android App]
