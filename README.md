# 42_Fractol_Resources
> Computer Graphics Fractals

<!-- mtoc-start -->

* [Complex Numbers](#complex-numbers)
  * [Initializing a Complex Number](#initializing-a-complex-number)
  * [Deriving the Formula for Squaring a Complex Number](#deriving-the-formula-for-squaring-a-complex-number)
* [Fractal Sets](#fractal-sets)
  * [The Mandelbrot Set](#the-mandelbrot-set)
    * [Generating the Mandelbrot Set](#generating-the-mandelbrot-set)
* [Generating the Newton-Raphson Set](#generating-the-newton-raphson-set)
  * [Seeking Polynomial Roots](#seeking-polynomial-roots)
  * [Newton's Method](#newtons-method)
  * [Differences & Improved Guesses (Step Size)](#differences--improved-guesses-step-size)
  * [The Newton-Raphson Method](#the-newton-raphson-method)
  * [Finding Roots in the Complex Plane](#finding-roots-in-the-complex-plane)
* [Fractal Generation Techniques](#fractal-generation-techniques)
  * [Escape-Time Fractals](#escape-time-fractals)
  * [Iterated Function Systems](#iterated-function-systems)
  * [Random Fractals](#random-fractals)
  * [Orbit Trap Method](#orbit-trap-method)
* [Refs](#refs)
  * [Docs](#docs)
  * [MiniLibX](#minilibx)
  * [Articles](#articles)
    * [Real Numbers](#real-numbers)
    * [Value of i](#value-of-i)
  * [Math Utils](#math-utils)
* [Repos](#repos)
* [Tools](#tools)
* [Videos](#videos)
* [LaTeX](#latex)
* [Footnotes](#footnotes)

<!-- mtoc-end -->
## Complex Numbers

### Initializing a Complex Number

> $Z = a + bi$
>
> where
>
> $a$ = Real part;
>
> $b$ = Imaginary part;
>
> $i^2 = -1$  || $i = \sqrt{-1}$
>

### Deriving the Formula for Squaring a Complex Number

> $(x + yi)^2 =$
>
> $= (x + yi) * (x + yi)$
>
> $= x^2 + xyi + xyi + y^2i^2$
>
> $= x^2 + 2xyi - y^2$
>
> $= x^2 - y^2 + 2xyi$

___
## Fractal Sets

Julia & Mandelbrot Sets are defined by:

> $Z_{n+1} = Z_{n} + c$

Z = a Complex number at n-th iteration;
c = Constant complex number corresponding to a point in the complex plane.
### The Mandelbrot Set
Was discovered by Benoit B. Mandelbrot while investigating mappings of the function:
> $f(z) = z^2 + c$

Is generated by iterating a simple function on the points of the complex plane.
- Points that `produce a cycle` (the same value over and over again) fall in the set;
- Points that `diverge` (give ever-growing values) lie outside it [Different colors represent different rates of diversion].
#### Generating the Mandelbrot Set

- Start from point $Z_0$ of the complex plane;
- Use the quadratic recurrence equation $Z_{n+1} = Z_{n}^2 + Z_{0}$ to obtain a sequence of complex numbers $Z_{n}$;

> - The points $Z_{n}$ are said to form the orbit of $Z_{0}$;
> - The Mandelbrot set, denoted by `M` is defined:
>
> If the orbit $Z_n$ fails to go to infinity,
>
> > we say that $Z_{n}$ is contained within the set $M$.
> > real numbers that are contained within the set to be in between $-2$ and $1/4$
> > imaginary numbers on the other hand have to be in between $-0.6i$ and $0.6i$
>
> If the orbit $Z_n$ does go to infinity,
>
> > we say that the point $Z_{0}$ is outside $M$.## The Julia Set

___
## Generating the Newton-Raphson Set

The Newton-Raphson Set is an infinite family of fractals generated by the iterative Newton-Raphson method of solving polynomials.

The starting point will be to assume some kind of polynomial and then find its roots (When the equation solves to zero).

> Example.: $P(x) = x^5 + x^2 - x - 0.2 = 0$

This polynomial has 3 roots:

> $P(x) = -1.193$
>
> $P(x) = -0.1709$
>
> $P(x) = 0.8119$
>
> > Check out its [graph](https://www.desmos.com/calculator/fksk7o2p5l)!

### Seeking Polynomial Roots

But how do we compute the roots? This is a very common question in engineering and computer graphics.

> [!Note]
>
> For instance in compute graphics, the text on the screen is usually not defined using pixel values, instead they are defined as a bunch of polynomial curves know as `bezier curves`.
>
> [Bezier Curves](https://en.wikipedia.org/wiki/B%C3%A9zier_curve)

If the problem at hand involves a quadratic function, then we can use the quadratic formula:

> **Quadratic Function**
>
> $ax^2 + bx + c = 0;$
>
> **Quadratic Polynomial Formula**
>
> $r_1,r_2 = \dfrac{-b ± \sqrt{b^2 - 4ac}}{2a}$

> [!Note]
>
> This formula is ubiquitously used to calculate light effects and general 3D manipulation during the production of games and animation movies.
>
> **Learn More**:
> - [Quadratic Polynomial Formula](https://en.wikipedia.org/wiki/Quadratic_formula)
> - [3D GRAPHING QUADRATIC EQUATIONS WITH SIMULATION METHODOLOGY](https://www.globusjournal.com/wp-content/uploads/2020/03/GMIT-JD15-Rajeev.pdf)
> - [General Quadratic Equation in 3-D](https://www.maplesoft.com/support/help/maple/view.aspx?path=MathApps%2FGeneralQuadraticEquationIn3D)

There is also a Cubic Polynomial Formula that can be applied to Cubic Functions:

> **Cubic Formula**
>
> $x^3 +px + q = 0;$
>
> **Cubic Polynomial Formula**
>
> $root = \sqrt[3]{-\dfrac{q}{2} + \sqrt{\dfrac{q^2}{4} + \dfrac{p^3}{27}}} + \sqrt[3]{-\dfrac{q}{2} - \sqrt{\dfrac{q^2}{4} + \dfrac{p^3}{27}}}$
>
> **Learn More**
> - [Mathologer : 500 years of NOT teaching THE CUBIC FORMULA. What is it they think you can't handle?](https://www.youtube.com/watch?v=N-KXStupwsc)

Now, you might be wondering about higher order polynomial formulas.

- A Quartic formula exists but no one really uses it in practice due to its complexity.
- After that, there is no analogous formula to solve Quintic or higher order polynomials. This is know as the **Unsolvability of the Quintic**.

In other words, it is possible to prove that for an extensive set of standard functions (that use $+$, $-$, $*$, $/$, and $\sqrt[n]{ }$, $sin$, $cos$, $exp$, $log$, etc), there is no way to combine them together that allows us to plug in the coefficients of quintic polynomial and always get out a root.

This unsolvability issue in a way doesn't matter because we have other ways to approximate a solution to this kind of equation with whatever level of precision necessary.

A common way to achieve this is by applying **Newton's Method**.

___
### Newton's Method

Take our previous polynomial example:

> $P(x) = x^5 + x^2 - x - 0.2 = 0$

The algorithm starts with a random guess, let's call it $X_0$.

Most likely the initial output of our polynomial at $X_0$ will not be 0, so we haven't found the solution.

> Guess : $x_0 = 1.3$

This return value is some other value that represents the **height** of the curve at $X_0$.

To improve the guess, we have to ask,

> **When does the linear approximation to the function around that value equal zero?**
>
> In other words, if we were to draw a tangent line to the graph at this point, when does this tangent line cross the x-axis?

Assuming that this tangent is a decent approximation of the function in the general vicinity of some true root, the  spot where this approximation equals zero should bring us closer to a true root.

As long as we are able to take a derivative of this function, (which with polynomials is always a possibility) we can compute the slope of this linear approximation.

### Differences & Improved Guesses (Step Size)

Then how do we find out the difference between the current guess and an improved guess? **What is the size of this step?**

One way to think about this, is to consider the fact that the slope of the tangent line, it's rise being greater than the run, suggests the **height of this graph divided by the length of the step**.

> **Slope / Tangent**
>
> $Slope = \dfrac{P(x_0)}{-Step}$

On the other hand the slope of this tangent line is the derivative of the polynomial at that point.

> **Derivative**
>
> $P'(0_0) =\dfrac{P(x_0)}{-Step}$
>
> > Taking our previous polynomial example:
> >
> > $P(x) = x^5 + x^2 - x - 0.2 = 0$
> >
> > We get its derivative as:
> >
> > $P'(x) = 5x^4 + 2x - 1$

So if we rearrange this equation $P'(x_0) =\dfrac{P(x_0)}{-Step}$, we get a simple expression that gives us the ability to compute this step size:

> $Step = \dfrac{P(x_0)}{P'(x_0)}$

So the next guess will be $X_1$ adjusted by the step size:

$X_1 = X_0 - \dfrac{P(x_0)}{P'(x_0)}$

After that we can repeat the process. We compute the value of this function and the slope at this new guess, which gives us a new linear approximation. Then make the next guess $x_2$, wherever that tangent line crosses the x-axis.

> Guess : $x_2 = 1.054$

Repeat this process enough times and before too long you'll find yourself extremely close to a true root.

___

So the formula to calculate the next step size is:

> **Step Size Formula**
>
> $x_{n+1} = x_n - \dfrac{P(x_0)}{P'(x_0)}$

___
A few intuitions worthy of note:
- If $P(x_0)$ is really large, and the graph gets real high, we need to take a larger step to get closer to a true root.
- But if $P'(x_0)$ is also really large, making the slope of the graph steeper, we need to take a smaller step to get closer to a true root.
- While it works great when we start calculations near a root, where it converges really quickly, if your initial guess is far from a root it can find a couple weaknesses.
	- In some cases the sequence of new guesses that we get bounces around the local minimum of a function sitting above the x-axis.
	- This makes sense since the linear approximation of the function around these values all the way to the right, is entirely unrelated to the nature of the function around its true root. It gives no useful information about the true root.
	- It is only when by chance this process is able to throw the new guess off far enough to the left that the sequence of new guesses is able to approximate the true root.

___
### The Newton-Raphson Method

This was a method used by Newton to solve polynomial expressions. He made it look much more complicated than it needed to be. Luckily a few years later Joseph Rafson published a simpler, more accessible version much more alike to the method we are discussing. Because of this it is commonly known as the **Newton-Raphson Method**, a recurrent topic in calculus classes.

___
### Finding Roots in the Complex Plane





___
## Fractal Generation Techniques
### Escape-Time Fractals
### Iterated Function Systems
### Random Fractals
### Orbit Trap Method

___
## Refs
### Docs
- [42Docs](https://harm-smits.github.io/42docs/)
- [Fractals Educators Guide](https://fractalfoundation.org/fractivities/FractalPacks-EducatorsGuide.pdf)
- [Lode's Computer Graphics Tutorial : Julia Mandelbrot Set](https://lodev.org/cgtutor/juliamandelbrot.html)
- [Newtown's Fractal](https://young.physics.ucsc.edu/242/newton.pdf)
- [Newton-Raphson Equations Solutions](https://www.sciencedirect.com/topics/mathematics/newton-raphson-method#:~:text=The%20Newton%2DRaphson%20method%20begins,0%20crosses%20the%20x%2Daxis.)
- [Mathologer : 500 years of NOT teaching THE CUBIC FORMULA. What is it they think you can't handle?](https://www.youtube.com/watch?v=N-KXStupwsc)
### MiniLibX
- [minilibx-linux](https://github.com/42Paris/minilibx-linux)
- [minilibx : harm-smits Docs](https://harm-smits.github.io/42docs/libs/minilibx/getting_started.html)
- [minilibx : ilkou Docs](https://github.com/ilkou/minilibx)
- [minilibx : 42-cursus Docs](https://42-cursus.gitbook.io/guide/minilibx)
- [events-with-the-minilibx](https://aurelienbrabant.fr/blog/events-with-the-minilibx)
- [minilibx (in Rust)](https://docs.rs/minilibx/latest/minilibx/)
- [minilibx : ft_libgfx](https://github.com/qst0/ft_libgfx?tab=readme-ov-file)
- [minilibx : Gontjarow](https://gontjarow.github.io/MiniLibX/)
### Articles
- [Fractal - Wikipedia](https://en.wikipedia.org/wiki/Fractal)
- [History of Fractals](https://nnart.org/history-of-fractals/)
- [What is Wonderdraft?](https://nnart.org/what-is-wonderdraft/)
- [Understanding Julia and Mandelbrot Sets](https://www.karlsims.com/julia.html)
- [Tag: Complex Numbers — Acko.net](https://acko.net/tag/complex-numbers/)
- [Complex Analysis](https://complex-analysis.com/content/mandelbrot_set.html)
- [Classica Iterated Function Systems](https://larryriddle.agnesscott.org/ifs/ifs.htm)
#### Real Numbers
- [Real Numbers (Definition, Properties and Examples)](https://byjus.com/maths/real-numbers/)
#### Value of i
- [Value of i in Complex Numbers - Powers of i Chart](https://byjus.com/maths/value-of-i/)
- [Value of I - Commonly Used Values of i](https://www.vedantu.com/maths/value-of-i)
### Math Utils
- [How to scale down a range of numbers with a known min and max value](https://stackoverflow.com/questions/5294955/how-to-scale-down-a-range-of-numbers-with-a-known-min-and-max-value)
## Repos
- [fract-ol: graphically beautiful fractals | Medium](https://medium.com/@leogaudin/fract-ol-creating-graphically-beautiful-fractals-6664b6b045b5)
- [fract-ol — render beautiful sets. | by Braulio Santos | Jan, 2024 | Medium](https://medium.com/@by1jorgesantos/fract-ol-render-beautiful-sets-0699a378b953)
- [GitHub - agavrel/42-fractol: Infographic \~ Fractal](https://github.com/agavrel/42-fractol)
- [GitHub - Alexdelia/42-fract-ol: 42 project around 2D fractal in minilibx](https://github.com/Alexdelia/42-fract-ol)
- [GitHub - aamaral-42/42_fract-ol: 42 project](https://github.com/aamaral-42/42_fract-ol)
## Tools
- [Online graphing calculator — NumWorks](https://www.numworks.com/simulator/)
## Videos
- [Idiot's guide to fractals](https://www.youtube.com/watch?v=gfVmtaOUER8)
- [What's so special about the Mandelbrot Set? - Numberphile](https://youtu.be/FFftmWSzgmk?si=QebM2_Ny866hULFQ)
- [The dark side of the Mandelbrot set - Mathologer](https://youtu.be/9gk_8mQuerg?si=mCjcqvcn6kVsQN8Y)
- [Playlist about everything and anything Mandelbrot and Julia](https://www.youtube.com/watch?v=7MotVcGvFMg&list=PL9tHLTl03LqG4ajDvqyfCDMKSxmR_plJ3)
- [Beyond the Mandelbrot set, an intro to holomorphic dynamics](https://youtu.be/LqbZpur38nw?si=7gpxDJIpsfJYp_0m)
- [Draw a Pollock painting with the minilibX](https://www.youtube.com/watch?v=9eAPbNUQD1Y)
- [Introduction to the minilibX : a simple X-Window programming API in C](https://www.youtube.com/watch?v=bYS93r6U0zg&t=0s)
## LaTeX
- https://wch.github.io/latexsheet/latexsheet-0.png
- [users.dickinson.edu/\~richesod/latex/latexcheatsheet.pdf](https://users.dickinson.edu/~richesod/latex/latexcheatsheet.pdf)
- [LaTeX/Mathematics - Wikibooks, open books for an open world](https://en.wikibooks.org/wiki/LaTeX/Mathematics)
- [Markdown and LaTeX introduction](https://ashki23.github.io/markdown-latex.html)
## Footnotes

[^1]: [The Fractal Geometry of Nature - Benoit B. Mandelbrot - Google Livros](https://books.google.pt/books?id=0R2LkE3N7-oC&redir_esc=y)
[^2]: [Are Fractals or Fractal Curves Differentiable?](https://nnart.org/are-fractals-differentiable/)
[^3]: [How to Draw Fractals by Hand: A Beginner's Guide](https://nnart.org/how-to-draw-fractals-by-hand-a-beginners-guide/)
[^4]: [Complete List of Books by Benoit Mandelbrot](https://nnart.org/complete-list-of-books-by-benoit-mandelbrot/)
[^5]: [How Are Fractals Used in Technology and Engineering?](https://nnart.org/how-are-fractals-used-in-technology-and-engineering/)
[^6]: [Style Guide: How Did Jackson Pollock Paint?](https://nnart.org/style-guide-jackson-pollock/)
[^7]: [How Do Fractals Appear in Nature? 10 Outstanding Examples](https://nnart.org/fractals-in-nature/)
[^8]: [How Are Fractals Used in Technology and Engineering?](https://nnart.org/how-are-fractals-used-in-technology-and-engineering/)
