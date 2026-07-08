# EcoSort---Artificial-Neural-Networks

EcoSort: Teaching AI to Recognize Recyclable Materials Through Images
Introduction

Every day, millions of tons of waste are produced around the world. One challenge in improving recycling systems is correctly identifying what materials are being thrown away. A plastic bottle, a piece of cardboard, and a glass container may look simple to humans, but separating them automatically requires a computer to understand images.

For this project, I created EcoSort, an artificial intelligence system that analyzes images of waste and predicts what material they contain. The goal was not just to build a model that says whether something is recyclable, but to teach the AI to recognize the specific material type: cardboard, glass, metal, paper, plastic, or general trash.

The dataset used for training and testing can be accessed here:

TrashNet Dataset: https://github.com/garythung/trashnet

The Idea Behind EcoSort

When humans look at an object, we automatically recognize patterns. We know that a shiny object with reflections is probably glass, or that a thin flexible container is likely plastic. Computers do not naturally understand these concepts. Instead, they need to learn patterns from many examples.

EcoSort works by showing an AI model thousands of labeled waste images. Over time, the model learns visual differences between materials and becomes better at predicting what category a new image belongs to.

Rather than creating a simple recyclable/non-recyclable classifier, I decided to make the problem more detailed. The model first identifies the material type, and then recyclability can be determined from that prediction. For example:

Cardboard → recyclable
Glass → recyclable
Metal → recyclable
Paper → recyclable
Plastic → recyclable
Trash → non-recyclable

This approach gives more useful information than only predicting a yes/no recycling label.

Understanding the Data

To train EcoSort, I used the TrashNet dataset, which contains images divided into six categories:

Cardboard
Glass
Metal
Paper
Plastic
Trash

The dataset contains over 2,500 images of waste items. Before training the AI, I organized the images into three groups:

Training data (70%) — used to teach the model
Validation data (15%) — used to monitor progress while training
Testing data (15%) — used to measure final performance

Keeping separate testing images is important because it shows whether the model can recognize new examples instead of simply memorizing the images it has already seen.

Dataset Distribution

Building the AI Model

Instead of creating an AI model completely from scratch, I used a technique called transfer learning.

The idea is similar to teaching someone who already understands basic concepts. Rather than starting from zero, the model begins with knowledge learned from millions of previous images and then adapts that knowledge to recycling images.

The main model used was a computer vision model called ResNet-18. It was originally trained on a large collection of everyday images, allowing it to already understand useful visual patterns such as shapes, textures, and edges.

I adjusted the final part of the model so it could specialize in recognizing recycling materials.

Comparing Different Approaches

To understand whether the AI was actually learning useful information, I compared it against several simpler approaches.

Random Guessing

This method simply guesses a category randomly. It achieved about:

16.4% accuracy

This represents the minimum performance expected from a model with no useful understanding.

Always Guessing the Most Common Category

This approach always predicts the material that appears most often in the dataset.

Accuracy:

23.4%

Although slightly better than random guessing, it does not actually understand images.

Logistic Regression

This was a basic machine learning approach that looked at image pixels directly.

Accuracy:

46.6%

This showed that some patterns exist in the images, but a more advanced vision model was needed.

CLIP Zero-Shot Model

I also tested a model called CLIP, which can compare images with text descriptions without additional training. For example, it can compare an image against phrases like:

"a photo of glass"
"a photo of plastic"

Accuracy:

67.4%

This was impressive because the model had never specifically been trained on this recycling dataset.

ResNet-18 Fine-Tuned Model

The final EcoSort model achieved:

88.3% material classification accuracy

This was significantly better than every other approach.

Model Comparison

What Did the Model Do Well?

The AI performed especially well when identifying:

Cardboard: 95.1% accuracy
Metal: 95.2% accuracy
Paper: 94.4% accuracy
Plastic: 93.2% accuracy

These materials often have strong visual patterns that make them easier to distinguish.

The model struggled more with:

Glass: 76.3% accuracy
Trash: 72.7% accuracy

These categories were harder because they contain more visual variety. For example, glass objects can have different shapes, colors, reflections, and transparency, making them harder for an AI system to separate from plastic or metal.

Looking at the Mistakes

Accuracy alone does not explain everything. I also examined examples where the AI made incorrect predictions.

The most common mistakes were:

Glass → Plastic
Glass → Metal
Trash → Plastic

These mistakes make sense because many recycling materials share similar appearances. A clear plastic container and a glass bottle may have similar shapes and colors, making them difficult for an AI model to separate.

Understanding these mistakes is important because it shows where future improvements should focus.

An Additional Experiment: Understanding Images Without Training

One interesting part of this project was testing whether AI models could recognize recycling materials without being specifically trained on this dataset.

Using CLIP and image embeddings, I tested models that relied more on previously learned visual knowledge.

The results showed that pretrained AI models already understand some material concepts, but a specialized recycling model performs better when accuracy is the main goal.

This suggests that combining general AI knowledge with specialized training can create stronger environmental applications.

Limitations and Future Improvements

Although EcoSort performed well, there are still limitations.

The dataset contains mostly clean images with a single object in each picture. Real-world recycling environments are much more complicated. A camera in a recycling facility might encounter:

Multiple objects in one image
Dirty or damaged materials
Different lighting conditions
Objects partially hidden from view

Future improvements could include:

Training on larger real-world recycling datasets
Detecting multiple objects in one image
Deploying the model into a mobile application
Connecting predictions to automated sorting systems
Conclusion

EcoSort demonstrates how artificial intelligence can help address environmental challenges by improving how we identify and sort recyclable materials.

The project showed that a carefully trained computer vision model can recognize waste materials with high accuracy, outperforming simpler approaches and even general-purpose AI models.

While AI alone cannot solve the global waste problem, tools like EcoSort can contribute to smarter recycling systems by making sorting faster, more consistent, and more efficient.
