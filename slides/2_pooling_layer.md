# Pooling Layer
<div></div>

The pooling layer (**POOL**) is a downsampling operation, typically applied after a convolution layer, which does some spatial invariance. Most popular kinds of pooling:
<div class="grid grid-cols-[2fr_1fr] gap-3">
<div>

* **Max pooling**
  * Selects maximum value of the current view
  * Preserve detected features
  * Most commonly used
</div>
<!-- <div>
<br>
```python {all}
m = nn.MaxPool2d(2, stride=2)
input = torch.randn(20, 16, 50)
output = m(input)
```
</div> -->
<div>
  <figure>
    <img src="/max-pooling-a.png" style="width: 250px !important;">
  </figure>  
</div>
</div>

<div class="grid grid-cols-[2fr_1fr]">
<div>

* **Average pooling**
  * Averages the values of the current view
  * Downsamples feature map
  * Used in LeNet
</div>
<div>
  <figure>
    <img src="/average-pooling-a.png" style="width: 250px !important;">
  </figure>
</div>
</div>
<span style="color:grey"><small>Gifs are from <a href="https://stanford.edu/~shervine/teaching/cs-230/cheatsheet-convolutional-neural-networks">Convolutional Neural Networks cheatsheet</a></small></span>

---

# Pooling properties
<br>

* Pooling aggregate results over a window of value

* Pooling leaves the number of channels unchanged and it applies to each channel separately

* Max-pooling is preferable to average pooling, as it confers some degree of invariance to output

* A popular choice is to pick a pooling window size of $2\times 2$ to quarter the spatial resolution of output