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
  * [Seeking Polynomial Roots ](#seeking-polynomial-roots-)
* [Fractal Generation Techniques](#fractal-generation-techniques)
  * [Escape-Time Fractals](#escape-time-fractals)
  * [Iterated Function Systems](#iterated-function-systems)
  * [Random Fractals](#random-fractals)
  * [Orbit Trap Method](#orbit-trap-method)
* [Refs](#refs)
  * [Docs](#docs)
  * [MiniLibX](#minilibx)
  * [Articles](#articles)
    * [Real Numbers ](#real-numbers-)
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
> $ax² + bx + c = 0;$
>
> **Quadratic Formula**
>
> $r_1,r_2 = \dfrac{-b ± \sqrt{b^2 - 4ac}}{2a}$

> [!Note]
>
> This formula is ubiquitously used to calculate light effects and general 3D manipulation during the production of games and animation movies.
>
> [Quadratic Formula](https://en.wikipedia.org/wiki/Quadratic_formula)
>
> - [3D GRAPHING QUADRATIC EQUATIONS WITH SIMULATION METHODOLOGY](https://www.globusjournal.com/wp-content/uploads/2020/03/GMIT-JD15-Rajeev.pdf)
> - [General Quadratic Equation in 3-D](https://www.maplesoft.com/support/help/maple/view.aspx?path=MathApps%2FGeneralQuadraticEquationIn3D)



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
