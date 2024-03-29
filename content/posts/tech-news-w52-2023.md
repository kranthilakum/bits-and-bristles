---
title: Tech News w52 2023
date: 2023-12-12T09:55:46+05:30
draft: false
categories:
- "tech-news"
tags:
- "programming"
- "tech-news"
---

## AWS Titan Image Generator

Titan Image Generator has the capability to generate new images based on a text description or customize existing images.

## Git Partial Clone


Partial clones represent a streamlined version of git clones initiated through specific command line arguments. Repositories that employ partial clones have demonstrated an average reduction of 88.6% in cloning time. Partial clones offer improved performance compared to traditional clones, particularly benefiting large repositories.

Unlike traditional clones, partial clones don't retrieve every historical object in the repository during the initial clone. Instead, they postpone the download of numerous objects until the checkout of a branch or other git scenarios requiring them.

## Google Distilling Step-by-Step

Google Research recently open-sourced Distilling Step-by-Step, a technique for fine-tuning smaller language models. Distilling Step-by-Step requires less training data than standard fine-tuning and results in smaller models that can outperform few-shot prompted large language models (LLMs) that have 700x the parameters.

https://blog.research.google/2023/09/distilling-step-by-step-outperforming.html

## Microsoft Orca 2

Microsoft Research released its Orca 2 LLM, a fine-tuned version of Llama 2 that performs as well as or better than models that contain 10x the number of parameters. Orca 2 uses a synthetic training dataset and a new technique called Prompt Erasure to achieve this performance.

Orca 2 models are trained using a teacher-student scheme, where a larger, more powerful LLM acts as a teacher for a smaller student LLM, with the goal of improving the performance of the student to be comparable with that of a larger model. Microsoft's training technique teaches the smaller model multiple reasoning techniques and also how to choose the most effective technique for a given task. To do this, the teacher is given sophisticated prompts to trigger a certain reasoning behavior. However, in a scheme called Prompt Erasure, the student is given only the task requirements and desired response, but not the teacher's prompt. When evaluated on benchmarks, a 13B parameter Orca 2 model outperformed a baseline 13B parameter Llama 2 by 47.54%. The 7B parameter Orca 2 was "better or comparable" to a 70B parameter Llama 2 on reasoning tasks.

Although LLMs like ChatGPT can often perform well on a wide range of tasks with few-shot prompting, hosting the models is challenging due to their memory and compute requirements. Smaller models can also perform well when fine-tuned, and many researchers have investigated training them with synthetic datasets generated by larger LLMs. 

[Orca](https://www.microsoft.com/en-us/research/project/orca/)

## JHipster 8.0 Released

JHipster, the web and microservices applications generator, has recently released version 8.0. New features in this release include setting HashiCorp Consul as the default service discovery mechanism, support for Development Containers, and the enabling of Cross-Origin Resource Sharing (CORS) for each application that acts as a gateway or is a monolith. Support for both JDK 20 and 21 was added, allowing users to take advantage of previews of simplified structured concurrency (JDK 21) or the second preview of record patterns (JDK 20). Upgraded to Hibernate 6.2.x (unlocking support for Java records and STRUCT types), and build tools were upgraded to Maven 3.9.5 and Gradle 8.4. The project is now on the Spring Boot 3.x release train. The Node.js dependency was bumped to 18.17.1, adopting the Node 18 LTS. Angular was upgraded to version 16, Vue was upgraded to version 3. Vite will be used as the build tool for Vue projects, and Prettier was upgraded to version 3. Node users will also have access to the Fetch API. Spring Boot 3.2 and Angular 17 might be available in an upcoming version, 8.1.0, sometime in December 2023.

- [JHipster 8 Demo Tutorial](https://github.com/mraible/jhipster8-demo#readme)
- [JHipster online](https://start.jhipster.tech/)
- [JHipster issue tracker](https://github.com/jhipster/generator-jhipster/issues?q=is%3Aopen)

## Stable Video Diffusion (SVD)

Stability AI released the code and model weights for Stable Video Diffusion (SVD), a video generation AI model. When given an input image as context, the model can generate 25 video frames at a resolution of 576x1024 pixels.

The model is based on Stability's Stable Diffusion text-to-image generation model, with additional video pre-training and fine-tuning using a high-quality curated dataset. To perform this additional training, Stability collected a dataset called Large Video Dataset (LVD), which contains 580M video clips representing 212 years of runtime. While the initial model release only supports image-to-video generation, Stability AI claims it can be adapted for multiple video generation tasks, including text-to-video and multi-view (i.e., 3D object) generation.

Building SVD required to collect and annotate a large dataset of videos. Starting with raw video, the team first removed motion inconsistencies such as "cuts" as well as videos with no motion at all. They then applied three synthetic captions to each clip using an image-only caption model, a video caption model, and an LLM to combine the two. They also used CLIP to extract aesthetic scores for selected frames in the video samples. After training a base video diffusion model on the large dataset, the researchers used smaller curated datasets to fine-tune task-specific models for text-to-video, image-to-video, frame-interpolation, and multi-view generation. They also trained LoRA camera-control blocks for the image-to-video model. The multi-view generation model outperformed state-of-the-art models Zero123 and SyncDreamer. When evaluated by human judges, the output of the image-to-video model was preferred over that generated by state-of-the-art commercial products GEN-2 and PikaLabs.

[Stable Video Diffusion](https://github.com/Stability-AI/generative-models)

## LinkedIn Espresso

LinkedIn uses Espresso, the document platform built on top of MySQL, to store and serve most of its data. LinkedIn was able to dramatically improve the scalability and performance of its Espresso database by migrating it from HTTP/1.1 to HTTP/2, resulting in a reduction in the number of connections, latency, and garbage collection times. To achieve these gains, the team had to optimize the Netty's default HTTP/2 stack to make it fit their needs. With the organic growth of LinkedIn’s platform, the volume of data is increasing, forcing the company to constantly expand the footprint of Espresso clusters and work on optimizations, such as introducing a centralized caching layer for Espresso or adopting Protocol Buffers for its inter-service communication.