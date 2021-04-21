---
# Title, summary, and page position.
linktitle: Chapter 3 - Plates and shells
summary: Learn about finite element formulation of plates and shells.
weight: 1
icon: book
icon_pack: fas

# Page metadata.
title: Chapter 3 - Plates and shells
date: "2018-09-09T00:00:00Z"
type: book  # Do not modify.
---

## III.1 Overview
---

Plates and shells are common structures in the field of applied mechanics, their main property being that they support transverse loading through bending action (and is some cases as we will see, through membrane and shear effects). Finite element formulation for plate and shells has a higher degree of complexity than other types of elements. The complexity arises from the nature of high order differential equations. To overcome the complex formulations, different solutions have been proposed.
First, the classical plate bending theory is presented along with its finite element formulation. Then other types of plate theories follow, such as shear deformable plate elements, with displacement degrees of freedom only, mixed elements and hybrid elements.
Then the type of shell derived, is the one which is the combination of plate bending and plane stress elements, with a proper coordinate transformation from local to global coordinate axis, while using the drilling degree of freedom to bypass singularity problem in the transformation matrix.
The second shell element is developed by degenerating from 3-D solid elements, but for the sake of simplicity we focus on the first type of shell only.

## III.2 Classical plate theory (Kirchoff-Love)
---

The basic assumptions for the classical Kirchhoff plate bending theory are very similar to those for the Euler-Bernoulli beam theory. One of the most important assumptions for both theories is that a straight line normal to the midplane in the un-deformed case remains normal after deformation. This leads to the fact that transverse deformation is not going to be taken into account, or as we might say: neglected.

In-plane displacements $ u $ and $ v $ can be expressed as

<a name="label1"></a>
$$u=-z \frac{\partial w}{\partial x}$$
<div style="text-align: right"> (1) </div>

<a name="label2"></a>
$$v=-z \frac{\partial w}{\partial y}$$
<div style="text-align: right"> (2) </div>

Where $ x $ and $ y $ are the in-plane axes located at the midplane of the plate, and $ z $ is perpendicular to the plane defined by these (in direction of the thickness). As follows $ u $ and $ v $ are displacements along, respectively, the $ x $- and $ y $- axes, while $ w $ is the transverse displacement (deflection) along the $ z $-axis.

Because we neglect the transverse shear deformation, in-plane strains can be written in terms of displacements

<a name="label3"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>ε</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>ε</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
            <msub>
              <mi>γ</mi>
              <mrow>
                <mi>x</mi>
                <mi>y</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo>=</mo>
    <mo>−</mo>
    <mi>z</mi>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
        <mtr>
          <mtd>
            <msub>
              <mi>κ</mi>
              <mrow>
                <mi>x</mi>
              </mrow>
            </msub>
          </mtd>
          <mtd>
            <msub>
              <mi>κ</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
          </mtd>
          <mtd>
            <msub>
              <mi>κ</mi>
              <mrow>
                <mi>x</mi>
                <mi>y</mi>
              </mrow>
            </msub>
          </mtd>
        </mtr>
      </mtable>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (3) </div>

where

<a name="label4"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>κ</mi>
  <msup>
    <mo fence="false" stretchy="false">}</mo>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>κ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>κ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>κ</mi>
            <mrow>
              <mi>x</mi>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mi>z</mi>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mfrac>
            <mrow>
              <msup>
                <mi mathvariant="normal">∂</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msup>
              <mi>w</mi>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msup>
                <mi>x</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msup>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <msup>
                <mi mathvariant="normal">∂</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msup>
              <mi>w</mi>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msup>
                <mi>y</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msup>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>2</mn>
          <mfrac>
            <mrow>
              <msup>
                <mi mathvariant="normal">∂</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msup>
              <mi>w</mi>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (4) </div>

is called curvature.

{{< figure src="Figure%20III-1.png" caption="Thin plate element in bending (Source: Amar Khennane)" numbered="true" width="500">}}

Assuming plane stress condition for plate bending and substituting ([3](#label3)) and ([4](#label4)) into the constitutive equation. This states the relationship between the stresses and strains. For an isotropic material, the constitutive equation becomes

<a name="label5"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>σ</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mo stretchy="false">[</mo>
  <mi>D</mi>
  <mo stretchy="false">]</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>ε</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (5) </div>

By substituting ([3](#label3)) and ([4](#label4))

<a name="label6"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>σ</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mo>−</mo>
  <mi>z</mi>
  <mo stretchy="false">[</mo>
  <mi>D</mi>
  <mo stretchy="false">]</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>κ</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (6) </div>

in which

<a name="label7"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>σ</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>σ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>σ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msup>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
              <msub>
                <mi>τ</mi>
                <mrow>
                  <mi>x</mi>
                  <mi>y</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">}</mo>
            </mrow>
            <mrow>
              <mi>T</mi>
            </mrow>
          </msup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (7) </div>

and the material property matrix $ [D] $ becomes

<a name="label8"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">[</mo>
  <mi>D</mi>
  <mo stretchy="false">]</mo>
  <mo>=</mo>
  <mfrac>
    <mi>E</mi>
    <mrow>
      <mn>1</mn>
      <mo>−</mo>
      <msup>
        <mi>v</mi>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msup>
    </mrow>
  </mfrac>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mi>v</mi>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>v</mi>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>10</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mn>1</mn>
              <mo>−</mo>
              <mi>v</mi>
            </mrow>
            <mn>2</mn>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (8) </div>

Moments are defined as

<a name="label9"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>M</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <msubsup>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>h</mi>
      <mrow>
        <mo>/</mo>
      </mrow>
      <mn>2</mn>
    </mrow>
    <mrow>
      <mi>h</mi>
      <mrow>
        <mo>/</mo>
      </mrow>
      <mn>2</mn>
    </mrow>
  </msubsup>
  <mo fence="false" stretchy="false">{</mo>
  <mi>σ</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mi>z</mi>
  <mi>d</mi>
  <mi>z</mi>
</math>
<div style="text-align: right"> (9) </div>

where 

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>M</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
        <mtr>
          <mtd>
            <msub>
              <mi>M</mi>
              <mrow>
                <mi>x</mi>
              </mrow>
            </msub>
          </mtd>
          <mtd>
            <msub>
              <mi>M</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
          </mtd>
          <mtd>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
              <msub>
                <mi>M</mi>
                <mrow>
                  <mi>x</mi>
                  <mi>y</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">}</mo>
            </mrow>
          </mtd>
        </mtr>
      </mtable>
      <mrow>
        <mi>T</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>

and $ h $ is the plate thickness. Substituting Eq. ([6](#label6)) into Eq. ([9](#label9)) gives the relationship between moment and curvature.

<a name="label10"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>M</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mo>−</mo>
  <mo stretchy="false">[</mo>
  <mrow>
    <mover>
      <mi>D</mi>
      <mo>~</mo>
    </mover>
  </mrow>
  <mo stretchy="false">]</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>κ</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (10) </div>

where

<a name="label11"></a>
$$[\widetilde{D}]=\frac{h^{3}}{12}[D]$$
<div style="text-align: right"> (11) </div>

Equilibrium equations are obtained from the free-body diagram. Moment equilibriums about the $ y $- and $ x $-axes and force equilibrium about the $ z $-axis yield, after neglecting the higher order terms,

<a name="label12"></a>
$$\frac{\partial M_{x}}{\partial x}+\frac{\partial M_{x y}}{\partial y}-Q_{x}=0$$
<div style="text-align: right"> (12) </div>

<a name="label13"></a>
$$\frac{\partial M_{x y}}{\partial x}+\frac{\partial M_{y}}{\partial y}-Q_{y}=0$$
<div style="text-align: right"> (13) </div>

<a name="label14"></a>
$$\frac{\partial Q_{x}}{\partial x}+\frac{\partial Q_{y}}{\partial y}+p=0$$
<div style="text-align: right"> (14) </div>

where $ Q_{x} $ and $ Q_{y} $ are the shear forces and $ p $ is the distributed pressure loading. Elimination of the shear forces from Eqs. ([12](#label12)) to ([14](#label14)) gives

<a name="label15"></a>
$$\frac{\partial^{2} M_{x}}{\partial x^{2}}+2 \frac{\partial^{2} M_{x y}}{\partial x \partial y}+\frac{\partial^{2} M_{y}}{\partial y^{2}}+p=0$$
<div style="text-align: right"> (15) </div>

{{< figure src="Figure%20III-2.png" caption="Free body diagram of a plate element (Source: Young W. Kwon, Hyochoong Bang)" numbered="true" width="300">}}

Combining Eqs. ([4](#label4)), ([10](#label10)) and ([15](#label15)) finally produces the biharmonic governing equation for plate bending in terms of transverse displacement $ w $.

<a name="label16"></a>
$$\frac{\partial^{4} w}{\partial x^{4}}+2 \frac{\partial^{4} w}{\partial x^{2} \partial y^{2}}+\frac{\partial^{4} w}{\partial y^{4}}=\frac{p}{D_{r}}$$
<div style="text-align: right"> (16) </div>

where $ D_{e}=\frac{E h^{3}}{12\left(1-v^{2}\right)} $ is the plate rigidity.

This is often written as

<a name="label17"></a>
$$\nabla^{4} w=\frac{q}{D_{r}}$$
<div style="text-align: right"> (17) </div>
  
  
Summing up, the deflection theory of plates attributed to Kirchhoff is based on the following assumptions:

* The x–y plane coincides with the middle plane of the plate in the un-deformed geometry.
* The lateral dimension of the plate is at least 10 times its thickness.
* The vertical displacement of any point of the plate can be taken equal to that of the point (below or above it) in the middle plane.
* A vertical element of the plate before bending remains perpendicular to the middle surface of the plate after bending.
* Strains are small: deflections are less than the order of (1/100) of the span length.
* The strain of the middle surface is zero or negligible.

## III.3 Classical plate bending elements

## III.3.1 Three-node element
---

Deriving a three-node element based on the classical plate bending theory. Shown in the following figure. Each node has three degrees of freedom: displacement in $ z $ direction – $ w $; a rotation around the $ x $-axis, $ w_{y} $, (derivative of $ w $ with respect to $ y $); and a rotation about the $ y $-axis, $ w_{x} $ (derivative of $ w $ with respect to $ x $).

The displacement function $ w $ is assumed to be

<a name="label18"></a>
$$\begin{array}{c}{w(x, y)=a_{1}+a_{2} x+a_{3} x+a_{4} x^{2}+a_{5} x y+a_{6} y^{2}+a_{7} x^{3}+a_{8}\left(x^{2} y+x y^{2}\right)+a_{9} y^{3}=} \\\\ {=[X]\{a\}}\end{array}$$
<div style="text-align: right"> (18) </div>

where

<a name="label19"></a>
$$[X]=\left[\begin{array}{llllllll}{1} & {x} & {y} & {x^{2}} & {x y} & {y^{2}} & {x^{3}} & {\left(x^{2} y+x y^{2}\right)} & {y^{3}}\end{array}\right]$$
<div style="text-align: right"> (19) </div>

and 

<a name="label20"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>a</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left left left left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>1</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>2</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>3</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>4</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>5</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>6</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>a</mi>
              <mrow>
                <mn>7</mn>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msup>
              <mrow data-mjx-texclass="INNER">
                <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
                <msub>
                  <mi>a</mi>
                  <mrow>
                    <mn>8</mn>
                  </mrow>
                </msub>
                <mo data-mjx-texclass="CLOSE">}</mo>
              </mrow>
              <mrow>
                <mi>T</mi>
              </mrow>
            </msup>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (20) </div>

With constants $ a_{i} $ are to be replaced by nodal variables $ w $, $ w_{x} $ and $ w_{y} $. Taking derivatives of the displacement function with respect to $ x $ and $ y $ yields

<a name="label21"></a>
$$\frac{\partial w}{\partial x}=a_{2}+2 a_{4} x+a_{5} y+3 a_{7} x^{2}+a_{8}\left(2 x y+y^{2}\right)$$
<div style="text-align: right"> (21) </div>

<a name="label22"></a>
$$\frac{\partial w}{\partial y}=a_{3}+a_{5} x+2 a_{6} y+2 a_{8}\left(x^{2}+2 x y\right)+3 a_{9} y^{2}$$
<div style="text-align: right"> (22) </div>

{{< figure src="Figure%20III-3.png" caption="Three-node plate bending element (Source: Young W. Kwon, Hyochoong Bang)" numbered="true" width="500">}}

Evaluation of equations from ([18](#label18)) through ([22](#label22)) at the three nodal points gives the following equation:

<a name="label23"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>d</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mo stretchy="false">[</mo>
  <mrow>
    <mover>
      <mi>X</mi>
      <mo stretchy="false">~</mo>
    </mover>
  </mrow>
  <mo stretchy="false">]</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>a</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (23) </div>

where

<a name="label24"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>d</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>w</mi>
        <mrow>
          <mn>1</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
        <mrow>
          <mn>1</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
        <mrow>
          <mn>1</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mi>w</mi>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mi>w</mi>
        <mrow>
          <mn>3</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
        <mrow>
          <mn>3</mn>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">(</mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">)</mo>
        </mrow>
        <mrow>
          <mn>3</mn>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
</math>
<div style="text-align: right"> (24) </div>

and

<a name="label25"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">[</mo>
  <mrow>
    <mover>
      <mi>X</mi>
      <mo stretchy="false">~</mo>
    </mover>
  </mrow>
  <mo stretchy="false">]</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mo>+</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>3</mn>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mo>+</mo>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
          <mo>+</mo>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>3</mn>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <mo>+</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>3</mn>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <mo>+</mo>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
          <mo>+</mo>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>3</mn>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
          <mo>+</mo>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>3</mn>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
          <mo>+</mo>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>2</mn>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msubsup>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
          <mo>+</mo>
          <mn>2</mn>
          <msub>
            <mi>x</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
          <msub>
            <mi>y</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>3</mn>
          <msubsup>
            <mi>y</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (25) </div>

Inverting equations ([23](#label23)) and substituting the results into Eq. ([18](#label18)) yields the following

<a name="label26"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>w</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mo stretchy="false">[</mo>
  <mi>H</mi>
  <mo stretchy="false">]</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>d</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (26) </div>

Where the row vector of shape functions of size $ 9 * 1 $ is computed from

<a name="label27"></a>
$$[H]=[X][X]^{-1}$$
<div style="text-align: right"> (27) </div>

In-plane strains are computed from Eq. ([26](#label26)) as

<a name="label28"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>ε</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mo stretchy="false">[</mo>
  <mi>B</mi>
  <mo stretchy="false">]</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>d</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (28) </div>

where

<a name="label29"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo fence="false" stretchy="false">{</mo>
  <mi>ε</mi>
  <mo fence="false" stretchy="false">}</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow>
            <msub>
              <mi>ε</mi>
              <mrow>
                <mi>x</mi>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msub>
              <mi>ε</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <msup>
              <mrow data-mjx-texclass="INNER">
                <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
                <msub>
                  <mi>γ</mi>
                  <mrow>
                    <mi>x</mi>
                    <mi>y</mi>
                  </mrow>
                </msub>
                <mo data-mjx-texclass="CLOSE">}</mo>
              </mrow>
              <mrow>
                <mi>T</mi>
              </mrow>
            </msup>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (29) </div>

<a name="label30"></a>
$$[B]=-z[L][\tilde{X}]^{-1}$$
<div style="text-align: right"> (30) </div>

<a name="label31"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">[</mo>
  <mi>L</mi>
  <mo stretchy="false">]</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>2</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>10</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>6</mn>
            <mi>x</mi>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>2</mn>
            <mi>y</mi>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>2</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>2</mn>
            <mi>x</mi>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>6</mn>
            <mi>y</mi>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>2</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>4</mn>
            <mo stretchy="false">(</mo>
            <mi>x</mi>
            <mo>+</mo>
            <mi>y</mi>
            <mo stretchy="false">)</mo>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mn>0</mn>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (31) </div>

Substitution of the strain-nodal displacement relation, Eq. ([28](#label28)) into the expression for the element stiffness matrix,

<a name="label32"></a>
$$\left[K_{e}\right]=\int_{\Omega^{e}}[B]^{T}[D][B] d \Omega=[B]^{T}[D][B] A$$
<div style="text-align: right"> (32) </div>

yields

<a name="label33"></a>
$$\begin{array}{l}{\quad\left[K^{e}\right]=\int_{\Omega^{e}} \int_{z}[B]^{T}[D][B] d z d \Omega} \\\\ {=[\tilde{X}]^{-T} \int_{\Omega^{e}} \int_{z} Z^{2}[L]^{T}[D][L] d z d \Omega[\tilde{X}]^{-1}} \\\\ {\quad=[\tilde{X}]^{-T} \int_{\Omega^{e}}[L]^{T}[\widetilde{D}][L] d \Omega[\tilde{X}]^{-1}}\end{array}$$
<div style="text-align: right"> (33) </div>

where

<a name="label34"></a>
$$[\widetilde{D}]=\frac{h^{3}}{12}[D]$$
<div style="text-align: right"> (34) </div>

Here $ [D] $ is the constitutive matrix of the plane stress condition, $ \Omega^{e} $ is the two-dimensional element domain in the $ x y $-plane, and $ h $ is the thickness of the plate. The element domain is the triangular shape as seen in the previous figure. The element stiffness matrix is of size $ 9 × 9 $ and the corresponding element nodal vector is given in  Eq. ([24](#label24)).

## III.3.2 Four-node element
---

Consider the rectangular plate element shown in the following figure. The element has four nodes and 12 dof in total. A trial function for the unknown $ w(x,y) $ will contain 12 parameters:

<a name="label35"></a>
$$w(x, y)=\alpha_{1}+\alpha_{2} x+\alpha_{3} y+\alpha_{4} x^{2}+\alpha_{5} x y+\alpha_{6} y^{2}+\alpha_{7} x^{3}+\alpha_{8} x^{2} y+\alpha_{9} x y^{2}+ \\ \alpha_{10} y^{3}+\alpha_{11} y x^{3}+\alpha_{12} x y^{3}$$
<div style="text-align: right"> (35) </div>

<a name="label36"></a>
$$\frac{\partial w}{\partial x}=\alpha_{2}+2 \alpha_{4} x+\alpha_{5} y+3 \alpha_{7} x^{2}+2 \alpha_{8} x y+\alpha_{9} y^{2}+3 \alpha_{11} x^{2} y+\alpha_{12} y^{3}$$
<div style="text-align: right"> (36) </div>

<a name="label37"></a>
$$\frac{\partial w}{\partial y}=\alpha_{3}+\alpha_{5} x+2 \alpha_{6} y+\alpha_{8} x^{2}+2 \alpha_{9} y x+3 \alpha_{10} y^{2}+\alpha_{11} x^{3}+3 \alpha_{12} y^{2} x$$
<div style="text-align: right"> (37) </div>

{{< figure src="Figure%20III-4.png" caption="Four-node element (Source: Amar Khennane)" numbered="true" width="500">}}

It can be seen that both $ w (x,y) $ and its derivatives are defined by cubic polynomials. As a cubic is uniquely defined by four constants, the two end values of the displacements and slopes will therefore define the displacements uniquely along any boundary. However, this is not the case for the derivatives, since only two end values of the slopes exist, the cubic is not specified uniquely. And in general, a discontinuity of normal slope will occur. The function is therefore called “non-conforming.”


## III.4 Shear deformable plate element (Reissner-Mindlin plate)
---

The Reissner-Mindlin plate theory includes the effect of transverse shear deformation like the Timoshenko beam theory. Hence, a plane normal to the midplane of the plate before deformation does not remain normal to the midplane any longer after deformation. The internal energy expression for the shear deformable plate should include transverse shear energy as well as bending energy. The internal energy is expressed as

<a name="label38"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>U</mi>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>V</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>σ</mi>
        <mrow>
          <mi>b</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mi>d</mi>
  <mi>V</mi>
  <mo>+</mo>
  <mfrac>
    <mi>κ</mi>
    <mn>2</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>V</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>σ</mi>
        <mrow>
          <mi>s</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ε</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mi>d</mi>
  <mi>V</mi>
</math>
<div style="text-align: right"> (38) </div>

where

<a name="label39"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>σ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>σ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>σ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msup>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
              <msub>
                <mi>τ</mi>
                <mrow>
                  <mi>x</mi>
                  <mi>y</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">}</mo>
            </mrow>
            <mrow>
              <mi>T</mi>
            </mrow>
          </msup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (39) </div>

<a name="label40"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>ϵ</mi>
        <mrow>
          <mi>x</mi>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mi>ϵ</mi>
        <mrow>
          <mi>y</mi>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mi>γ</mi>
        <mrow>
          <mi>x</mi>
          <mi>y</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
</math>
<div style="text-align: right"> (40) </div>

are the bending stress and strain components while

<a name="label41"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>σ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>τ</mi>
        <mrow>
          <mi>x</mi>
          <mi>z</mi>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mi>τ</mi>
        <mrow>
          <mi>y</mi>
          <mi>z</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
</math>
<div style="text-align: right"> (41) </div>

<a name="label42"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>γ</mi>
        <mrow>
          <mi>x</mi>
          <mi>z</mi>
        </mrow>
      </msub>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <msub>
        <mi>γ</mi>
        <mrow>
          <mi>y</mi>
          <mi>z</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
</math>
<div style="text-align: right"> (42) </div>

are the transverse shear components. In addition, $ \kappa $ is the shear energy correction factor and equal to $ \frac{5}{6} $ .

Substitution of the constitutive equations for both bending and shear components yields

<a name="label43"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>U</mi>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>V</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>ϵ</mi>
        <mrow>
          <mi>b</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mi>d</mi>
  <mi>V</mi>
  <mo>+</mo>
  <mfrac>
    <mi>κ</mi>
    <mn>2</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>V</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>ϵ</mi>
        <mrow>
          <mi>s</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mi>d</mi>
  <mi>V</mi>
</math>
<div style="text-align: right"> (43) </div>

in which

<a name="label44"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mfrac>
    <mi>E</mi>
    <mrow>
      <mn>1</mn>
      <mo>−</mo>
      <msup>
        <mi>v</mi>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msup>
    </mrow>
  </mfrac>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mi>v</mi>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>v</mi>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mn>1</mn>
              <mo>−</mo>
              <mi>v</mi>
            </mrow>
            <mn>2</mn>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (44) </div>

is the constitutive equation for the plane stress condition and

<a name="label45"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mi>G</mi>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mi>G</mi>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (45) </div>

Further, $ V $ is the three-dimensional domain which is equal to $ 𝑑Ω×𝑑𝑧 $. The $ xyz $ coordinate axis is the same as in the figure.

{{< figure src="Figure%20III-5.png" caption="Shear deformable plate element (Source: Amar Khennane)" numbered="true" width="500">}}

In order to get the derivate element stiffness matrix for the shear deformable plate, we need to express the strains in terms of nodal variables. The in-plane displacements are given as

<a name="label46"></a>
$$u=-z \theta_{x}(x, y)$$
<div style="text-align: right"> (46) </div>

<a name="label47"></a>
$$v=-z \theta_{y}(x, y)$$
<div style="text-align: right"> (47) </div>

and the transverse displacement is

<a name="label48"></a>
$$w=w(x, y)$$
<div style="text-align: right"> (48) </div>

where $ \theta_{x} $ and $ \theta_{y} $ are rotations of the midplane about the $ y $ and $ x $ axes, respectively. The midplane is assumed to have no in-plane deformation. In the case of the shear deformable plate,

<a name="label49"></a>
$$\theta_{x}=\frac{\partial w}{\partial x}-\gamma_{x z}$$
<div style="text-align: right"> (49) </div>

<a name="label50"></a>
$$\theta_{y}=\frac{\partial w}{\partial y}-\gamma_{y z}$$
<div style="text-align: right"> (50) </div>

where $ \gamma $ is the angle caused by the shear deformation.

Because the transverse displacement $ w $ and slope $ \theta $ are independent, we need shape functions to interpolate them independently. As a result, the shear deformable element requires $ C^{0} $ compatibility. Isoparametric shape functions are used for the plate element formulation as we will see in the following. The transverse displacement and slopes are interpolated as 

<a name="label51"></a>
$$w=\sum_{i=1}^{n} H_{i}(\xi, \eta) w_{i}$$
<div style="text-align: right"> (51) </div>

<a name="label52"></a>
$$\theta_{x}=\sum_{i=1}^{n} H_{i}(\xi, \eta)\left(\theta_{x}\right)_{i}$$
<div style="text-align: right"> (52) </div>

<a name="label53"></a>
$$\theta_{y}=\sum_{i=1}^{n} H_{i}(\xi, \eta)\left(\theta_{y}\right)_{i}$$
<div style="text-align: right"> (53) </div>

Here $ n $ is the number of nodes per element and the same shape functions are used for the displacement and slope interpolations. As for the sake of simplicity, bilinear isoparametric shape functions are used. However, higher-order shape functions can and are used in the same manner. Bending and shear strains are computed from displacements.

<a name="label54"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ε</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mo>−</mo>
  <mi>z</mi>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (54) </div>

<a name="label55"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ε</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (55) </div>

where

<a name="label56"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>4</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>4</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>4</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (56) </div>

<a name="label57"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center center center center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>4</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>4</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>3</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>3</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mo>−</mo>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>4</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>4</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (57) </div>

<a name="label58"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mtable columnalign="center center center center center center center center center center" columnspacing="1em" rowspacing="4pt">
    <mtr>
      <mtd>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN">{</mo>
          <msub>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">(</mo>
              <msub>
                <mi>θ</mi>
                <mrow>
                  <mi>x</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">)</mo>
            </mrow>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
        </mrow>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>1</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mi>w</mi>
          <mrow>
            <mn>1</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>x</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>2</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>2</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mi>w</mi>
          <mrow>
            <mn>2</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>x</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>3</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>3</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mi>w</mi>
          <mrow>
            <mn>3</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>x</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>4</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <msub>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">(</mo>
            <msub>
              <mi>θ</mi>
              <mrow>
                <mi>y</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">)</mo>
          </mrow>
          <mrow>
            <mn>4</mn>
          </mrow>
        </msub>
      </mtd>
      <mtd>
        <mrow data-mjx-texclass="INNER">
          <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
          <msub>
            <mi>w</mi>
            <mrow>
              <mn>4</mn>
            </mrow>
          </msub>
          <mo data-mjx-texclass="CLOSE">}</mo>
        </mrow>
      </mtd>
    </mtr>
  </mtable>
</math>
<div style="text-align: right"> (58) </div>

Substitution of Eqs. ([54](#label54)) and ([55](#label55)) into the energy expression Eq. ([43](#label43)) yields for each plate element

<a name="label59"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>U</mi>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msup>
        <mi>d</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <msup>
        <mi mathvariant="normal">Ω</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
    </mrow>
  </msub>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>z</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mi>d</mi>
  <mi>z</mi>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>+</mo>
  <mfrac>
    <mi>κ</mi>
    <mn>2</mn>
  </mfrac>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msup>
        <mi>d</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <msup>
        <mi mathvariant="normal">Ω</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
    </mrow>
  </msub>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi>z</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>s</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mi>d</mi>
  <mi>z</mi>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (59) </div>

As a result, the element stiffness matrix for plate bending in case of thick plates can be expressed as

<a name="label60"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msup>
      <mi>K</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mfrac>
    <msup>
      <mi>h</mi>
      <mrow>
        <mn>3</mn>
      </mrow>
    </msup>
    <mn>12</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <msup>
        <mi mathvariant="normal">Ω</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
  <mo>+</mo>
  <mi>κ</mi>
  <mi>h</mi>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <msup>
        <mi mathvariant="normal">Ω</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>s</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
</math>
<div style="text-align: right"> (60) </div>

where $ h $ is the plate thickness.
 
{{% callout note %}}
One thing to be noted here is that shear energy becomes dominant compared to the bending energy as the plate thickness becomes very small compared to its side dimensions. This phenomenon is known as shear locking. The cause of this is that bending energy is proportional to $ h^{3} $ while shear energy is proportional to $ h $; therefore, as $ h $ gets smaller, the shear energy becomes dominant over the bending term. As a mean of solving this kind of problem, selective or reduced integration technique is used, which basically means under-integrating the shear energy term. As a general rule, bending term is integrated using the exact integration rule. For example, bilinear four-node isoparametric elements use the $ 2×2 $ Gauss-Legendre quadrature for bending while 1-point integration is used for shear term. For biquadratic nine-node elements we have $ 3×3 $ integrations for bending and $ 2×2 $ for shear.
{{% /callout %}}

## III.5 Plate element with displacement degrees of freedom
---

We have the plate bending developed in this section represented on the following figure, where $ x $, $ y $ and $ z $ describe global coordinates of the plate and $ u $, $ v $ and $ w $ are the displacements; $ h $ is the plate thickness. The $ xy $ plane is parallel to the midplane prior to deflection.

The displacement of any point can be described with

<a name="label61"></a>
$$u=u(x, y, z)$$
<div style="text-align: right"> (61) </div>

<a name="label62"></a>
$$v=v(x, y, z)$$
<div style="text-align: right"> (62) </div>

<a name="label63"></a>
$$w=w(x, y, z)$$
<div style="text-align: right"> (63) </div>

Meaning that the in-plane displacements $ u $ and $ v $ vary through the plate thickness as well as within the $ xy $-plane while the transverse displacements $ w $ remains constant through the plate thickness. In order to interpolate displacements with the help of shape functions and nodal displacements, two kinds of interpolations are needed: one interpolation within the $ xy $-plane and the other in the $ z $-axis.

{{< figure src="Figure%20III-6.png" caption="late element with displacement DOFs (Source: Young W. Kwon, Hyochoong Bang)" numbered="true" width="500">}}

In the $ xy $-plane during interpolation, shape functions $ N_{i}(x,y) $ are used where subscript $ i $ varies depending on the number of nodes on the $ xy $-plane. On the other hand, shape functions $ H_{j}(z) $ are used for interpolation along the $ z $-axis, where subscript $ j $ varies depending on the number of nodes along the plate thickness. Because two in-plane displacements are functions of $ x $, $ y $ and $ z $, both shape functions are used, while transversal displacement uses only shape functions $ N_{i}(x,y) $. With the help of isoparametric elements with mapping of the $ \xi\eta $-plane onto the $ xy $-plane and the $ \zeta $-axis to the $ z $-axis, the three displacements can be expressed as

<a name="label64"></a>
$$u=\sum_{i=1}^{N_{1}} \sum_{j=1}^{N_{2}} N_{i}(\xi, \eta) H_{j}(\zeta) u_{i j}$$
<div style="text-align: right"> (64) </div>

<a name="label65"></a>
$$v=\sum_{i=1}^{N_{1}} \sum_{j=1}^{N_{2}} N_{i}(\xi, \eta) H_{j}(\zeta) v_{i j}$$
<div style="text-align: right"> (65) </div>

<a name="label66"></a>
$$w=\sum_{i=1}^{N_{1}} N_{i}(\xi, \eta) w_{i}$$
<div style="text-align: right"> (66) </div>

in which $ N_{1} $ and $ N_{2} $ are the numbers of nodes in the $ xy $-plane (or $ \xi\eta $-plane) and $ z $-axis ($ \zeta $-axis), respectively. In addition, the first subscript for $ u $ and $ v $ denotes the node numbering in terms of the $ xy $-plane ($ \xi\eta $-plane) and the second subscript indicates the node numbering in terms of the $ z $-axis ($ \zeta $-axis).

In the following for further studying this plate type, we set up a case $ N_{1}=4 $ and $ N_{2}=2 $; that is, four-node quadrilateral shape functions are used for the $ xy $-plane interpolation and linear shape functions are employed for the $ z $-axis interpolation. Nodal displacements $ u_{i1} $ and $ v_{i1} $ are displacements on the bottom surface of the plate element, while displacements $ u_{i2} $ and $ v_{i2} $ are located on the top surface. As we can see in Eqs.([64](#label64)),([65](#label65)) through Eq.([66](#label66)) there is no rotational degree of freedom for this kind of bending element. This is represented in the previous figure, for ease of understanding.

In this present formulation, we have the both bending strain energy and transverse shear strain energy present. We can express bending and transverse shear energy in the following manner (with the help of displacements):

<a name="label67"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>ϵ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>ϵ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>γ</mi>
            <mrow>
              <mi>x</mi>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mi>u</mi>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>v</mi>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>w</mi>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (67) </div>

<a name="label68"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>γ</mi>
            <mrow>
              <mi>y</mi>
              <mi>z</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>γ</mi>
            <mrow>
              <mi>x</mi>
              <mi>z</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mi>u</mi>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>v</mi>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>w</mi>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (68) </div>

in the case $\{\epsilon_{b}\} $ is the bending strains and $\{\epsilon_{s}\} $ is the transverse shear strains. The normal strain along the plate thickness  $\{\epsilon_{z}\} $ is omitted here.
Substitution of displacements, Eqs.([64](#label64)), ([65](#label65)) through ([66](#label66)), into the kinematic equations, Eq.([67](#label67)) and ([68](#label68)), with $ N_{1}=4 $ and $ N_{2}=2 $ expresses both bending and shear strains in the following way:

<a name="label69"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>ϵ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>ϵ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>γ</mi>
            <mrow>
              <mi>x</mi>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mi mathvariant="normal">∂</mi>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mi>u</mi>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>v</mi>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>w</mi>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (69) </div>

where bending part is

<a name="label70"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
          <mn>1</mn>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mstyle scriptlevel="0">
      <mspace width="1em"></mspace>
    </mstyle>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
          <mn>2</mn>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mstyle scriptlevel="0">
      <mspace width="1em"></mspace>
    </mstyle>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
          <mn>3</mn>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mstyle scriptlevel="0">
      <mspace width="1em"></mspace>
    </mstyle>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
          <mn>4</mn>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (70) </div>

<a name="label71"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
        <mi>i</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>1</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <msub>
            <mi>H</mi>
            <mrow>
              <mn>2</mn>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>x</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (71) </div>

<a name="label72"></a>

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <mrow data-mjx-texclass="INNER">
        <mo data-mjx-texclass="OPEN">{</mo>
        <msubsup>
          <mi>d</mi>
          <mrow>
            <mn>1</mn>
          </mrow>
          <mrow>
            <mi>e</mi>
          </mrow>
        </msubsup>
        <mo data-mjx-texclass="CLOSE">}</mo>
      </mrow>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <mrow data-mjx-texclass="INNER">
        <mo data-mjx-texclass="OPEN">{</mo>
        <msubsup>
          <mi>d</mi>
          <mrow>
            <mn>2</mn>
          </mrow>
          <mrow>
            <mi>e</mi>
          </mrow>
        </msubsup>
        <mo data-mjx-texclass="CLOSE">}</mo>
      </mrow>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <mrow data-mjx-texclass="INNER">
        <mo data-mjx-texclass="OPEN">{</mo>
        <msubsup>
          <mi>d</mi>
          <mrow>
            <mn>1</mn>
          </mrow>
          <mrow>
            <mi>e</mi>
          </mrow>
        </msubsup>
        <mo data-mjx-texclass="CLOSE">}</mo>
      </mrow>
      <mstyle scriptlevel="0">
        <mspace width="1em"></mspace>
      </mstyle>
      <mrow data-mjx-texclass="INNER">
        <mo data-mjx-texclass="OPEN">{</mo>
        <msubsup>
          <mi>d</mi>
          <mrow>
            <mn>2</mn>
          </mrow>
          <mrow>
            <mi>e</mi>
          </mrow>
        </msubsup>
        <mo data-mjx-texclass="CLOSE">}</mo>
      </mrow>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
</math>
<div style="text-align: right"> (72) </div>

<a name="label73"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msubsup>
      <mi>d</mi>
      <mrow>
        <mi>i</mi>
      </mrow>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msubsup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>u</mi>
            <mrow>
              <mi>i</mi>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>v</mi>
            <mrow>
              <mi>i</mi>
              <mn>1</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>u</mi>
            <mrow>
              <mi>i</mi>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>v</mi>
            <mrow>
              <mi>i</mi>
              <mn>2</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>w</mi>
            <mrow>
              <mi>i</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (73) </div>

<a name="label74"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (74) </div>

where shear part is

<a name="label75"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="left left left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
            <msub>
              <mi>B</mi>
              <mrow>
                <mi>s</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">]</mo>
          </mrow>
        </mtd>
        <mtd>
          <mo>=</mo>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">[</mo>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>B</mi>
                <mrow>
                  <mi>s</mi>
                  <mn>1</mn>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
            <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>B</mi>
                <mrow>
                  <mi>s</mi>
                  <mn>2</mn>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>B</mi>
                <mrow>
                  <mi>s</mi>
                  <mn>3</mn>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>B</mi>
                <mrow>
                  <mi>s</mi>
                  <mn>4</mn>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
            <mo data-mjx-texclass="CLOSE">]</mo>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (75) </div>

<a name="label76"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
        <mi>i</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>N</mi>
            <mrow>
              <mi>i</mi>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>N</mi>
            <mrow>
              <mi>i</mi>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>N</mi>
                <mrow>
                  <mi>i</mi>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>N</mi>
            <mrow>
              <mi>i</mi>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>N</mi>
            <mrow>
              <mi>i</mi>
            </mrow>
          </msub>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>2</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>z</mi>
            </mrow>
          </mfrac>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <msub>
                <mi>H</mi>
                <mrow>
                  <mn>1</mn>
                </mrow>
              </msub>
            </mrow>
            <mrow>
              <mi mathvariant="normal">∂</mi>
              <mi>y</mi>
            </mrow>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (76) </div>

The constitutive equation for the isotropic material is

<a name="label77"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>σ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (77) </div>

where

<a name="label78"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>σ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>σ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>σ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msup>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
              <msub>
                <mi>τ</mi>
                <mrow>
                  <mi>x</mi>
                  <mi>y</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">}</mo>
            </mrow>
            <mrow>
              <mi>T</mi>
            </mrow>
          </msup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (78) </div>

<a name="label79"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mfrac>
    <mi>E</mi>
    <mrow>
      <mn>1</mn>
      <mo>−</mo>
      <msup>
        <mi>v</mi>
        <mrow>
          <mn>2</mn>
        </mrow>
      </msup>
    </mrow>
  </mfrac>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mi>v</mi>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mi>v</mi>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mfrac>
            <mrow>
              <mn>1</mn>
              <mo>−</mo>
              <mi>v</mi>
            </mrow>
            <mn>2</mn>
          </mfrac>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (79) </div>

for the bending components and

<a name="label80"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>σ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (80) </div>

where

<a name="label81"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>σ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>τ</mi>
            <mrow>
              <mi>y</mi>
              <mi>z</mi>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msup>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN" fence="true" stretchy="true" symmetric="true"></mo>
              <msub>
                <mi>τ</mi>
                <mrow>
                  <mi>x</mi>
                  <mi>z</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">}</mo>
            </mrow>
            <mrow>
              <mi>T</mi>
            </mrow>
          </msup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE" fence="true" stretchy="true" symmetric="true"></mo>
  </mrow>
</math>
<div style="text-align: right"> (81) </div>

<a name="label82"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>D</mi>
    <mrow>
      <mi>s</mi>
    </mrow>
  </msub>
  <mo>=</mo>
  <mfrac>
    <mi>E</mi>
    <mrow>
      <mn>2</mn>
      <mo stretchy="false">(</mo>
      <mn>1</mn>
      <mo>+</mo>
      <mi>v</mi>
      <mo stretchy="false">)</mo>
    </mrow>
  </mfrac>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="left left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mn>1</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>1</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (82) </div>

where Eq.([83](#label83)) is the material property matrix for the plane stress condition as usually assumed for the plate bending theory.

For a unidirectional fibrous composite, the material property matrices become

<a name="label83"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>D</mi>
    <mrow>
      <mi>b</mi>
    </mrow>
  </msub>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>D</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>D</mi>
            <mrow>
              <mn>12</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>D</mi>
            <mrow>
              <mn>12</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>D</mi>
            <mrow>
              <mn>22</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>D</mi>
            <mrow>
              <mn>33</mn>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (83) </div>

in which

<a name="label84"></a>
$$D_{11}=\frac{E_{1}}{1-v_{12} v_{21}}$$
<div style="text-align: right"> (84) </div>

<a name="label85"></a>
$$D_{12}=\frac{E_{1} v_{21}}{1-v_{12} v_{21}}$$
<div style="text-align: right"> (85) </div>

<a name="label86"></a>
$$D_{22}=\frac{E_{2}}{1-v_{12} v_{21}}$$
<div style="text-align: right"> (86) </div>

<a name="label87"></a>
$$D_{33}=G_{12}$$
<div style="text-align: right"> (87) </div>

and

<a name="label88"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>G</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>G</mi>
            <mrow>
              <mn>12</mn>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (88) </div>

Here, $ 1 $ and $ 2 $ denote the longitudinal and transverse directions of the unidirectional composite. $ E $ is the elastic modulus, $ G_{ij} $ is the shear modulus of the $ i-j $ plane and $ v_{ij} $ is the Poisson’s ratio for strain in the $ j $-direction when stressed in the $ i $-direction. There are five independent material properties for Eq.([83](#label83)) through ([88](#label88)) because of the reciprocal relation $ \frac{v_{12}}{E_{1}}=\frac{v_{21}}{E_{2}} $.

The total potential energy can be expressed as

<a name="label89"></a>
$$\Pi=U-W$$
<div style="text-align: right"> (89) </div>

where the internal strain energy $ U $ consists of two parts

<a name="label90"></a>
$$U=U_{b}+U_{s}$$
<div style="text-align: right"> (90) </div>

The bending strain energy $ U_{b} $ is

<a name="label91"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>U</mi>
    <mrow>
      <mi>b</mi>
    </mrow>
  </msub>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi mathvariant="normal">Ω</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>σ</mi>
        <mrow>
          <mi>b</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
</math>
<div style="text-align: right"> (91) </div>

and the transverse shear strain energy is

<a name="label92"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>U</mi>
    <mrow>
      <mi>s</mi>
    </mrow>
  </msub>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <mi mathvariant="normal">Ω</mi>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msub>
        <mi>σ</mi>
        <mrow>
          <mi>s</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msub>
      <mi>ϵ</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
</math>
<div style="text-align: right"> (92) </div>

where $ \Omega $ is the plate domain. After finite element discretization, substitution of the previous equations into Eqs.([91](#label91)) and ([92](#label92)) gives

<a name="label93"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>U</mi>
    <mrow>
      <mi>b</mi>
    </mrow>
  </msub>
  <mo>=</mo>
  <munder>
    <mo data-mjx-texclass="OP">∑</mo>
    <mrow>
      <mi>e</mi>
    </mrow>
  </munder>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msup>
        <mi>d</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <msup>
        <mi mathvariant="normal">Ω</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>b</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>b</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (93) </div>

and

<a name="label94"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <msub>
    <mi>U</mi>
    <mrow>
      <mi>s</mi>
    </mrow>
  </msub>
  <mo>=</mo>
  <munder>
    <mo data-mjx-texclass="OP">∑</mo>
    <mrow>
      <mi>e</mi>
    </mrow>
  </munder>
  <mfrac>
    <mn>1</mn>
    <mn>2</mn>
  </mfrac>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">{</mo>
      <msup>
        <mi>d</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
      <mo data-mjx-texclass="CLOSE">}</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <msub>
    <mo data-mjx-texclass="OP">∫</mo>
    <mrow>
      <msup>
        <mi mathvariant="normal">Ω</mi>
        <mrow>
          <mi>e</mi>
        </mrow>
      </msup>
    </mrow>
  </msub>
  <msup>
    <mrow data-mjx-texclass="INNER">
      <mo data-mjx-texclass="OPEN">[</mo>
      <msub>
        <mi>B</mi>
        <mrow>
          <mi>s</mi>
        </mrow>
      </msub>
      <mo data-mjx-texclass="CLOSE">]</mo>
    </mrow>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>D</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <msub>
      <mi>B</mi>
      <mrow>
        <mi>s</mi>
      </mrow>
    </msub>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mi>d</mi>
  <mi mathvariant="normal">Ω</mi>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mi>e</mi>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (94) </div>

where summation is performed over the total number of finite elements and superscript $ e $ indicates each element. Kinematic matrices $ \left[B_{b}\right] $ and $ \left[B_{s}\right] $ are provided in Eqs.([70](#label70)) and ([75](#label75)) while constitutive matrices $ \left[D_{b}\right] $ and $ \left[D_{s}\right] $ are given in Eq.([79](#label79)) and ([82](#label82)) for the isotropic material, and in Eqs.([83](#label83)) and ([88](#label88)) for the unidirectional composite.

The external work is written as

<a name="label95"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mi>W</mi>
  <mo>=</mo>
  <mo fence="false" stretchy="false">{</mo>
  <mi>d</mi>
  <msup>
    <mo fence="false" stretchy="false">}</mo>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mo fence="false" stretchy="false">{</mo>
  <mi>F</mi>
  <mo fence="false" stretchy="false">}</mo>
</math>
<div style="text-align: right"> (95) </div>

in which $ \{d\} $ is the system nodal displacement vector and $ \{F\} $ is the system force vector. There is no rotational degree of freedom for the present element, the external moment is applied to the force vector as a couple applied on the top and bottom nodes of the plate element shown in the previous figure.

Invoking the stationary value of the total potential energy yields the finite element matrix equation. The element stiffness matrix can be expressed as

  
<a name="label96"></a>
$$\left[K_{e}\right]=\int_{\Omega^{e}}\left[B_{b}\right]^{T}\left[D_{b}\right]\left[B_{b}\right] d \Omega+\int_{\Omega^{e}}\left[B_{s}\right]^{T}\left[D_{s}\right]\left[B_{s}\right] d \Omega$$
<div style="text-align: right"> (96) </div>

## III.6 Shell made of in-plane and bending elements
---

Shells usually are made up of curved surfaces, but if we consider the radius of curvature infinitely large, then the geometry of the shell becomes a flat plate. When a shell is divided into a number of small finite elements, each element may be considered as a flat plate with a slightly different orientation is space. Thus, each element may be modeled as a plate bending element. However, there is the problem of different orientation in connecting plate elements, which cause in-plane deformation in the neighbouring elements.

As a result, a shell element can be obtained as a combination of a plate bending element and a plane stress element in the same way that a 2-D frame element is obtained from a beam bending element and a bar element. In the case of plate bending an element has a transverse defection and two bending rotations as degrees of freedom per node, while the plane stress element has two in-plane displacements per node. This gives us five degrees of freedom per node, three displacements and two rotations, the stiffness matrix of this kind of shell element is given as

<a name="label97"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>K</mi>
                <mrow>
                  <mi>b</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mo stretchy="false">[</mo>
            <mn>0</mn>
            <mo stretchy="false">]</mo>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow>
            <mo stretchy="false">[</mo>
            <mn>0</mn>
            <mo stretchy="false">]</mo>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>K</mi>
                <mrow>
                  <mi>m</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>d</mi>
            <mrow>
              <mi>b</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>d</mi>
            <mrow>
              <mi>m</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">{</mo>
            <msub>
              <mi>F</mi>
              <mrow>
                <mi>b</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">{</mo>
            <msub>
              <mi>F</mi>
              <mrow>
                <mi>m</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (97) </div>

where we have $ K $, $ d $ and $ F $ representing stiffness matrix, nodal displacement/rotation vector and nodal force/moment vector respectively. The matrices are made up of two parts, one for the plate bending and one for plate stretching. Subscripts $ b $ and $ m $ denote bending and membrane (stretching) deformations of the shell element.

When shell elements are oriented differently, for example the corners of a cube or box-type shell structure, a bending rotation in one element becomes a so-called drilling rotation in another element. Therefore, to assemble the element matrices and vectors into the system matrix and vector, the drilling rotational degree of freedom $ \theta_{z} $ should be included. Resulting from this, the degrees of freedom of the element matrix and vector shall increase by one (to include the drilling degree of freedom per node). This leads to equation ([97](#label97)) to be modified into

<a name="label98"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>K</mi>
                <mrow>
                  <mi>b</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mo stretchy="false">[</mo>
            <mn>0</mn>
            <mo stretchy="false">]</mo>
          </mrow>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <mtable columnalign="center center" columnspacing="1em" rowspacing="4pt">
                <mtr>
                  <mtd>
                    <mn>0</mn>
                  </mtd>
                </mtr>
              </mtable>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <mtable columnalign="center center" columnspacing="1em" rowspacing="4pt">
                <mtr>
                  <mtd>
                    <msub>
                      <mi>K</mi>
                      <mrow>
                        <mi>m</mi>
                      </mrow>
                    </msub>
                  </mtd>
                </mtr>
              </mtable>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">{</mo>
            <msub>
              <mi>d</mi>
              <mrow>
                <mi>b</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">{</mo>
            <msub>
              <mi>d</mi>
              <mrow>
                <mi>m</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>θ</mi>
            <mrow>
              <mi>z</mi>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">{</mo>
            <msub>
              <mi>F</mi>
              <mrow>
                <mi>b</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mrow data-mjx-texclass="INNER">
            <mo data-mjx-texclass="OPEN">{</mo>
            <msub>
              <mi>F</mi>
              <mrow>
                <mi>m</mi>
              </mrow>
            </msub>
            <mo data-mjx-texclass="CLOSE">}</mo>
          </mrow>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (98) </div>

The matrix and vectors in equation ([98](#label98)) are expressed in terms of a local coordinate system that has $ x $- and $ y $-axes along the midplane of each flat shell element and the $ z $-axis normal to the plane. To assemble those matrices and vectors into the system matrix and vectors, the nodal degrees of freedom in terms of each local axis must be transformed into the corresponding nodal degrees of freedom in terms of the global coordinate axes common to all elements. Having the transformation matrix called $ \left[T\right] $,

<a name="label99"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mtext>local</mtext>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mo stretchy="false">[</mo>
  <mi>T</mi>
  <mo stretchy="false">]</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>d</mi>
      <mrow>
        <mtext>global</mtext>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (99) </div>

Matrix $ \left[T\right] $ transforms the global degrees of freedom into the local degrees of freedom. It consists of direction cosines between the global and local coordinate systems.

At every node we have the relation between local and global degrees of freedom expressed as

<a name="label100"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msup>
            <mi>u</mi>
            <mrow>
              <mtext>local</mtext>
            </mrow>
          </msup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msup>
            <mi>v</mi>
            <mrow>
              <mtext>local</mtext>
            </mrow>
          </msup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msup>
            <mi>w</mi>
            <mrow>
              <mtext>local</mtext>
            </mrow>
          </msup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msubsup>
            <mi>θ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
            <mrow>
              <mtext>local</mtext>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msubsup>
            <mi>θ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
            <mrow>
              <mtext>local</mtext>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msubsup>
            <mi>θ</mi>
            <mrow>
              <mi>z</mi>
            </mrow>
            <mrow>
              <mtext>local</mtext>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
        <mtd>
          <msub>
            <mi>l</mi>
            <mrow>
              <mn>11</mn>
            </mrow>
          </msub>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <mtable columnalign="left" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <msup>
            <mi>u</mi>
            <mrow>
              <mtext>global</mtext>
            </mrow>
          </msup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msup>
            <mi>v</mi>
            <mrow>
              <mtext>global</mtext>
            </mrow>
          </msup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msup>
            <mi>w</mi>
            <mrow>
              <mtext>global</mtext>
            </mrow>
          </msup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msubsup>
            <mi>θ</mi>
            <mrow>
              <mi>x</mi>
            </mrow>
            <mrow>
              <mtext>global</mtext>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msubsup>
            <mi>θ</mi>
            <mrow>
              <mi>y</mi>
            </mrow>
            <mrow>
              <mtext>global</mtext>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <msubsup>
            <mi>θ</mi>
            <mrow>
              <mi>z</mi>
            </mrow>
            <mrow>
              <mtext>global</mtext>
            </mrow>
          </msubsup>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (100) </div>

where $ l_{ij} $ is the direction cosine between local axis $ x_{i} $ and the global axis $ X_{j} $. This relationship can be used for each node. Thus, the transformation matrix $ \left[T\right] $ for a four-node element becomes

<a name="label101"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mo stretchy="false">[</mo>
  <mi>T</mi>
  <mo stretchy="false">]</mo>
  <mo>=</mo>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">[</mo>
    <mtable columnalign="center center center center" columnspacing="1em" rowspacing="4pt">
      <mtr>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>T</mi>
                <mrow>
                  <mi>d</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>T</mi>
                <mrow>
                  <mi>d</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>T</mi>
                <mrow>
                  <mi>d</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
      </mtr>
      <mtr>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mn>0</mn>
        </mtd>
        <mtd>
          <mrow>
            <mrow data-mjx-texclass="INNER">
              <mo data-mjx-texclass="OPEN">[</mo>
              <msub>
                <mi>T</mi>
                <mrow>
                  <mi>d</mi>
                </mrow>
              </msub>
              <mo data-mjx-texclass="CLOSE">]</mo>
            </mrow>
          </mrow>
        </mtd>
      </mtr>
    </mtable>
    <mo data-mjx-texclass="CLOSE">]</mo>
  </mrow>
</math>
<div style="text-align: right"> (101) </div>

where matrix $ \left[T_{d}\right] $ is that used in Eq. ([100](#label100)) having a size of $ 6×6 $.

Using the transformation matrix, the transformed stiffness matrix and load vector are given below:

<a name="label102"></a>
$$\left[K^{g l o b a l}\right]=[T]^{T}\left[K^{\text {local}}\right][T]$$
<div style="text-align: right"> (102) </div>

<a name="label103"></a>
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>F</mi>
      <mrow>
        <mtext>global</mtext>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
  <mo>=</mo>
  <mo stretchy="false">[</mo>
  <mi>T</mi>
  <msup>
    <mo stretchy="false">]</mo>
    <mrow>
      <mi>T</mi>
    </mrow>
  </msup>
  <mrow data-mjx-texclass="INNER">
    <mo data-mjx-texclass="OPEN">{</mo>
    <msup>
      <mi>F</mi>
      <mrow>
        <mtext>local</mtext>
      </mrow>
    </msup>
    <mo data-mjx-texclass="CLOSE">}</mo>
  </mrow>
</math>
<div style="text-align: right"> (103) </div>

{{< figure src="Figure%20III-7.png" caption="Forces and moments in an elementary plate/shell (Source: J.N. Reddy)" numbered="true" width="500">}}

{{% callout note %}}
In the case when the shell is actually flat, the shell stiffness becomes singular because of the singular terms associated with the drilling degrees of freedom. In order to avoid such a problem, a small number can be added to the diagonal term of the matrix in Eq. ([98](#label98)) associated with the drilling degree of freedom $ \theta_{z} $. This number should not be too small as to cause the modified matrix to be singular or near singular. Also, we should avoid using too large values as well because it is an arbitrary addition.
{{% /callout %}}
