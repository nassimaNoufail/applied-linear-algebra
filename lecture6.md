Lecture 6: Projections
======================

In class, we worked through much of the mathematics of this chapter
already.  Make sure you understand why and how the calculations work
in the rest of that worksheet.  Also, make sure you read the chapter.

<div class="exercise">
Text exercise 6.1
</div>

<div class="exercise">
Text exercise 6.3
</div>

<div class="exercise">
Text exercise 6.4
</div>

<div class="exercise">
Text exercise 6.5
</div>


Lecture 7: QR
======================

We didn't talk about the "When Vectors Become Continuous Functions"
section in class.  If you plan to do things with physics, signal processing, or
differential equations, you should really read this section, though.

<div class="exercise">
Text exercise 7.1
</div>
<div class="exercise">
Text exercise 7.5
</div>

Lecture 8: Gram-Schmidt
=======================

We'll have a review question asking about modified Gram-Schmidt later.
Also, a question involving numerical stability was given in class.

Lecture 9: Matlab
=======================

We didn't talk about this chapter in class.  You should read through
Experiments 2 and 3 in the chapter, though, to see the results.  You
can do some of the calculations in Octave.  Plotting doesn't quite
work yet in the demo below, though.

<octavecell>

```
x = (-128:128)'/128
A=[x.^0 x.^1 x.^2 x.^3];
[Q, R] = qr(A, 0);
scale = Q(257, :);
Q = Q*diag(1 ./scale);
Q
```

</octavecell>

Lecture 10: Householder
=======================

Here is an example of using Sage to compute a QR decomposition.  For
matrices over `RDF`, Sage uses Householder reflections to compute the decomposition
(internally using
[Scipy](http://docs.scipy.org/doc/scipy/reference/generated/scipy.linalg.qr.html)
and the LAPACK functions
[dgeqrf](http://www.netlib.org/lapack/double/dgeqrf.f) and [dorgqr](http://www.netlib.org/lapack/double/dorgqr.f)).

<sagecell>

```
A=matrix(RDF,3,3,[3,2,-1, 2,5,4, 3,1,0])
Q,R=A.QR()

html.table([
["$A$", A],
["$Q$", Q], 
["$R$", R], 
["$QQ^*$", Q*Q.H], # should be close to the identity since Q is unitary
["$A-QR$", A-Q*R], # should be close to zero
])
```

</sagecell>

<div class="exercise">
Text exercise 10.1
</div>

<div class="exercise"> 

<!-- matrix(QQ,4,3,[2,4,-1, 3,2,3, 3,-2,1, 5,2,0]) -->

Let $$A=\begin{bmatrix}2&4&-1\\3&2&3\\3&-2&1\\5&2&0\end{bmatrix}.$$

Calculate a full QR decomposition for $A$ in the following ways (I've
used the book notation for the intermediate quantities).  Make
sure to show all of your work for each step.  You can use a computer
or calculator to do the arithmetic, and you can round off to 4
decimals in intermediate calculations.

#. Modified Gram-Schmidt:
    #. Calculate $q_1$ and the projector $P_{\perp q_1}$
	#. Calculate the new vectors $v^{(2)}_2$ and $v^{(2)}_3$
	#. Calculate $q_2$ and the projector matrix $P_{\perp q_2}$
	#. Calculate the new vector $v^{(3)}_3$
	#. Calculate $q_3$
	#. Calculate a 4 by 4 $Q$ and a 4 by 3 $R$ (show how you get them from your
       calculations above) and double-check that $Q$ is unitary and
       that $A=QR$.
  
#. Householder reflections.  Use the strategy mentioned in the book to
   calculate the appropriate direction for $v$ in each case below to
   avoid numerical error.
    #. Calculate $Q_1$ and the $v$ corresponding to $Q_1$, as well as $Q_1A$.
	#. Calculate $Q_2$ and the $v$ corresponding to $Q_2$.
	#. Calculate $Q$ and $R$ (show how you get them from your
       calculations above) and double-check that $Q$ is unitary and
       that $A=QR$.

</div>

Lecture 11: Least Squares
=========================

<div class="exercise">

Use least squares to find the best-fitting line for the points
$(2,3)$, $(-1,2)$, $(5,4)$, $(3,1)$, $(1,3)$.  Use QR decomposition
(Algorithm 11.2) to do the least squares.  Your final answer
should be a line of the form $y=a_0+a_1x$ (find $a_0$ and $a_1$).  You
can use Sage or other software to compute $\hat Q$ and $\hat R$ (in
Sage, compute the full QR decomposition and then delete the necessary
rows and columns to get a reduced QR decomposition).

</div>


Lecture 12: Conditioning and Condition numbers
==============================================

<div class="exercise">

Show that if $A$ is square and nonsingular, then
$$\frac{\norm{x}}{\norm{Ax}}\leq \norm{A^{-1}}.$$

</div>

<div class="exercise">

Show that if $A\in \mathbb{C}^{m\times m}$ is nonsingular and has
smallest singular value $\sigma_m$, then $\norm{A^{-1}}_2=1/\sigma_m$.

</div>
