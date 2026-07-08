EcoSort: Teaching AI to Recognize Recyclable Materials Through Images
Introduction

Every day, people throw away millions of tons of waste. One challenge with recycling is figuring out what materials objects are made from. Humans can easily tell the difference between a plastic bottle and a glass container, but computers need to learn how to recognize these differences.

For this project, I created EcoSort, an artificial intelligence system that looks at images of waste and predicts what material they contain.

Instead of only asking "Is this recyclable?", EcoSort identifies the specific material:

Cardboard
Glass
Metal
Paper
Plastic
Trash

This gives more useful information because recycling systems can use the material type to decide how an item should be handled.

The dataset used for this project is the TrashNet dataset:

https://github.com/garythung/trashnet

How EcoSort Works

Humans recognize objects by looking at patterns. For example, glass usually has reflections, plastic often has a certain shape and texture, and cardboard has a unique surface appearance.

Computers do not naturally understand these differences. Instead, they learn by studying many examples.

EcoSort was trained by showing an AI model thousands of pictures of different waste materials. The model looked for patterns in these images and learned how to classify new examples.

Examples of images used to train EcoSort.
<img width="1182" height="166" alt="image" src="https://github.com/user-attachments/assets/b8d6f53b-d74c-4a6d-80bd-a49383747bae" />

The Data

EcoSort used the TrashNet dataset, which contains over 2,500 images divided into six categories:

Cardboard
Glass
Metal
Paper
Plastic
Trash

The images were split into three groups:

Training data (70%)
Used to teach the AI model.

Validation data (15%)
Used to check how the model was improving.

Testing data (15%)
Used to measure how well the final model worked on images it had never seen before.

Keeping separate testing data helps make sure the model is actually learning instead of memorizing pictures.

Teaching the AI Model

Instead of building an AI model from the beginning, I used a method called transfer learning.

Transfer learning allows a model that already understands general images to learn a new task faster. It is similar to teaching someone who already knows basic shapes and objects how to identify recycling materials.

The main model used was ResNet-18, a computer vision model that can recognize patterns such as shapes, colors, and textures.

I adapted this model so it could specialize in identifying recycling materials.

Testing Different Methods

To see if EcoSort was actually improving, I compared it against simpler methods.

Random Guessing

This method randomly guesses a category.

Accuracy:
16.4%

This shows what happens when there is no understanding of the images.

Guessing the Most Common Material

This method always predicts the category that appears most often.

Accuracy:
23.4%

It performs slightly better but does not actually analyze the image.

Logistic Regression

This was a basic machine learning method that looked at image information directly.

Accuracy:
46.6%

This showed that simple methods could find some patterns, but they were limited.

CLIP

CLIP is an AI model that can compare images with text descriptions.

For example, it can compare an image with:

"a photo of glass"
"a photo of plastic"

Accuracy:
67.4%

This was impressive because CLIP was not specifically trained on recycling images.

EcoSort Final Model

The final ResNet-18 model achieved:

88.6% Accuracy

This means the model correctly identified the material in almost 9 out of 10 test images.

Comparison of EcoSort against other approaches.
<img width="1189" height="390" alt="image" src="https://github.com/user-attachments/assets/04cca6d3-105e-4e4f-b896-495b70b7071a" />


How Well Did EcoSort Perform?

The model was especially good at identifying:

Metal: 95.2%
Cardboard: 95.1%
Paper: 94.4%
Plastic: 93.2%

These materials usually have clear visual features that make them easier to recognize.

The hardest categories were:

Glass: 76.3%
Trash: 72.7%

Glass was difficult because it can look similar to plastic or metal. Trash was challenging because it contains many different objects that do not share one clear appearance.

Where the model made correct and incorrect predictions.
<img width="565" height="526" alt="image" src="https://github.com/user-attachments/assets/afa956ef-9453-40a7-8f76-2cc34615aa59" />


Understanding Mistakes

Accuracy does not tell the whole story. Looking at mistakes helps explain where the AI struggles.

The most common errors were:

Glass → Plastic
Glass → Metal
Trash → Plastic

These mistakes are understandable because some materials look very similar.

For example, a clear plastic bottle and a glass bottle may have similar shapes, colors, and reflections.

Examples where EcoSort predicted the wrong material.
<img width="1433" height="593" alt="image" src="https://github.com/user-attachments/assets/a352ea47-e07e-4f00-b693-cb1c8c4d6dfc" />


Future Improvements

Although EcoSort performed well, there are still improvements that could make it more useful in real recycling systems.

The current dataset contains mostly clean images with one object at a time. Real recycling environments are more difficult because objects may be:

Dirty
Damaged
Overlapping
Poorly lit

Future improvements could include:

Training on larger real-world recycling datasets
Detecting multiple objects in one image
Creating a mobile app version
Connecting the model to automated sorting machines
Conclusion

EcoSort shows how artificial intelligence can help improve recycling by identifying materials from images.

The project demonstrated that AI can learn to recognize different waste materials and achieve much higher accuracy than simple methods.

While AI cannot solve the entire waste problem by itself, systems like EcoSort could help make recycling faster, easier, and more efficient.
