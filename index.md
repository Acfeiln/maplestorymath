<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> $$\require{braket}$$

First things first: this site is messy. It's basically an extended scratch journal. For now, it's for me to doodle as I learn GitHub Pages. Eventually, this will have a blog-like format with links to posts, but for now I'm just going to write something.

Bra-ket tests: $$\bra{a} \ket{a} \braket{a} \set{a} \Bra{a} \Ket{a} \Braket{a} \Set{a} \ketbra{a}{a}$$

## 3 Line Epic is Cheaper?

### Prerequisites
A cube rolls a set of potential lines. Let $$p$$ be the probability that you roll some desired set of lines in one roll. Then the probability of getting these lines at least once in $$N$$ rolls is

$$
\qquad \displaystyle 1 - \left( 1 - p \right)^N
$$.

(If you're interested in the derivation, this is the geometric distribution's cumulative distribution function. The Wikipedia page also includes means, variances, and all other manner of stats 101 goodness. I'll take a slightly different approach, mostly for fun.)

Suppose we want a failure rate of at most $$f$$, so that after $$N$$ rolls, the chance we *haven't* gotten our desired lines is $$\leq f$$. Then at minimum we need to roll $$N$$ times such that

$$
\qquad \displaystyle 1 - \left( 1 - p \right)^N = 1 - f
$$,

giving

$$
\qquad \displaystyle N = \frac{\log f}{\log \left( 1 - p \right)}
$$.

**Note: this is NOT the minimum number of rolls required to get your lines.** That is always lower bounded by $$1$$---you can get arbitrarily lucky. Instead this is the minimum number of rolls you need for the *chances* of seeing your lines at least once to exceed $$1 - f$$. So for example if $$f = 0.1$$, we're talking about $$N$$ such that

$$\qquad \displaystyle \mathrm{Pr} \left( \text{desired lines at least once in } N \text{ rolls} \right) = 90 \%$$. 

**This is also NOT the expected number of rolls required to see your lines.** That would be $$\braket{N} = 1/p $$---something big, and also something biased by the boundless possibility to fail. The geometric distribution is asymmetrical, and nobody can actually realize $$N \to \infty$$ rolls, so I'll only bring the expected values back in at the end for comparison and some interpretation. Nevertheless, good to know the asymptotics are there if you want them.

### The Question
I want to ask: could I ever benefit *more* by trying for *less* likely rolls with cheaper occult cubes in the epic tier, versus spending more on master or meister cubes for *more* likely unique/legendary lines?

As a concrete example, consider a CRA hat. A perfect 3 epic lines with just one primary gives +12% stat. You could in principle transfer hammer this potential from lower-level equipment, saving an order of magnitude on reveal costs (though I won't factor that in here). A single primary unique line wouldn't do better, you'd need to roll at least 2, which would give +15% stat. Or, you could roll a single primary legendary line to do the exact same as the 3 line epic. **The question is: what is cheaper, in terms of only cube costs? Going for 3 lines on epic gear, or going for 2 on unique gear? Or even 1 line on legendary?**

### General Solution
Let $$p_\text{o}$$ be the probability of rolling a desired set of epic lines per occult cube, and $$p_\text{m}$$ that of rolling a desired set of unique or legendary (as applicable) lines using a master or meister (or other) cube. I assume your item is *already* at the desired tier; I'm not including anything to do with rank-up chances for now. Similarly, let $$c_\text{o}$$ be the cost (in mesos) per occult cube, and $$c_\text{m}$$ be that for whichever fancier cube you wish to compare. Finally, let $$N_\text{o}$$ and $$N_\text{m}$$ be the minimum number of rolls you need to achieve a failure rate $$\leq f$$ on your occult and fancier rolls, respectively. (Remember, this is 

The *total* cost of rolling until you have probability $$1 - f$$ of getting your epic lines with occult cubes is $$ c_\text{o} N_\text{o}$$, and for the fancier ones it's $$ c_\text{m} N_\text{m}$$. Let's define a ratio $$k$$:

$$
\qquad \displaystyle k \stackrel{.}{=} \frac{c_\text{o} N_\text{o}}{c_\text{m} N_\text{m}}
$$.

Plugging in what we worked out earlier,

$$
\boxed{ \qquad \displaystyle k = \frac{c_\text{o} \log \left( 1 - p_\text{m}\right) }{c_\text{m} \log \left( 1 - p_\text{o}\right)}}
$$.

**SO: when $$k \geq 1$$, it's worth rolling the fancier cubes. Otherwise, it'll cost less "on average" (not actually taken on average) to go for more lines on occult cubes.** Notice that "maximum desired failure rate" $$f$$ doesn't show up in the final formula at all---we got rid of it by considering only the *ratio* of costs. Thus the result applies for *any* failure rate: the goal is just to get your desired lines with equal chances. It will take more rolls for less likely outcomes (3-lines epic), but will cost more to use fancier cubes. 

**And, just another note that I have *not* calculated any expected values.** These are instead based on having a fixed failure rate: if $$k < 1$$, it costs more to roll to a 95% chance (or any other chance you like) of seeing your desired epic lines than to a 95% chance of seeing your desired unique/etc. lines.

### Example: CRA Hat in Bera
Before actually crunching some numbers, we should take another quick look at our result for $$k$$. Notice the ratio of *costs* appears on its own, while the ratios of probabilities are obscured behind logarithms. This should prime us to expect cost per cube to matter *more* than chances of success between the different cubes. In Bera:
