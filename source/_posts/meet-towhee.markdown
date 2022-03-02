---
layout: post
title: 'Meet Towhee: All You Need For X2Vec'
date:   2022-03-01
categories: Towhee
---
## Intro
[Towhee](https://towhee.io/) is dedicated to developing a machine learning platform that focuses on embedding tasks. As  our slogan says, 'X2Vec, Towhee is all you need', we aim to help our users decode the unstructured data into embeddings with a few lines of code.

In this article, we will introduce Towhee, some vital components, along with some demos. 

## Motivation Behind Towhee
The world is full of data, with some data, such as digits and texts, being easily storable, while others, things like images, videos, molecular structures, not being as easy to manage. This hard to store data is what we call unstructured data, and is a growing focus in the machine learning community. In order to be able to understand this data, the field has directed its focus on turning unstructured data into structured data, also known as embedding.

There is one issue, not all data holders and developers are capable of efficiently converting this unstructured data into embeddings. Converting requires deep knowledge in machine learning and also requires large amounts of data that not everyone might have. Not having the ability to analyze this data holds back many users, and because of this, we decided to focus our efforts on unlocking the value of unstructured data to everyone.

Out of this effort comes Towhee, an open-source platform to simplify embedding tasks. Towhee offers everyone the ability to unlock their data within a few lines of code.We made Towhee open-source because we want to build a community, where all the users and developers can contribute their part to promote the development of unstructured data. 

## Essential Components

### Operator
An Operator is the minimum functional unit in Towhee. Each operator has its own specific function. For instance, an 'Image Pre-processing Operator' might rotate and cut input images while an 'Embedding Model Operator' would turn the valid input images into embeddings using a model like Resnet50. 

### Pipeline
A Pipeline is a Directed Acyclic Graph (DAG), where each node is an operator. In Towhee, each pipeline deals with a certain type of embedding task, describing each step that the engine has to take to reach the final result.

Here is a simple example that shows how data flows inside the pipeline:

![image-embedding-pipeline](/images/pipeline.png)

<center>Image Emebedding Pipeline</center>

As indicated in the exmaple above:
1. The user feeds the input image to the Pipeline.
2. The Pre-Process Operator receives the image and does some pre-processing.
3. The Embedding Model Operator receives the processed image and generates the output embedding. 

## Hub
Towhee has built up a hub to store Pipelines, Operators, Datesets(coming soon). Users can create repositories in our hub, and upload their pipelines and operators to hub so that everyone in Towhee community can take advantage of them.

## Demo
In this section, I am going to show a simple pipeline demo on image embedding.
This pipeline simply encodes the input images into embeddings. It consists of two functional operators, namely 'image_decoder' and 'embedding_model'. The decoder loads the input image with cv2 and convert it into a `towhee.Image`. Next, the model operator generates the embedding with specific pre-trained model, which in this case is Resnet50. The user does not need to know how the pipeline works, they create embeddings within 3 lines:
```python
from towhee import pipeline
img_pipeline = pipeline('image-embedding')
embedding = img_pipeline('path/to/your/image')
```
Users can use our pre-defined pipelines from hub by simply telling Towhee their embedding task, which in this case is 'image-embedding'. Towhee will find the corresponding default pipeline either in the local cache or on the hub. For engineers who want to specify the pipeline they prefer:
```python
from towhee import pipeline
my_pipeline = pipeline('author/pipeline_name')
```
We also allow users to load the pipeline by name as long as the pipeline exists in our hub or users' local cache, such codes are supported. 

If the pipeline does not exist, do not worry, we encourage all users to upload their own pipelines or operators to our hub with simple commands so as to develop and activate our community.

## Vision
In the current stage, Towhee is a work-in-progress machine-learning platform. But in the near future, we want to make it an ecosystem that taps into the greater potential of unstructured data. This is why we are so eager to build a like-minded community; together we can make a difference.

---
__<center>You are more than welcome to join our community</center>__

[<img src='/images/towhee_logo.png' width='30' height='30' alt='Towhee'>](https://towhee.io/)

[<img src='/images/github.png' width='30' height='30' alt='GitHub'>](https://github.com/towhee-io/towhee)

[<img src='/images/slack.png' width='30' height='30' alt='Slack'>](https://slack.towhee.io)

[<img src='/images/twitter.png' width='30' height='30' alt='Twitter'>](https://twitter.com/towheeio)
