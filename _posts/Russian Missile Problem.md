# Russian missile problem - estimating how many Kh-101 cruise missiles Russia produced

Like the average layman, I began following Michael Kofman's Twitter account after Mr Putin decided we should not enjoy the first spring after COVID. Recently, he shared the meticulous [work by John Hardie](https://www.longwarjournal.org/archives/2022/12/estimating-russias-kh-101-production-capacity.php) compiling the serial numbers of downed Kh-101 cruise missiles and from there estimating Russia's production capacity. I'll leave the military experts to educate us why those missiles are a big deal, but as an economist I can say: I just spotted a German tank problem in the wild!

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Interesting look at estimating Kh-101s based on serial numbers and batches. A different approach than trying to guestimate max engine production capacity for missiles. <a href="https://t.co/Rblumiigud">https://t.co/Rblumiigud</a></p>&mdash; Michael Kofman (@KofmanMichael) <a href="https://twitter.com/KofmanMichael/status/1605555833282011136?ref_src=twsrc%5Etfw">December 21, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

That is, we can use a well-tested method of statistcal inference to estimate how many units have been produced in total just from the serial numbers of a much smaller sample. 




### Appendix: the 'reverse' German tank problem

In this instance, we want to estimte the population *minimum* from a sample of $k$ observations. Recall the standard German tank problem assumes the serial minimum to be 1 and it is the maximum that is unknown. Hence its 'reverse'.

The basic principle unsurprisingly is the same. Under the same assumptions, we begin by specifying the probability density function,

$$
Pr(M=m) = \frac{\binom{N-m-1}{k-1}}{\binom{N-R}{k}}
$$


where $N$ is the population maximum (which we know in this case) and $R$ the population minimum. $M$ is now the random variable for the sample minimum and $m$ the observed sample minimum. $m$ is defined over $[R,R+k]$.

To see why, the sample of $k$ values is drawn from integers from $R$ to $N$. So there are always 	$\binom{N-R}{k}$. 

The expected value can is therefore

$$
E(M) = \sum_{m=R}^{R+k} {m * Pr(M=m)} = \sum_{m=R}^{R+k} {m * \frac{\binom{N-m-1}{k-1}}{\binom{N-R}{k}}}
$$

There would be a tremendous amount of algebra involved if one is looking for a closed form solution (See [here](https://web.williams.edu/Mathematics/sjmiller/public_html/math/talks/GermanTankProblem_Talk_Hampshire2019.pdf) and a more general treatment [here](https://web.williams.edu/Mathematics/sjmiller/public_html/math/papers/GTPv10.pdf)). Finally we can substitute $E(M)$ for observed value sample minimum $m$, which is the closest we can get to $E(M)$ with our sample. We can then arrive at a closed form solution to $R$.