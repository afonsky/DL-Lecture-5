# 2D convolutional NN visualization on MNIST <a href="https://adamharley.com/nn_vis/cnn/2d.html">[link]</a>

<iframe src="https://adamharley.com/nn_vis/cnn/2d.html" width="1100" height="550" style="-webkit-transform:scale(0.8);-moz-transform-scale(0.8); position: relative; top: -65px; left: -120px"></iframe>

---

# Convolutional Neural Network (CNN)
### CNN is a sequence of convolutional layers, interspersed with activation functions
<br>
<br>
<br>
<div>
  <figure><center>
    <img src="/cnn_layers.png" style="width: 700px !important;">
</center>
    <figcaption style="color:#b3b3b3ff; font-size: 11px; position: absolute;"><br>Image by
      <a href="http://cs231n.stanford.edu/slides/2016/winter1516_lecture7.pdf">Andrej Karpathy</a>
    </figcaption>
  </figure>   
</div>

---

# CNN Architecture
#### Common CNN architecture can be seen as:
<br>

### Input
<br>

### Convolutional blocks
* Convolution + Activation (ReLU)
* Convolution + Activation (ReLU)
* ...
* Maxpooling
<br>
<br>

### Output
* Fully-connected layer(s)
* Softmax

---

# CNN for Deep Learning
## Deep Learning = Learning Hierarchical Representations
### It's deep if it has more than one stage of non-linear feature transformation
<br>
<div>
  <figure><center>
    <img src="/cnn_hierarchical_representation.png" style="width: 500px !important;">
</center>
    <figcaption style="color:#b3b3b3ff; font-size: 11px; position: absolute;"><br>Image by
      <a href="https://drive.google.com/file/d/18UFaOGNKKKO5TYnSxr2b8dryI-PgZQmC/view?usp=share_link">Yann LeCun</a>
    </figcaption>
  </figure>   
</div>

---

# Convolutional Neural Network
## Putting it all together
<br>
<div>
  <figure><center>
    <img src="/cnn_architecture.jpg" style="width: 700px !important;">
</center>
    <figcaption style="color:#b3b3b3ff; font-size: 11px; position: absolute;"><br>Image by
      <a href="http://cs231n.stanford.edu/slides/2016/winter1516_lecture7.pdf">Andrej Karpathy</a>
    </figcaption>
  </figure>   
</div>

---

<br>
<br>
<br>
<br>
<br>
<br>

# <center><huge>CNNs Case Studies</huge></center>

---

# LeNet-5 [LeCun et al., 1998]

<div class="grid grid-cols-[2fr_4fr] gap-8">
<div>

```python {all}
class LeNet5(nn.Module):
    def __init__(self):
        super().__init__()
        self.conv1 = nn.Conv2d(1, 20, 5, 1)
        self.conv2 = nn.Conv2d(20, 20, 5, 1)
        self.fc1 = nn.Linear(4*4*50, 500)
        self.fc2 = nn.Linear(500, 10)

    def forward(self, x):
        x = F.relu(self.conv1(x))
        x = F.max_pool2d(x, 2, 2)
        x = F.relu(self.conv2(x))
        x = F.max_pool2d(x, 2, 2)
        x = x.view(-1, 4*4*50)
        x = F.relu(self.fc1)
        x = self.fc2(x)
    return F.logsoftmax(x, dim=1)
```
</div>
<div>
  <figure><center>
    <img src="/cnn_LeNet-5.png" style="width: 600px !important;">
</center>
  </figure>   
</div>
</div>

* Conv filters were `5x5`, applied at stride `1`
* Subsampling (Pooling) layers were `2x2` applied at stride `2`

---

# AlexNet [Krizhevsky et al., 2012]

<div>
  <figure><center>
    <img src="/cnn_AlexNet.png" style="width: 600px !important;">
</center>
    <figcaption style="color:#b3b3b3ff; font-size: 11px; position: absolute;">Simplified version of Krizhevsky, Alex, Sutskever, and Hinton. "Imagenet classification with deep convolutional neural networks." NIPS 2012
    </figcaption>
  </figure>   
</div>
<br>

Input: $227 \times 227 \times 3$ images
* First layer: 96 filters of size $11 \times 11$ aplied at stride $4$
* Output volume: $55 \times 55 \times 96$
* Total $(11 \times 11 \times 3) \times 96 \approx 35000$ parameters

AlexNet is also provides the first use of ReLU activation (known as ReLU networks).

---

# VGG-16 [Simonyan et al., 2014]

<div>
  <figure><center>
    <img src="/cnn_VGG-16.png" style="width: 700px !important;">
</center>
    <figcaption style="color:#b3b3b3ff; font-size: 11px; position: absolute;">Simonyan, Karen, and Zisserman. "Very deep convolutional networks for large-scale image recognition." (2014)
    </figcaption>
  </figure>   
</div>

---

# ResNet

<div>
  <figure><center>
    <img src="/cnn_ResNet.jpg" style="width: 600px !important;">
</center>
    <figcaption style="color:#b3b3b3ff; font-size: 11px; position: absolute;">"Deep residual learning for image recognition." CVPR. (2016)
    </figcaption>
  </figure>   
</div>
<br>

#### A block learns the residual w.r.t. identity

#### ResNet50 Compared to VGG:
* Superior accuracy in all vision tasks
* 5.25% top-5 error vs 7.1%

---

# State of the art

### Finding right architectures: Active area or research

<div>
  <figure><center>
    <img src="/cnn_sota_1.png" style="width: 550px !important;">
</center>
  </figure>   
</div>
<br>

### Modular building blocks engineering

#### See also: [DenseNets](https://d2l.ai/chapter_convolutional-modern/densenet.html), [ResNet flavours](https://d2l.ai/chapter_convolutional-modern/resnet.html) (Wide ResNets, ResNeXts, Pyramidal ResNets)

<span style="color:grey"><small>From Kaiming He slides "Deep residual learning for image recognition." ICML. (2016)</small></span>

---

# State of the art

### Top 1-accuracy, performance and size on ImageNet

<div>
  <figure><center>
    <img src="/cnn_sota_2.png" style="width: 750px !important;">
</center>
  </figure>   
</div>
<br>

#### See also: https://paperswithcode.com/sota/image-classification-on-imagenet

<span style="color:grey"><small>From Canziani, Paszke, and Culurciello. "An Analysis of Deep Neural Network Models for Practical Applications." (May 2016)</small></span>
