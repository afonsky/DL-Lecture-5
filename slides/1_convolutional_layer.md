# <center>Neural networks so far</center>
<br>
<br>

<div>
<center>
  <figure>
    <img src="/nn_patterns_1.png" style="width: 550px !important;">
  </figure>
</center>
</div>
<br>
<br>

# <center>Can recognize patterns in data (e.g. digits)</center>
<br>
<br>
<br>
<span style="color:grey"><small>Slides 20-26 are adapted from <a href="https://deeplearning.cs.cmu.edu/F22/document/slides/lec9.CNN1.pdf">Bhiksha Raj's slides</a></small></span>

---

# <center>The weights look for patterns</center>

<br>

<div>
<center>
  <figure>
    <img src="/nn_patterns_2.png" style="width: 620px !important;">
  </figure>
</center>   
</div>
<br>

### The green pattern looks more like the weights pattern (black) than the red pattern
* The green pattern is more *correlated* with the weights

---

# <center>Flower</center>
<br>

<div>
<center>
  <figure>
    <img src="/nn_patterns_3.jpg" style="width: 650px !important;">
  </figure>
</center>    
</div>
<br>
<br>

# <center>Is there a flower in any of these images?</center>

---

# <center>Flower</center>
<br>

<div>
<center>
  <figure>
    <img src="/nn_patterns_4.jpg" style="width: 650px !important;">
  </figure>
</center>   
</div>
<br>

* Will a NN that recognizes the left image as a flower<br> also recognize the one on the right as a flower?
* Need a network that will “fire” regardless of the precise location of the target object

---

# The need for shift invariance
<br>

* In many problems the location of a pattern is not important
  * Only the presence of the pattern is important
* Conventional NNs are sensitive to location of pattern
  * Moving it by one component results in an entirely different
input that the NN won't recognize
* Requirement: Network must be **shift invariant**

---

# Solution: Scan

<div>
<center>
  <figure>
    <img src="/nn_patterns_5.jpg" style="width: 600px !important;">
  </figure>
</center>   
</div>

### Scan for the desired object
* “Look” for the target object at each position
* At each location, entire region is sent through NN

---

# Solution: Scan

<div>
<center>
  <figure>
    <img src="/nn_patterns_6.jpg" style="width: 550px !important;">
  </figure>
</center>   
</div>

### Determine if any of the locations had a flower
* Each neuron in the right represents the output of the NN when it classifies one location in the input figure
* Look at the maximum value
  * Or pass it through a simple NN (e.g. linear combination + softmax)

---

# Convolutional Layer

### This scan-like approach is realized in **convolution layers** of NNs:

<div>
<center>
  <figure>
    <img src="/conv_2D_1.gif" style="width: 550px !important;">
  </figure>
</center>   
</div>

* Blue (lower) matrix is $5\times 5$ **input**
* Dark blue (shade) is $3\times 3$ **kernel** (a.k.a. **filter**)
* Cian (upper) matrix is $3\times 3$ **output** (a.k.a **feature map** or **activation map**)


<br>
<span style="color:grey"><small>Gifs are from <a href="https://arxiv.org/abs/1603.07285">A guide to convolution arithmetic for deep learning</a> by Vincent Dumoulin and Francesco Visin</small></span>

---

# Convolutional Layer (1D)
<div>
<center>
  <figure>
    <img src="/conv_1D_1.gif" style="width: 350px !important;">
  </figure>
</center>   
</div>

#### A convolution is an operation between two signals: input and kernel.

#### To get the convolution output of an input vector and a kernel:
- **Slide the kernel** at each different possible positions in the input
- For each position, perform the **element-wise product** between the kernel and the corresponding part of the input
- **Sum** the result of the element-wise product

<br>
<span style="color:grey"><small>Gifs are from <a href="https://arxiv.org/abs/1603.07285">A guide to convolution arithmetic for deep learning</a> by Vincent Dumoulin and Francesco Visin</small></span>

---

# Convolutions in 2D: example

<br>
<br>
<br>
<figure>
  <img src="/convolutions_1.png" style="width: 500px !important;">
</figure>

---

# Convolutions in 2D: example

<br>
<br>
<br>
<figure>
  <img src="/convolutions_2.png" style="width: 500px !important;">
</figure>

---

# Convolutional Layer
<div></div>

Assuming the given input $I$ with respect to its dimensions, we can select the following
**hyperparameters** of the convolution layer:
* Kernel (**Filter**) size $F$
* **Stride** $S$ - the number of *pixels* by which the window moves after each operation
* **Zero-padding** $P$ - the number of zeroes at each side of the boundaries of the input

<div class="grid grid-cols-[5fr,2fr]">
<div>
<center>
  <figure>
    <img src="/conv_layer_1.png" style="width: 450px !important;">
  </figure>
</center>   
</div>
<div>
<br>
<br>
<br>
Therefore:

  $\boxed{O = \frac{I - F + 2P}{S} + 1}$
</div>
</div>

<br>
<br>
<span style="color:grey"><small>Images are from <a href="https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-convolutional-neural-networks">Convolutional Neural Networks cheatsheet</a></small></span>

---

# Convolutional Layer: multiple channels
<div></div>

You can use have : multiple channels in input. A color image usually have 3 input channels: RGB.
Therefore, the kernel will also have channels, one for each input channel.

<div class="grid grid-cols-[5fr_3fr] gap-8">
<div>
  <figure>
    <img src="/conv-2d-in-channels.gif" style="width: 550px !important;">
  </figure>  
</div>
<div>
  <figure>
    <img src="/conv-2d-out-channels.gif" style="width: 400px !important;">
  </figure>
</div>
</div>

<br>
<span style="color:grey"><small>Gifs are from <a href="https://github.com/theevann/amld-pytorch-workshop/blob/master/6-CNN.ipynb">the PyTorch Workshop at Applied ML Days 2019</a></small></span>

---

# Images as Functions

### No change:
<br>
  <figure>
    <img src="/im_no_change.gif" style="width: 500px !important;">
  </figure>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="color:grey"><small>Gifs are from <a href="https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html">https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html</a></small></span>

---

# Images as Functions

### Shifted right by one pixel:
<br>
  <figure>
    <img src="/im_1_pixel_right.gif" style="width: 500px !important;">
  </figure>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="color:grey"><small>Gifs are from <a href="https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html">https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html</a></small></span>

---

# Images as Functions

### Blurred:
<br>
  <figure>
    <img src="/im_blurred.gif" style="width: 500px !important;">
  </figure>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="color:grey"><small>Gifs are from <a href="https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html">https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html</a></small></span>

---

# Images as Functions

### How to obtain sharpened image?

Step 1: Original - Smoothed = "Details"
<br>
  <figure>
    <img src="/sharpening1.png" style="width: 570px !important;">
  </figure>
<br>


<span style="color:grey"><small>Images are from <a href="https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html">https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html</a></small></span>

---

# Images as Functions

### How to obtain sharpened image?

Step 2: Original + "Details" = Sharpened
<br>
  <figure>
    <img src="/sharpening2.png" style="width: 590px !important;">
  </figure>
<br>


<span style="color:grey"><small>Images are from <a href="https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html">https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html</a></small></span>

---

# Images as Functions

### Sharpened:
<br>
  <figure>
    <img src="/im_sharpened.gif" style="width: 570px !important;">
  </figure>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="color:grey"><small>Gifs are from <a href="https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html">https://ai.stanford.edu/~syyeung/cvweb/tutorial1.html</a></small></span>

---

# Image Kernels Explained Visually <a href="https://setosa.io/ev/image-kernels/">[link]</a>

<iframe src="https://setosa.io/ev/image-kernels/" width="1100" height="550" style="-webkit-transform:scale(0.8);-moz-transform-scale(0.8); position: relative; top: -65px; left: -120px"></iframe>

---

# Convolutions properties

* The convolution detects the presence of a pattern in the image which is defined by the filter

* The stronger the pattern on the image section, the larger the convolution value will be

* The result of convolution of the image with the filter is a new image

* The convolution maximum is invariant to shifts

* Local connectivity
  * A pixel in the resulting image depends only on a a small portion of the original image

* Shared weights
  * The weights are the same for all pixels in the resulting image