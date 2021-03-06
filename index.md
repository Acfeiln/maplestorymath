<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

First things first: this site is messy. It's basically an extended scratch journal. For now, it's for me to doodle as I learn GitHub Pages. Eventually, this will have a blog-like format with links to posts, but for now I'm just going to write something.

## 3 Line Epic is Cheaper?

### Preliminaries
A cube rolls a set of potential lines. Let $$p$$ be the probability that you roll some desired set of lines in one roll. Then the likelihood of getting these lines at least once in $$N$$ rolls is

$$
\qquad \displaystyle 1 - \left( 1 - p \right)^N
$$.

(If you're interested in the derivation, this is the [geometric distribution](https://en.wikipedia.org/wiki/Geometric_distribution)'s cumulative distribution function. The Wikipedia page also includes means, variances, and all other manner of stats 101 goodness.)

Suppose we want a failure rate of at most $$f$$, so that after $$N$$ rolls, the chance we *haven't* gotten our desired lines is $$\leq f$$. That is, we want

$$ 
\qquad \displaystyle \mathrm{Pr} \left( \geq 1 \text{ success in } N \right) = 1 - \left( 1 - p \right)^N \\
\qquad \displaystyle \phantom{\mathrm{Pr} \left( \geq 1 \text{ success in } N \right)} \geq 1 - f $$which gives

$$
\qquad \displaystyle N \geq \frac{\log f}{\log \left( 1 - p \right)}
$$.

**Note: this is NOT the minimum number of rolls required to get your lines.** That is always lower bounded by $$1$$---you can get arbitrarily lucky. Instead this is the minimum number of rolls you need for the *chances* of seeing your lines at least once to exceed $$1 - f$$. So for example if $$f = 0.1$$, we're talking about $$N$$ such that 

$$\qquad \displaystyle \mathrm{Pr} \left( \geq 1 \text{ success in } N \right) \geq 90 \%$$. 

**This is also NOT the expected number of rolls required to see your lines.** That would be $$\left \langle N \right \rangle = 1/p $$. We'll compare with looking at averages at the end.

### The Question
Could I ever benefit *more* by trying for *less* likely rolls with cheaper occult cubes in the epic tier, versus spending more on master or meister cubes for *more* likely unique/legendary lines?

Consider a CRA hat. A perfect 3 epic lines with just one primary gives +12% stat. A single primary unique line wouldn't do better, you'd need to roll at least 2, which would give +15% stat. Or, you could roll a single primary legendary line to do the exact same as the 3 line epic. **The question is: which is cheaper? Going for 3 lines on epic gear, or going for 2 on unique gear? Or even 1 line on legendary?**

### General Solution
Let $$p_1$$ be the likelihood of rolling a desired set of "1 tier" lines per cube type "1;" let $$ p_2 $$ be that of rolling a desired set of "2 tier" lines per cube type "2." We're setting ourself up to compare *any* two types of cubing, but one concrete example would be for "1" to mean rolling perfect epic lines on occult cubes and "2" for rolling 2 stat unique with master cubes.

Now, let $$c_1$$ be the cost per roll type "1" and $$c_2$$ be that per roll type "2."

Finally, let $$N_1$$ and $$N_2$$ be the minimum number of rolls you need to achieve a failure rate $$\leq f$$ on type "1" and "2" rolls, respectively.

The *total* cost of rolling until you have probability $$1 - f$$ of getting your "1 tier" lines with roll type "1" is $$ c_1 N_1$$, and for "2" it's $$ c_2 N_2$$. Define a ratio $$k$$:

$$
\qquad \displaystyle k \stackrel{.}{=} \frac{c_1 N_1}{c_2 N_2}
$$.

Plugging in what we worked out earlier,

$$
\qquad \displaystyle \boxed{ k = \frac{c_1 \log \left( 1 - p_2\right) }{c_2 \log \left( 1 - p_1\right)}}
$$.

**SO: when $$k \geq 1$$, it's worth rolling for type "2." Otherwise, it's likely cheaper to go for type "1."** Notice that "maximum desired failure rate" $$f$$ doesn't show up in the final formula at all---we got rid of it by considering only the *ratio* of costs. Thus the result applies for *any* failure rate: the goal is just to get your desired lines with equal chances. It will take more rolls for less likely outcomes (3-lines epic), but will cost more to use fancier cubes. 

### What About Averages?
Like I said earlier, I've avoided a formulation based on averages. But you don't have to! You'd get a sort of "average $$k$$," which I'll label $$\bar{k}$$, based on the expected number of rolls and fixed costs $$c_1$$ and $$c_2$$. You'd get

$$\qquad \displaystyle \bar{k} = \frac{c_1 p_2}{c_2 p_1}$$.

Quite a bit simpler! Why didn't I just do that?

Well, at root, because I didn't want the information the expected number of rolls tells me. It says: okay, you have infinitely many players, and each player is allowed to roll infinitely many times. Let 'em roll. Now, with these infinite statistics, take a weighted average of the number of rolls it took, and there's your number. I didn't want to work with that number, because no player has access to infinitely many attempts. That average includes not just a few but *infinitely many* sequence lengths that are *longer* than even the richest player could afford. 

I opted for something more direct: how many rolls before there's a 90% (or whatever %) chance you've gotten your lines. Since I only care *when to switch cubes*, rather than what the cost numbers are individually, my result turns out to be valid even in the 100% success limit. It is, to me, a more directly and usefully interpretable thing.

But what consequences did my approach have on $$k$$, compared to if I'd calculated $$\bar{k}$$? It turns out that (and you can show this with some calculus) whenever $$p_1 \leq p_2$$, $$k \geq \bar{k}$$ (with equality when $$p_1 = p_2$$). This means my approach has you switching over to unique/legendary *sooner* than the average approach---and this is true regardless of cubing costs. 

### Example: CRA Hat in Bera
Even more!
