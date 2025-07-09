# Artificial-Dataset-For-Faces

Creating an artificial dataset using Stable Diffusion for different emotions on human faces, which can be further utilized for emotion classification or sentiment analysis.

## Introduction

This project uses the Stable Diffusion technique to generate synthetic images of human faces representing four distinct emotions: **happy**, **sad**, **angry**, and **surprised**. The generated dataset is intended to aid in emotion recognition and sentiment analysis tasks. Each face is conditioned on randomly selected attributes such as ethnicity and gender.

To improve semantic accuracy, the project uses **CLIP-based reranking** to select the most relevant image from multiple generated candidates based on the textual prompt.

## Diffusers

[Hugging Face Diffusers](https://github.com/huggingface/diffusers) is a library for pretrained diffusion models that supports generation tasks like images, audio, and more.

Key features of the library used in this project:
- Pretrained Stable Diffusion pipelines for fast inference.
- Support for negative prompts to filter undesired image features.
- Customizable noise schedulers and model components.

## CLIP-Based Reranking

To ensure the generated image accurately reflects the intended prompt, each image is scored using OpenAI's CLIP model (`clip-vit-base-patch32`). For every prompt:
- Multiple candidates are generated (e.g., 3 per prompt).
- The image with the highest CLIP score is selected and saved.

This process helps filter out poor or off-prompt generations, resulting in a higher-quality dataset.

## Dataset Description

- **Structure**: The dataset is organized into folders by emotion (e.g., `happy/`, `sad/`, etc.).
- **Images per emotion**: Multiple unique samples are saved per emotion, with diversity in ethnicity and gender.
- **Format**: Images are saved in `.png` format and zipped as `faces_dataset.zip`.

Each saved image is the top-ranked output from a batch of multiple generated candidates, scored using CLIP.

## Dataset Usage

This dataset can be used in:
- Emotion recognition tasks
- Facial expression classification
- Synthetic data augmentation
- Training/testing deep learning models in sentiment analysis

