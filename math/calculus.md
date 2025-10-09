Calculus
========================
# Partial Differentiation
## Partial Derivative
* For multivariate functions, the partial derivative of a function $f(x, y)$ wrt $x$ is defined as:

$$
f_x(x, y) = \lim_{\Delta x \rightarrow 0} \frac{f(x + \Delta x, y) - f(x, y)}{\Delta x}
$$

* Practically that means $y$ is treated as constant when differentiating wrt $x$.  

## Gradient
* Gradient is a vector of partial derivatives

$$
\nabla f(x, y) = (f_x(x, y), f_y(x, y))
$$

## Chain Rule
* The chain rule for multivariate calculus:

$$
\frac{d}{dt} f(x, y) = f_x(x, y) \frac{dx}{dt} + f_y(x, y) \frac{dy}{dt} = \nabla f(x, y) \cdot \left( \frac{dx}{dt}, \frac{dy}{dt} \right)
$$

* Differential form:

$$
df = \nabla f \cdot (dx, dy)
$$


## Linear Approximation
* If we approximate, the differential $dx$, $dy$ with a finite change in $x$ and $y$ from $a$ and $b$ respectively we get a final linear approximation near $a$ and $b$.

$$
f(x, y) - f(a, b) = f_x(a, b) (x - a) + f_y(a, b) (y - b)
$$

## Directional Derivatives
* We can get the derivative in any direction represented by unit vector $u$. This is defined as:

$$
D_u f(x, y) = \nabla f(x, y) \cdot u
$$

* Thus we see that $f_x(x, y)$ is the derivative along the direction $(1, 0)$.

## Geometry of Gradients
* Gradients always point in direction of steepest ascent.
  * In other words, directional derivative is maximized when unit vector $u$ points in the direction of derivative.  
  * From the definition of directional derviatives, the dot product $u \cdot \nabla f(x, y)$ is maximized when both vectors point in the same direction.
* Gradients are normal to level curves.
  * A level curve at $c$ is defined as any $(x, y)$ where $f(x, y) = c$.
  * Parameteric version: $f(r(t)) = c$ where $r$ is a level curve. 
  * Take derivative of $t$ from both sides: $\nabla f(r(t)) \cdot (r'(t)) = 0$
  * $r'(t)$ is the tangent, which is normal to the gradient $f(r(t))$ on the level curve.
 

