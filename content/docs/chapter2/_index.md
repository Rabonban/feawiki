---
# Title, summary, and page position.
linktitle: Chapter 2 - Isoparametric elements
summary: Learn how to use Academic's docs layout for publishing online courses, software documentation, and tutorials.
weight: 1
icon: book
icon_pack: fas

# Page metadata.
title: Chapter 2 - Isoparametric elements
date: "2018-09-09T00:00:00Z"
type: book  # Do not modify.
---

Isoparametric elements are introduced in this chapter because these elements are very important to application of complex shapes of domains. A numerical integration technique called Gauss-Lagrange is also discussed along with isoparametric elements.

Isoparametric elements use mathematical mapping from one coordinate system into another coordinate system, with the first being called the //physical//- and the second one //natural// coordinate system. The problem topology is provided in the physical coordinate system (can be called $xyz$-axis). Element shape functions are defined in terms of the //natural// coordinate system, denoted with $\xi \eta \zeta$-axis. Thus, mapping is needed between the two coordinate systems.

First, we discuss a one-dimensional isoparametric element to discuss the basics of isoparametric elements. Multi-dimensional elements will be discussed later. Shape functions for the isoparametric elements are given as terms of //natural// coordinates as seen in the following figure. Nodes are located at $\xi_{1}=-1$ and $\xi_{2}=1$. While the positions are arbitrary, selecting the previous values is useful, because the //natural// coordinate system is normalized between −1 and 1.



[[div]]
[[=image Figure%20II-1.png size="small"]]
//Figure II-1 Element in natural coordinate//
[[/div]]

[[div]]
[[=image Figure%20II-2.png size="small"]]
//Figure II-2 Element in physical coordinate//

[[/div]]

The shape function is written as


$$H_{1}(\xi)=\frac{1}{2}(1-\xi)$$


and


$$H_{2}(\xi)=\frac{1}{2}(1+\xi)$$


The physical linear element may be located at any position in the physical coordinate system. The element has two coordinate values [[$x_{1}$]] and [[$x_{2}$]], with two nodal variables [[$u_{1}$]] and [[$u_{2}$]].

Any point between [[$\xi_{1}=-1$]] and [[$\xi_{2}=1$]] in the //natural// coordinate system can be mapped onto a point between [[$x_{1}$]] and [[$x_{2}$]] in the //physical// coordinate system using the shape functions defined in Eqs. ([[eref label1]]) and ([[eref label2]]).

[[math label3]]
x=H_{1}(\xi) x_{1}+H_{2}(\xi) x_{2}
[[/math]]

The shape functions are also used to interpolate the variable [[$ u $]] within the element as

[[math label4]]
x=H_{1}(\xi) u_{1}+H_{2}(\xi) u_{2}
[[/math]]

If the shape functions are used for geometric mapping as well as nodal variable interpolation, the element is called isoparametric element.

To compute [[$ \frac{d u}{d x} $]], which is necessary in most of the cases to compute element matrices, we use the chain rule as

$$\begin{array}{l}{\frac{d u}{d x}=\frac{d H_{1}(\xi)}{d x} u_{1}+\frac{d H_{2}(\xi)}{d x} u_{2}} \\ {=\frac{d H_{1}(\xi)}{d \xi} \frac{d \xi}{d x} u_{1}+\frac{d H_{2}(\xi)}{d \xi} \frac{d \xi}{d x} u_{2}}\end{array}$$

where we require $ \frac{d \xi}{d x} $ which is the inverse of $ \frac{d x}{d \xi} $. We can compute the latter from Eq.([[eref label3]]).

The //Jacobian// becomes

[[math label6]]
J=\frac{d x}{d \xi}=\frac{d H_{1}(\xi)}{d \xi} x_{1}+\frac{d H_{2}(\xi)}{d \xi} x_{2}=\frac{1}{2}\left(x_{2}-x_{1}\right)
[[/math]]

Substituting Eq. ([[eref label6]]) into Eq. ([[eref label5]]) results in

[[math label7]]
\frac{d u}{d x}=-\frac{1}{x_{2}-x_{1}} u_{1}+\frac{1}{x_{2}-x_{1}} u_{2}
[[/math]]

Derivatives of shape functions with respect to //physical// coordinate system are

[[math label8]]
\frac{d H_{1}(\xi)}{d x}=-\frac{1}{x_{2}-x_{1}}=-\frac{1}{h_{i}}
[[/math]]

[[math label9]]
\frac{d H_{2}(\xi)}{d x}=\frac{1}{x_{2}-x_{1}}=\frac{1}{h_{i}}
[[/math]]

where [[$ h_{i}=\left(x_{2}-x_{1}\right) $]] is the element size in the //physical// coordinate system.

At this point, the isoparamteric element does not seem to have an advantage over the conventional element because the isoparamteric element requires more steps such as applying the chain rule and mapping. The major advantage of isoparametric elements comes when analytical integration to compute element stiffness matrices and system vectors is either complicated or impossible. This is when element shapes are not regular or differential equations are complex. Therefore, we need a numerical integration technique. Because each isoparamteric element is defined in terms of the normalized domain [[$\xi_{1}=-1$]] and [[$ \xi_{2}=1 $]], it is easier to apply any numerical integration technique.

Triangular and quadrilateral finite elements make it possible for the direct assembly of the stiffness matrices and vectors of nodal forces. The calculation of the shape functions and assembly of the stiffness matrices for quadrilateral and higher order elements are achieved with using isoparametric elements.

The construction of trial solution over a finite element must satisfy the requirements of the problem to solve the geometry of the element. Depending on the type of the problem a trial solution must be continuous, and its derivative must exist (such as a bar problem) or the trial solution and its first derivative must be continuous, and its second derivative must exist (beam problem) and so on.

The compatibility principle, thus, can be formulated as:

* Class [[$ C^{0} $]] problem, trial function must be continuous across the boundary of the elements, but not necessary its derivatives.
* Class [[$ C^{1} $]] problem, both the trial function and its first-order derivatives must be continuous across the boundary of the elements, but not necessary its second-order derivatives.
* Class [[$ C^{n} $]] problem, the trial function and its [[$ (n-1)^{\mathrm{th}} $]] order derivatives must be continuous across the boundary, but not necessary its [[$ n^{\text { th }} $]] order derivatives.

When the size of an element shrinks to zero, the trail function must be able to represent:

* Class [[$ C^{0} $]] problem, a constant value of the exact function as well as constant values of its first-order derivatives.
* Class [[$ C^{1} $]] problem, a constant value of the exact function as well as constant values of its first- and second order derivatives.
* Class [[$ C^{n} $]] problem, a constant value of the exact function as well as constant values of its derivatives up until the [[$ n^{\text { th }} $]] order.

These conditions (compatibility and completeness) are sufficient to ensure that the finite element solution converges to the exact solution. However, the solutions obtained with the finite element method are only approximations to the exact solutions, therefore it is worthwhile to understand these principles to assess the accuracy or make a diagnosis of a finite element model.

+ II.1 Quadrilateral elements

Shape functions for a bilinear isoparametric element are:

[[math label10]]
H_{1}(\xi, \eta)=\frac{1}{4}(1-\xi)(1-\eta)
[[/math]]

[[math label11]]
H_{2}(\xi, \eta)=\frac{1}{4}(1+\xi)(1-\eta)
[[/math]]

[[math label12]]
H_{3}(\xi, \eta)=\frac{1}{4}(1+\xi)(1+\eta)
[[/math]]

[[math label13]]
H_{4}(\xi, \eta)=\frac{1}{4}(1-\xi)(1+\eta)
[[/math]]

The shape functions are defined in terms of normalized //natural// domain [[$ -1 \leq \xi \leq 1 $]] and [[$ -1 \leq \eta \leq 1 $]].

The element shape is a square in the //natural// coordinate system, it can be mapped into a general quadrilateral shape with distortions. When this is undertaken, the relative positions of nodal points should be consistent between the two elements in the //natural// and //physical// domains. In other words, successive path in counter clockwise direction should be the same for node numbers should be the same in //natural// and //physical// coordinates. A point [[$ (\xi, \eta) $]] within the natural element is mapped into a point [[$ (x, y $]]) within the physical element using the shape functions:

[[math label14]]
x=\sum_{i=1}^{4} H_{i}(\xi, \eta) x_{i}
[[/math]]

[[math label15]]
y=\sum_{i=1}^{4} H_{i}(\xi, \eta) y_{i}
[[/math]]

where [[$ x_{i} $]] and [[$ y_{i} $]] are the coordinate values of the [[$ i^{t h} $]] node.

Any physical variable can be interpolated using the same shape functions:

[[math label16]]
u=\sum_{i=1}^{4} H_{i}(\xi, \eta) u_{i}
[[/math]]

where [[$ u_{i} $]] is the nodal variable of [[$ i^{\mathrm{th}} $]] node.

[[=image Figure%20II-3.png size="small"]]
//Figure II-3 Bilinear element in natural coordinate (Source: Kwon Y. W., Hyochoong Bang)//

[[=image Figure%20II-4.png size="small"]]
//Figure II-4 Bilinear element in physical coordinate//

If we want to assemble system matrices, then we need to compute [[$ \frac{\partial H_{i}(\xi, \eta)}{\partial x} $]] and [[$ \frac{\partial H_{i}(\xi, \eta)}{\partial y} $]]. In order to do it, we use the chain again.

[[math label17]]
\frac{\partial}{\partial \xi}=\frac{\partial}{\partial x} \frac{\partial x}{\partial \xi}+\frac{\partial}{\partial y} \frac{\partial y}{\partial \xi}
[[/math]]

[[math label18]]
\frac{\partial}{\partial \eta}=\frac{\partial}{\partial x} \frac{\partial x}{\partial \eta}+\frac{\partial}{\partial y} \frac{\partial y}{\partial \eta}
[[/math]]

Rewriting these in matrix form:


$${\begin{array}{c}{\frac{\partial}{\partial \xi}} \\ {\frac{\partial}{\partial \eta}}\end{array}\right\}=\left[\begin{array}{ll}{\frac{\partial x}{\partial \xi}} & {\frac{\partial y}{\partial \xi}} \\ {\frac{\partial x}{\partial \eta}} & {\frac{\partial y}{\partial \eta}}\end{array}\right]\left\{\begin{array}{c}{\frac{\partial}{\partial x}} \\ {\frac{\partial}{\partial y}}\end{array}\right\}$$


The derivative shown of the left side column vector is called local derivative, while in the right side it is called global derivative. The square matrix is called the //Jacobian// and is denoted as for a 2-D case:

[[math label20]]
[J]=\left[\begin{array}{ll}{J_{11}} & {J_{12}} \\ {J_{21}} & {J_{22}}\end{array}\right]=\left[\begin{array}{cc}{\frac{\partial x}{\partial \xi}} & {\frac{\partial y}{\partial \xi}} \\ {\frac{\partial x}{\partial \eta}} & {\frac{\partial y}{\partial \eta}}\end{array}\right]
[[/math]]

The //Jacobian// can be easily extended for three-dimensional domain too.

The inverse of the //Jacobian// is denoted as:

[[math label21]]
[R]=[J]^{-1}=\left[\begin{array}{ll}{R_{11}} & {R_{12}} \\ {R_{21}} & {R_{22}}\end{array}\right]
[[/math]]

We can rewrite Eq. ([[eref label19]]) as

[[math label22]]
\left\{\begin{array}{l}{\frac{\partial}{\partial x}} \\ {\frac{\partial}{\partial y}}\end{array}\right\}=\left[\begin{array}{ll}{R_{11}} & {R_{12}} \\ {R_{21}} & {R_{22}}\end{array}\right]\left\{\begin{array}{c}{\frac{\partial}{\partial \xi}} \\ {\frac{\partial}{\partial \eta}}\end{array}\right\}
[[/math]]

Derivatives of the shape functions with respect to x and y can be obtained from the above equation:

[[math label23]]
\left\{\begin{array}{l}{\frac{\partial H_{i}}{\partial x}} \\ {\frac{\partial H_{i}}{\partial y}}\end{array}\right\}=\left[\begin{array}{cc}{R_{11}} & {R_{12}} \\ {R_{21}} & {R_{22}}\end{array}\right]\left\{\begin{array}{c}{\frac{\partial H_{i}}{\partial \xi}} \\ {\frac{\partial H_{i}}{\partial \eta}}\end{array}\right\}
[[/math]]

To be able to invert the //Jacobian//, its determinant cannot be 0 or negative. This can be achieved by using counter-clockwise order of nodes.

Other popular quadrilateral elements are eight-node isoparametric elements. Their shape functions are:

[[math label24]]
\left\{\begin{array}{l}{\frac{\partial}{\partial x}} \\ {\frac{\partial}{\partial y}}\end{array}\right\}=\left[\begin{array}{ll}{R_{11}} & {R_{12}} \\ {R_{21}} & {R_{22}}\end{array}\right]\left\{\begin{array}{c}{\frac{\partial}{\partial \xi}} \\ {\frac{\partial}{\partial \eta}}\end{array}\right\}
[[/math]]

Derivatives of the shape functions with respect to x and y can be obtained from the above equation:

[[math label25]]
\left\{\begin{array}{l}{\frac{\partial H_{i}}{\partial x}} \\ {\frac{\partial H_{i}}{\partial y}}\end{array}\right\}=\left[\begin{array}{cc}{R_{11}} & {R_{12}} \\ {R_{21}} & {R_{22}}\end{array}\right]\left\{\begin{array}{c}{\frac{\partial H_{i}}{\partial \xi}} \\ {\frac{\partial H_{i}}{\partial \eta}}\end{array}\right\}
[[/math]]

To be able to invert the //Jacobian//, its determinant cannot be 0 or negative. This can be achieved by using counter-clockwise order of nodes.

Other popular quadrilateral elements are eight-node isoparametric elements. Their shape functions are:

[[math label26]]
H_{1}=\frac{1}{4}(1-\xi)(1-\eta)(-1-\xi-\eta)
[[/math]]

[[math label27]]
H_{2}=\frac{1}{4}(1+\xi)(1-\eta)(-1+\xi-\eta)
[[/math]]

[[math label28]]
H_{3}=\frac{1}{4}(1+\xi)(1+\eta)(-1+\xi+\eta)
[[/math]]

[[math label29]]
H_{4}=\frac{1}{4}(1-\xi)(1+\eta)(-1-\xi+\eta)
[[/math]]

[[math label30]]
H_{5}=\frac{1}{2}\left(1-\xi^{2}\right)(1-\eta)
[[/math]]

[[math label31]]
H_{6}=\frac{1}{2}(1+\xi)\left(1-\eta^{2}\right)
[[/math]]

[[math label32]]
H_{7}=\frac{1}{2}\left(1-\xi^{2}\right)(1+\eta)
[[/math]]

[[math label33]]
H_{8}=\frac{1}{2}(1-\xi)\left(1-\eta^{2}\right)
[[/math]]

[[=image Figure%20II-5.png size="small"]]
//Figure II-5 Eight-node quadrilateral element in natural coordinate (Source: Young W. K., Hyochoong B.)//

+ II.2 Triangular elements

[[=image Figure%20II-6.png size="small"]]
//Figure II-6 Triangular element in natural coordinate//

As quadrilateral elements isoparametric elements, triangular isoparametric elements can be defined also. In terms of natural coordinate system, we have the shape functions as

[[math label34]]
H_{1}=1-\xi-\eta
[[/math]]

[[math label35]]
H_{2}=\xi
[[/math]]

[[math label36]]
H_{3}=\eta
[[/math]]

In case of the quadratic higher order triangle we have the shape functions written as

[[math label37]]
H_{1}=(1-\xi-\eta)(1-2 \xi-2 \eta)
[[/math]]

[[math label38]]
H_{2}=\xi(2 \xi-1)
[[/math]]

[[math label39]]
H_{3}=\eta(2 \eta-1)
[[/math]]

[[math label40]]
H_{4}=4 \xi(1-\xi-\eta)
[[/math]]

[[math label41]]
H_{5}=4 \xi \eta
[[/math]]

[[math label42]]
H_{2}=4 \eta(1-\xi-\eta)
[[/math]]

[[=image Figure%20II-7.png size="small"]]
//Figure II-7 Quadratic six-node triangular element in natural coordinate (Source:Young K. W., Hyochoong B.)//

+ II.3 Gauss integration

When we use analytical integration to express the theorem of virtual work during the evaluation of the stiffness matrix of an element of for ex. a beam, we have an easy task, because the beam element is unidimensional. However, when the number of elements is large, and their geometrical shape is general, as is the case of most of the finite element application, the use of analytical integration becomes difficult or outright impossible, and furthermore not well suited for coding. In this case we can use numerical integration.

Gauss-Legendre is such a numerical integration method, the most widely used and the most precise.

An integral is defined as:

[[math label43]]
\int_{a}^{b} f(x) d x=\lim _{n \rightarrow \infty} \sum_{i=1}^{n} f\left(x_{i}\right) d x_{i}
[[/math]]

The basic idea is to replace the continuous integral with a series of finite sums.

[[=image Figure%20II-8.png size="small"]]
//Figure II-8 Gauss-Lagrange integration (Source: Young K. W, Hyochoong B.)//

We can approximate ([[eref label43]]) as

[[math label44]]
\int_{a}^{a} f(x) d x \approx \sum_{i=1}^{N} f\left(x_{i}\right) \Delta x_{i}
[[/math]]

where [[$ N $]] is a finite number.

Rewritten in general way,

[[math label45]]
\int_{a}^{a} f(x) d x \approx \sum_{i=1}^{M} f\left(x_{i}\right) W_{i}
[[/math]]

where [[$ M $]] is the number of integration points, [[$ x_{i} $]] is the integration point (sampling point) and [[$ W_{i} $]] is the weighting coefficient. The weighting coefficient is the width of the rectangular strip whose height is [[$ f\left(x_{i}\right) $]]. Any numerical integration may be expressed in this form. To derive the standard values for sampling points and weights, the integration domain is normalized such that [[$ -1 \leq x \leq 1 $]]. Gauss-Legendre quadrature is useful for integrating polynomial functions. It can integrate polynomial function of order 2n-1 using n-point quadrature exactly. Sampling points and weighting coefficients are given in the following tables.

If the integrand is not a polynomial expression, Gauss quadrature an approximate result. In this case, an optimal number of integration points should be selected in consideration of accuracy and computational cost.

The quadrature rule can be extended for multi-dimensional integration. For a 2-D example of a normalized domain:

[[math label46]]
\begin{aligned} & \int_{-1}^{1} \int_{-1}^{1} f(\xi, \eta) d \xi d \eta=\int_{-1}^{1} \sum_{i=1}^{M_{1}} W_{i} f\left(\xi_{i}, \eta\right) d \eta \\=& \sum_{j=1}^{M_{2}} W_{j} \sum_{I=1}^{M_{1}} W_{i} f\left(\xi_{i}, \eta_{i}\right)=\sum_{i=1}^{M_{1}} \sum_{j=1}^{M_{2}} W_{i} W_{j} f\left(\xi_{i}, \eta_{i}\right) \end{aligned}
[[/math]]

[[=image Figure%20II-9.png size="small"]]
//Figure II-9 Sampling point and weights in Gauss quadrature (Source: Young K. W., Hyochoong B.)//

As we have seen Gauss quadrature evaluates single integrals between −1 and +1, double integrals over a quadrilateral, and triple integral over a cube. For example, to evaluate an integral over a quadrilateral, it is necessary to transform the quadrilateral into a reference element over which the integration can be carried out.

Evaluating the integral [[$ \int_{A} f(x, y) d A $]] over a quadrilateral area looks like:

Using isoparametric elements, writing [[$ x $]] and [[$ y $]] in terms of [[$ \xi $]] and [[$ \eta $]] as

[[math label47]]
x(\xi, \eta)=N_{1}(\xi, \eta) x_{1}+N_{2}(\xi, \eta) x_{2}+N_{3}(\xi, \eta) x_{3}+N_{4}(\xi, \eta) x_{4}
[[/math]]

[[math label48]]
y(\xi, \eta)=N_{1}(\xi, \eta) y_{1}+N_{2}(\xi, \eta) y_{2}+N_{3}(\xi, \eta) y_{3}+N_{4}(\xi, \eta) y_{4}
[[/math]]

shape functions are denoted in the place of [[$ H_{i} $]] with [[$ N_{i}(\xi, \eta) $]] and are given in Chapter II.1.

Using the equation of the Jacobian of the transformation to express elementary area [[$ d A = dxdy $]] in terms of the corresponding elementary area [[$ d \xi d \eta $]] of the reference element

[[math label49]]
d x d y=\operatorname{det}[J] d \xi d \eta
[[/math]]

Constructing nodal approximation for the function using its nodal values

[[math label50]]
f(\xi, \eta)=\sum_{i=1}^{n} N_{i}(\xi, \eta) f_{i}
[[/math]]

Finally, we get the integral

[[math label51]]
I=\int_{-1}^{+1} \int_{-1}^{+1}\left(\sum_{i=1}^{n} N_{i}(\xi, \eta) f_{i}\right) \operatorname{det}[J] d \xi d \eta
[[/math]]
