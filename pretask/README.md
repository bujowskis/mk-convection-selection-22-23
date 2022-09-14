# Pretask
Collect data on relatively simple evolutionary algorithm runs with different `mutation rate` parameter. Plot the results. Draw conclusions.

# Results
*(all the plots can be found in subdirectories of `pretask`)*

## Best fitness
*[directory with plots of best individual](pretask/best)*

The main interest was in the fitness of the best individual over the whole span of the simulation. The results are as follows:

### 0
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-0.png" height="200"/>

- With no mutations occuring, the algorithm only **exploits**, with no **exploration**.
- Clearly visible, prolonged periods of stagnation with minimal or no improvement can be seen in between `500-8,000` and
`8,000-20,000` number of evaluations, which are followed by very high spikes, until the fitness value virtually peaks at around `1.22`.
- Without big enough exploration, the algorithm is highly prone to fall into local optima.
- I suspect, such (relatively) high fitness value comes from the simplistic nature of the problem the algorithm is applied to.
In complex enough problems, it would be impossible for the algorithm to reach results close to global optima, unless **by chance**
The initial population allows reaching it by exploiting, which is undesired.

### 0.05
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-005.png" height="200"/>

As compared to no mutations:
- The initial stagnation periods are shorter.
- The algorithm makes initial fitness gains faster.
- Although close, the algorithm doesn't reach as high fitness, topping at the same value for over `30,000` evaluations.
That indicates, though better, the exploit part still dominates exploration and the algorithm is struggling to move on past
the reached local optimum.
- However, at around `43,000`, the algorithm did manage to find a better solution, which is followed by further gains.
That indicates introducing mutation and exploration proved helpful, and given enough evaluations, the algorithm would likely
have found potentially better solution.

### 0.1
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-010.png" height="200"/>

- There is just one initial stagnation period, and it is even shorter than the ones before.
- The algorithm reaches just below `1.2` fitness in about half the time it took for no mutations to do so.
- However, given the same amount of evaluations, the algorithm fails to reach the `1.2` fitness and stagnates at around `1.16`.
That would indicate `0.1` mutation intensity may already be too much for the given task and computational resources.

### 0.2
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-020.png" height="200"/>

- The plot suggests about the same fitness gains as for `no mutations` one, although this one tops out and stagnates with
about the same fitness value as for `10,000` evaluations in `no mutations`.
- After topping out, the algorithm did not make any improvements given all the evaluations followed. That indicates mutation intensity
may already be big enough, leading to unsuccessful exploit, potentially in a form of lost genes of the local optimum found so far.

### 0.3
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-030.png" height="200"/>

- The similar situation as for `0.2` mutation intensity, though worse (tops out even before reaching `1.0`).
- Further proof the mutation intensity is already too big and the algorithm is too random.

### 0.4
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-040.png" height="200"/>

- (Just as `0.3` is to `0.2`, this one is to `0.3`)
- Further proof mutation intensity too big

### 0.5
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/best/plot-best-050.png" height="200"/>

- Big overkill
- Algorithm virtually instantly, randomly, finds the solution it nearly tops out at
- The algorithm seems virtually no better than random search

## (locally) Max fitness
Since all-time max fitness was not the only data we could access, I decided to also take a look and analyze locally max fitness.
That is, locally max fitness value which is not equal to all-time fitness, with the absence of elitism in the algorithm.

In fact, initially I've made these plots by accident, as I have forgotten we are after all-time max. But the brief look was enough
to prove me these plots ilustrated the algorithm's behavior, inner-workings and flaws even better. So much as it would be foolish
not to mention and analyze these.

### 0
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-0.png" height="200"/>

- There are virtually no oscillations up around `8,000` evaluations. Until that point, a quite steady growth can be observed.
- After that point, the plot displays relatively small oscillations in max fitness value.
- These plot features indicate and confirm the exploiting nature of the algorithm, given no mutations. It sticks to the
local optimum found and hardly explores further, making minimal improvements, most likely just nearing the true value of
that optimum.

### 0.05
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-005.png" height="200"/>

- The oscillations show up much quicker
- After initial gain to nearly `1.2` fitness at around `10,000` evaluations, the algorithm oscillates in a downward trend.
That may indicate the local optimum was left out in favor of exploration, even though it means locally worse fitness.
- After the biggest downward spike at around `29,000` evaluations, the fitness value starts oscillating in a steady upward trend.
That may indicate the exploration was worth it, new (potentially better) local optimum was found, and the algorithm
managed to exploit it, which proved to yield better result than the previous optimum.
- Given more evaluations, it looks like the algorithm may have done better than the no mutations approach.

### 0.1
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-010.png" height="200"/>

- The oscillations occur roughly as quick as in `0.05`, although are relatively bigger throughout the whole plot.
- There seem to be two significant downard dents (`18,000` and `42,000` evaluations) followed by upward trend.
This may indicate (and confirm) the algorithm was more likely to deviate from the two local optima found and explore.
- It should be noted with the oscillations being relatively so high, the algorithm may have left out the local optima too soon,
failing to exploit them enough.
- Even so, it still does not seem the algorithm is too random, and the general uptrend remains.

### 0.2
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-020.png" height="200"/>

- The oscillations have just 2 notable upward spikes (`11,000` and `32,000` evaluations), while having around 5 notable downward ones
(`13,000`, `18,000`, `26,000`, `29,000` and `43,000` evaluations).
- Overall, there does not seem to be a desired general uptrend in fitness - the max stays around `0.8` most of the time, with
the exception of rare upward spikes and more frequent downward ones.
- It seems the mutation intensity is already too high and the algorithm fails to exploit local optima well.
It clearly seems too random.

### 0.3, 0.4, 0.5
<div style="display: flex, direction: row">
  <img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-030.png" height="200"/>
  <img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-040.png" height="200"/>
  <img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/max/plot-max-050.png" height="200"/>
</div>

- The situation is similar to that of `0.2`, though worse
- Each bigger mutation intensity brings higher oscilations and lowered *"most frequent fitness"*
- The algorithm definitely works too random.

## Average fitness
The interesting results of `max fitness` analysis made me think and pay more attention to not only the exact thing we were after,
but also the other data. From all the data we had, I thought it would also be good to visualize the **average fitness**.

### 0
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/avg/plot-avg-0.png" height="200"/>

- There is a clear, general uptrend
- The oscillations are becoming bigger towards around `25,000` and then are becoming smaller. That would indicate that
initially diverse population is becoming much more similar and convergent towards a given local optimum
  - initial fitness increase with relatively small oscillations, suggesting some exploration may be happening from the initial
randomness
  - middle big oscillations, suggesting the one best optimum is forcing other individuals to converge towards it, even though
it may mean taking them away from their local optima
  - late smaller and smaller oscillations, indicating the population converged and may change minimally
- This clearly indicates the problem of too much exploit and not enough exploration.

### 0.05
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/avg/plot-avg-005.png" height="200"/>

- Besides the three notable downspikes (`13,000`, `24,000` and `28,000`**(!!!)**), there is a general upward trend.
- The oscillations are quite consistent, except the donwspikes.
- The above two properties may indicate the introduced mutations helped prevent the population from easy and quick falling into
the same local optimum, which given enough evaluations, have prooved to bring up average fitness above the peak one of no mutations
- In the end, oscillations got smaller, suggesting convergence

### 0.1
<img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/avg/plot-avg-010.png" height="200"/>

- The oscillations are quite consistent throughout the whole plot, with an exception of frequent spikes up and down
- In the end, oscillations got smaller, suggesting convergence (although not as high as in the previous cases)
- Different from the previous plots, the general uptrend is not as easily seen. However, the plot quite stongly supports
the biger tendency for algorithm to explore. It appears so, as if given more evaluations, the results may have surpassed that of the previous mutations intensities.

### 0.2, 0.3
<div style="display: flex, direction: row">
  <img src="pretask/avg/plot-avg-020.png" height="200"/>
  <img src="pretask/avg/plot-avg-030.png" height="200"/>
</div>

- The oscillations are more or less equally big throughout the plot since the initial increase in fitness.
- There does not seem to be a general uptrend, but rather the average fitness revolves around just `0.3` in case of `0.2` mutation intensity and `0.26` in case of `0.3` mutation intensity.
It seems the mutation intensity may be too much and the algorithm fails to exploit.

### 0.4, 0.5
<div style="display: flex, direction: row">
  <img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/avg/plot-avg-040.png" height="200"/>
  <img src="https://github.com/bujowskis/mk-convection-selection-22-23/tree/main/pretask/avg/plot-avg-050.png" height="200"/>
</div>

- Not only the oscillations are quite significant throughout the plot, but there are also frequent significant downward spikes in fitness
(in case of `0.5` mutation intensity, quite often)
- It is clear the mutation intensity is too high and the algorithm works way too random.

# Conclusions
Overall, there is a significant dislaimer to be made while considering the results of this experiment, namely **the simplistic nature of the problem solved**.

In such case of problems, the exploting approach tends to actually work quite well, outranking the exploring approach, which is being punished for its inherit more complex and resource-consuming nature.

Exploration-based approaches truly shine when solving more complex problems, where sole exploit fails.
I do believe, given more complex benchmarked problem, exploting approach would not have done so well, and the algorithm
with properly balanced (by altering `mutation intensity` and setting it higher than for this problem) exploit-exploration ratio would prove the best.

Another thing worth adding is that, even despite the specified interest of the experiment, it is worth looking into other kind of data (in this case, `avg` and `max`).
Although some parameters may initially be thought irrelevant or uninteresting, if it can be afforded, one should store and analyze other data.
In worst case scenario, the initial assumptions will be confirmed. But it may so happen, that **this** exact data proves to
be much more insightful, and we may have been after the wrong thing after all.
