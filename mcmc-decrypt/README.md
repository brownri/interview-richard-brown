Decrypting Messages with MCMC
=============================

You are given a passage of English text that has been encrypted by remapping each symbol to a (usually) different one. For example,

```
<space> → v
a → s
b → !
...
```

Thus a text like `a boy...` might be encrypted by `sv!op...`. Assume that each symbol is mapped to a unique symbol. The file **symbols.txt** gives the list of symbols, one per line (n.b. the second line is `<space>`). The file **message.txt** gives the encrypted message.

Decoding the message by brute force is impossible, since there are 53 symbols thus 53! permutations. Instead you will set up a Metropolis-Hastings Markov chain to find modes on the space of permutations.

We model English text, say _s<sub>1</sub>s<sub>2</sub>···s<sub>n</sub>_ where _s<sub>i</sub>_ are symbols, as a Markov chain, where a symbol given the previous symbol is independent of all past symbols:

_p(s<sub>1</sub>s<sub>2</sub>···s<sub>n</sub>) = p(s<sub>1</sub>)p(s<sub>2</sub>|s<sub>1</sub>)···p(s<sub>n</sub>|s<sub>n - 1</sub>)_

 1. First, you need to learn some statistics of the English language. In particular, download a large text, say [War and Peace](http://www.gutenberg.org/files/2600/2600-0.txt), from the web and estimate the distribution of unigrams and bigrams for the given set of symbols - i.e. probabilities p(s) and transition probabilities p(s|t). You may ignore the probability for the initial symbol when estimating the transition probabilities. Give formulas for the maximum likelihood estimate of these probabilities as functions of counts of numbers of occurrences of symbols and pairs of symbols. Compute and report these estimated probabilities in a table.

 2. The state of the system consists of the permutation among the symbols. Let _σ(s)_ be the symbol which symbol _s_ is encrypted as, e.g. _σ(a) = s_ and _σ(b) = !_ above. We assume a uniform prior distribution over permutations. Are the latent variables _σ(s)_ for different symbols _s_ independent?

 3. Let _e<sub>1</sub>e<sub>2</sub>···e<sub>n</sub>_ be an encrypted English text. Write down the joint probability of _e<sub>1</sub>e<sub>2</sub>···e<sub>n</sub>_ and s<sub>1</sub>s<sub>2</sub>···s<sub>n</sub> given _σ_.

 4. We shall use a [Metropolis-Hastings](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm) (MH) sampler. The proposal is to pick two symbols and swap the symbols with which these two symbols are encrypted with. What are the proposal distributions and acceptance probabilities?

 5. Implement the MH sampler and run it on the included encrypted text.  Report the current decryption of the first 60 symbols after every 100 iterations. Your Markov chain should hopefully converge to give you a fairly sensible message.  (Hint:  it may help to initialize your chain intelligently and to try multiple times; if you do, please describe what you did).

 6. Is the chain mentioned above necessarily [ergodic](https://en.wikipedia.org/wiki/Ergodicity#Markov_chains)? If so, prove it; if not, explain and describe how you can fix it so that it is ergodic. Hint: some _p(s|t)_ values can be zero.
