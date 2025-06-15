+ Let's consider a set of **images** $X$ and a set of **labels** $Y$
+ There is a large family of problems in which we are required to label an image, or sections of an image with a specific label (**classification problem**)
+ Examples of varying complexity are:
	+ **Image** Classification (+ localization): label the whole image
	+ **Object** Recognition: recognize classes of objects in the image
	+ **Instance** Recognition: Recognize specific instances of an object in an image
	+ Object **Detection**: detect objects in an image
	+ **Instance Segmentation**: detect and segment different objects in an image
	+ **Semantic** segmentation: segment the image in complementary segments, each associated to a label. each pixel is associated to a label
+ An important factor in these problems is the **representation** of the images.
+ They must be **robust to intra-class variations** of different types
+ Possible representations may be:
	+ Pixels (not so robust)
	+ Gray-levels/color/gradient histograms (not too descriptive)
	+ Local key-points, in **Bag of key-points** (still too “hand-crafted”)
		+ This method was inspired by analogous ones in text-based contexts. 
		+ Sadly it requires too much input by the programmer, and working on just one scale is a big limitation
+ We could also just learn the features directly from the data, using CNNs
+ This **requires lots of data** (real, augmented, synthetic, etc.)
---
+ Now, we focus on **Object Detection** and its variants
+ The classical approach for it is, simply, **brute-force**: Using a **sliding window**, we scan all the possible sections of the image, and look for matches. Found the best ones, we use non-maxima suppression to find the best 
	+ *If we think about it, it can remind us of how CNNs work...*
+ CNNs based methods are for example
	+ **Region-based CNN** (R-CNN family) (Two stage CNN detectors)
	+ **YOLO** family (One stage CNN detectors)
		+ *Quite complex methods*
---
+ A metric to evaluate the performance of a object detector is the **Intersection Over Union** (IOU): $$IOU = \cfrac{\cap(\text{Ground Truth, Prediction})}{\cup(\text{Ground Truth, Prediction})}$$
+ Another two **metrics** are Precision ad Recall:
	+ **Precision** is "How many retrieved items are relevant?" $$ P= \cfrac{TP}{TP+FP}$$
	+ **Recall** is "How many relevant items are retrieved?" $$R = \cfrac{TP}{TP+FN}$$
+ In the case of **multi-class object detection**, we use instead a **confusion matrix** 
	+ The average of its diagonal is considered the **mean accuracy**
### R-CNNs
+ **Region-based Convolutional Neural Networks** (R-CNNs) are a DL approach to object detection which is kind of an evolution of the sliding window approach
+ Instead of considering all possible regions of the image, we have a pre-processing stage in which we detect all possible **candidate regions** which have a chance of being meaningful (around 2000)
+ The search fo the regions can be done in multiple ways:
	+ **Selective Search** algorithms are unsupervised segmentation approach which, based on color and shapes, iteratively compute candidate regions. It is designed to have high recall and small precision. It's still a bit slow...
	+ A speed up can be obtain by first learning with a CNN the feature of the image, and then select the regions **in the feature space** (**Fast R-CNN**)
		+ Working in the feature space makes us lose a bit of information because of cropping, but it is negligible
	+ An even greater speed up can be obtained if, instead of using SS, we just use a **Region Proposal Network** to predict the region proposal from the features (**Faster R-CNN**)
		+ The network uses a system of **anchor points** and **anchor boxes** to detect possible regions
### Mask R-CNNs
+ Those networks are evolutions of Faster R-CNNs specialized for the problem of **Instance Segmentation**
+ We add a third final section which computes a **mask** for the segmentation of the detected object
+ We need to **minimize the loss of information**, and as such we have a modified middle section, the **RoI Align**
	+ Compared to RoI Pooling, it avoids quantization, using **bilinear interpolation** to **compress** and store **information** about the pixels
### Semantic Segmentation
+ A first approach would be the classic **sliding window**, but it would be quite **inefficient**. Also, it would not reuse shared features
+ We could then go to a **fully convolutional** network. We would need to avoid pooling, such that we do not lose track of the pixel's meaning. But this would make the convolutions **quite expensive**
+ Instead, we use an approach reminiscent of **autoencoders**: we down-sample the data in the network and then **upsample** to return to the original size
	+ We'll need to do **unpooling** and **transposed convolution** (*details in notes and slides...*)
+ **Implementations** of this approach are:
	+ **UNET**>: (It includes some skip-connections, to preserve information between levels)
	+ **LinkNet**
	+ **Pyramid Scene Parsing Network**
	+ **Feature Pyramid Network**
### Depth Estimation
+ This problem **isn't that different from the previous**, we still want to classify each pixel with a class, its **depth value**
+ We could even learn from a single image, without stereopsis
+ The main methods are classified in two categories:
	+ **Global**: Designing a complex network that is powerful enough to directly regress the depth map
	+ **Local**: Splitting the input into bins or windows to reduce computational complexity
+ A clever method is **M4Depth**, which is based on the idea of estimating the roto-translation between two frames in a video, and use it to compute the depth
+ This field is mostly **limited** by the **lack of ground truth datasets** for supervised learning