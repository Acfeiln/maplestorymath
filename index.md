<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

First things first: this site is messy. It is basically an extended scratch journal. For now, it is for me to doodle as I learn GitHub Pages. Eventually, this will have a blog-like format with links to posts, but for now I'm just going to write something.

## Cubing rates and costs.
A cube rolls a set of potential lines. Let $$p$$ be the probability that you roll some desired set of lines in one roll. Then the probability of getting these lines at least once in $$N$$ rolls is

$$
\qquad \displaystyle 1 - \left( 1 - p \right)^N
$$.

(At some point, I'll put a link to a derivation here.)

Suppose we want a failure rate of at most $$f$$, so that after $$N$$ rolls chances we haven't gotten our desired lines is $$\leq f$$. Then at minimum we need to roll $$N$$ times such that

$$
\qquad \displaystyle 1 - \left( 1 - p \right)^N = 1 - f
$$,

giving

$$
\qquad \displaystyle N = \frac{\log f}{\log \left( 1 - p \right)}
$$.

Now, I want to ask: could it ever be *more* worth it to try for something *less* likely on cheaper occult cubes in the epic tier, versus spending more to use master or meister cubes for potentially more likely lines on unique or legendary tier?

Let's take a concrete example: a CRA hat. A perfect 3 epic lines with just one primary gives +12% stat. You could in principle transfer hammer this potential from lower-level equipment, saving an order of magnitude on potential reveal costs (though I won't factor that in right now). A single primary unique line wouldn't do better, you'd need to roll at least 2, which would give +15% stat. **The question is: what is cheaper, in terms of only cube costs? Going for 3 lines on epic gear, or going for 2 on unique gear?** Let's investigate.

Let $$p_\text{o}$$ be the probability of rolling a desired set of epic lines per occult cube, and $$p_\text{m}$$ be the probability of rolling a desired set of unique or legendary (as applicable) lines using a master or meister (or other) cube. I assume your item is *already* at the desired tier for this; I'm not including anything to do with rank-up probabilities for now. Similarly, let $$c_\text{o}$$ be the cost (in mesos) per occult cube, and $$c_\text{m}$$ be that for whichever fancier cube you wish to compare; and let $$N_\text{o}$$ and $$N_\text{m}$$ be the minimum number of rolls you need to achieve a failure rate $$\leq f$$ on your occult and fancier rolls, respectively.

Then the *total* cost of rolling until you have probability $$1 - f$$ of getting your epic lines with occult cubes is $$ c_\text{o} N_\text{o}$$, and for the fancier ones $$ c_\text{m} N_\text{m}$$. Let's define a ratio $$k$$:

$$
\qquad \displaystyle k \stackrel{.}{=} \frac{c_\text{o} N_\text{o}}{c_\text{m} N_\text{m}}
$$.

Plugging in what we worked out earlier,

$$
\qquad \displaystyle k = \frac{c_\text{o} \log \left( 1 - p_\text{m}\right) }{c_\text{m} \log \left( 1 - p_\text{o}\right)}
$$.

**When $$k \geq 1$$, it's worth rolling the fancier cubes. Otherwise, it'll cost less to go for a less likely line set on cheaper occult cubes.**
