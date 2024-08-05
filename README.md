# Computer-Vision-Project-on-Ground-To-Aerial-Matching

The goal of cross-view image based geo-localization is to determine the location of a given street view image by matching it against a collection of geo-tagged satellite images. This task is particularly challenging due to the significant differences in viewpoints and appearances between the two domains. Despite these difficulties, research in this field continues to progress, driven by its potential applications in navigation, autonomous vehicles, urban planning, and emergency response.

In this project we will do an analysis on a Ground-To-Aerial Matching task, we have taken inspiration from an existing paper and wanted to expand the research testing other architectures and giving the model new inputs generated by us in the other notebook.

**Dataset Creation**:
- We created a custom dataset class utilizing a portion of the CVUSA dataset, along with additional inputs generated from our other notebooks.

 **Model Architecture**: We implemented a Siamese-like network architecture with various configurations:
   - **Dual, Quad, Hex, and Octa architectures**: These architectures allow us to explore different kinds of networks.
   - Each architecture follows three main structures:
     - **Fully Combined**: Every branch shares weights within a single model.
     - **Half Combined**: Each half of the architecture shares a model.
     - **Non-Combined**: Each branch has its own independent model.

 **Model Backbones**: We experimented with two widely used backbone models:
 
  **VGG16**
  
  - We utilize the pretrained VGG16 model, focusing exclusively on its convolutional layers.
  - We add our custom fully connected layer at the end of the convolutional part.
   
  **ResNet50**:
  
  - We used the entire pretrained ResNet50 model, which includes both convolutional and FC layers.

For the Dataset we started with aerial and street images from the CVUSA subset we got from the paper, and augmented it generating many new inputs types:

1. **SIFT Images**: Scale-Invariant Feature Transform (SIFT) images, which capture key feature points for image matching and recognition tasks.
2. **Depth Maps**: Maps that provide information about the distance of the surfaces of scene objects from a viewpoint.
3. **Segmentation Maps**: Images that assign a label to each pixel, identifying which part of the image belongs to different objects or regions.
4. **Polar Transformation**: Only applied to aerial images, it produces image pairs that better align with the content of the scene, maintaining a similar arrangement of objects.

All considered, the model that reached peak performances after an extensive training of all our options is the OCTA-Non-Combined-VGG:

[photo]

