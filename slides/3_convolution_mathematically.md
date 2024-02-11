# Mathematical formulation of translation invariance

#### Starting from Multilayer Perceptron
* Suppose that $\mathbf{X}$ is input matrix and $\mathbf{H}$ is corresponding hidden representation and they both have the same shape
* Let $[\mathbf{X}]_{i, j}$ and $[\mathbf{H}]_{i, j}$ denote the pixel
at location $(i,j)$
* We want that  a shift in the input $\mathbf{X}$ should simply lead to a shift in the hidden representation $\mathbf{H}$:
$$\begin{aligned} \left[\mathbf{H}\right]_{i, j} &= [\mathbf{U}]_{i, j} + \sum_k \sum_l[\mathsf{W}]_{i, j, k, l}  [\mathbf{X}]_{k, l}\\ &=  [\mathbf{U}]_{i, j} +
\sum_a \sum_b [\mathsf{V}]_{i, j, a, b}  [\mathbf{X}]_{i+a, j+b}\end{aligned}$$
* This is only possible if $\mathsf{V}$ and $\mathbf{U}$ do not actually depend on $(i, j)$

---

# Mathematical formulation of translation invariance
<div></div>

$$\begin{aligned} \left[\mathbf{H}\right]_{i, j} &=  [\mathbf{U}]_{i, j} +
\sum_a \sum_b [\mathsf{V}]_{i, j, a, b}  [\mathbf{X}]_{i+a, j+b}\end{aligned}$$

* We have $[\mathsf{V}]_{i, j, a, b} = [\mathbf{V}]_{a, b}$ and $\mathbf{U}$ is a constant, say $u$
	* As a result, we can simplify the definition for $\mathbf{H}$:

$$[\mathbf{H}]_{i, j} = u + \sum_a\sum_b [\mathbf{V}]_{a, b}  [\mathbf{X}]_{i+a, j+b}$$

* This is a **convolution**!
We are effectively weighting pixels at $(i+a, j+b)$
in the vicinity of location $(i, j)$ with coefficients $[\mathbf{V}]_{a, b}$
to obtain the value $[\mathbf{H}]_{i, j}$

<br>

#### Note that $[\mathbf{V}]_{a, b}$ needs many fewer coefficients than $[\mathsf{V}]_{i, j, a, b}$ since it no longer depends on the location within the image


---

# Mathematical formulation of locality

* We believe that we should not have to look very far away from location $(i, j)$ in order to glean relevant information to assess what is going on at $[\mathbf{H}]_{i, j}$
	* This means that outside some range $|a|> \Delta$ or $|b| > \Delta$,
we should set $[\mathbf{V}]_{a, b} = 0$
	* Equivalently, we can rewrite $[\mathbf{H}]_{i, j}$ as

$$[\mathbf{H}]_{i, j} = u + \sum_{a = -\Delta}^{\Delta} \sum_{b = -\Delta}^{\Delta} [\mathbf{V}]_{a, b}  [\mathbf{X}]_{i+a, j+b}$$

* This reduces the number of parameters from $4 \times 10^6$ to $4 \Delta^2$, where $\Delta$ is typically smaller than $10$
	* As such, we reduced the number of parameters by another four orders of magnitude

---
# Convolutions
#### Why such equation is called **convolution**?

* In mathematics, the *convolution* between two functions, say $f, g: \mathbb{R}^d \to \mathbb{R}$ is defined as
$$(f * g)(\mathbf{x}) = \int f(\mathbf{z}) g(\mathbf{x}-\mathbf{z}) d\mathbf{z}$$
* We measure the overlap between $f$ and $g$ when one function is "flipped" and shifted by $\mathbf{x}$
* Whenever we have discrete objects, the integral turns into a sum:
$$(f * g)(i) = \sum_a f(a) g(i-a)$$
* In 2D, we have a corresponding sum
with indices $(a, b)$ for $f$ and $(i-a, j-b)$ for $g$:
$$(f * g)(i, j) = \sum_a\sum_b f(a, b) g(i-a, j-b)$$

