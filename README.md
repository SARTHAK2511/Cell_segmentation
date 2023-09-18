# Cell_segmentation

In our approach to solving this problem, we have chosen a customized U-Net architecture, a popular choice for image segmentation tasks. Let's delve into the key components and technical details:

**1. U-Net Architecture:**

The U-Net architecture is a convolutional neural network (CNN) known for its effectiveness in semantic segmentation. It consists of an encoder and a decoder, forming a U-shaped network.

**2. Preprocessing**

 I've established a robust image preprocessing pipeline to ready both color (RGB) and black-and-white (BW) images for neural network training. Within this pipeline, RGB images undergo conversion to tf.uint8, uniform resizing to 128x128 pixels, and subsequent normalization to a range of [0, 1]. For BW images, similar resizing occurs, followed by thresholding to generate binary masks. Processed data is stored in images_data and masks_data, then converted to TensorFlow tensors for seamless integration into model training. This meticulous preprocessing ensures standardized, compatible data, setting the foundation for effective neural network training in my project.

**3. Encoder (Downsampler):**

For our encoder, we employ a MobileNetV2 model, initialized with weights pre-trained on a large dataset. The input size for this encoder is set to 128x128 pixels with three color channels.

**4. Decoder (Upsampler):**

The decoder takes the feature maps produced by the encoder and performs the task of upsampling. It gradually increases the spatial resolution of the feature maps to generate a segmentation mask that matches the input image size.
For our decoder, we leverage the upsample block inspired by the pix2pix model. This block employs a combination of upsampling layers and skip connections, allowing the network to capture fine-grained details and spatial information.

**5. Training Process:**

During the training process, we train the model for 40 epochs

For validation, we perform validation on the test dataset
The training process involves optimizing the model's parameters using backpropagation and an appropriate optimizer ( Adam) to minimize the loss.
