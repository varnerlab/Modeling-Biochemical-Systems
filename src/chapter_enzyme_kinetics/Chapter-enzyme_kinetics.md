#### Models for enzyme catalyzed biochemical reactions

__Review__: Enzymes are proteins that catalyze the chemical reactions occurring inside simple and complex cells.
Enzymes are responsible for processing starting materials such as sugars into products of interest, waste products and eventually more cells.
Enzymes are also responsible for information processing, and biophysical functions such as transporting molecules across membranes.
Enzymes can be classified in one of six classes, based on the chemical reactions they catalyze.
Just like other types of catalysts, enzyme do *not* change the overall energetics of a chemical reaction, rather they lower the activation
barrier for the reaction to occur.

__Objectives__: In this chapter, we'll develop models describing the kinetics enzymes catalyzed reactions with and without inhibitors, and other regulatory molecules.
Toward this objective, we will introduce:

1. Idealized models of enzyme kinetics
2. Simple models of enzyme inhibitors
3. Allosteric models of enzyme regulation

#### Idealized models of enzyme kinetics
In general, modeling the kinetics (rate) of enzyme catalyzed reactions, for example the rate of starch degradation by $$\alpha$$-amylase, is a difficult problem.
However, we can gain insight into this difficult problem, and the general arguments of how to formulate the problem, by studying a simple idealized example.
Let's assume we have a well mixed test tube containing an enzyme $$E$$ (a protein that catalyzes chemical reactions) which converts substrate $$S$$ (the starting compound)
into product $$P$$. The kinetics of each elementary step can be written using mass-action kinetics, i.e.,

$$
	r_{1} = k_{1}\left[E\right]\left[S\right] \;
$$
$$
	r_{2} = k_{2}\left[E:S\right] \;
$$
$$
	r_{3} = k_{3}\left[E:S\right]\;
$$

where $$\left[\cdot\right]$$ denotes a species concentration, and $$k_{j}$$ denotes the rate constant governing the $$jth$$ elementary reaction.
The rate $$r_{1}$$ describes the *association* rate between the enzyme and substrate, $$r_{2}$$ describes the rate of dissociation of the enzyme substrate complex and $$r_{3}$$ denotes the rate of *chemical~conversion* of the bound substrate into product (where we assume the dissociation of the product from the enzyme is fast). Lastly, enzyme concentration must obey the relationship:
$$
	\left[E_{T}\right] = \left[E\right] + \left[E:S\right]
$$where $$\left[E_{T}\right]$$ denotes the total enzyme concentration in the tube, $$\left[E\right]$$ denotes the *free*
enzyme concentration (not bound to substrate) while $$\left[E:S\right]$$ denotes the enzyme substrate complex.

In order to estimate the *overall* rate of enzymatic conversion ($$v$$) of $$S$$ to $$P$$, we need to stipulate a single rate limiting step out of the set of elementary reactions describing the conversion.
Let's assume that the rate of chemical conversion ($$r_{3}$$) is the *slowest* step, i.e., the substrate bounces on/off the enzyme quickly with only a fraction of these binding events resulting in a successful chemical transformation. Thus, the overall rate of S to P is then given by:
$$
	v = k_{3}\left[E:S\right]
$$
Let's also assume that we already know (or can estimate) the rate constants $$k_{1},k_{2}$$ and $$k_{3}$$. When this is true, the only unknown in
Eqn. \eqref{eqn:overall-rate-start-simple} is $$\left[E:S\right]$$.
However, we can relate $$\left[E:S\right]$$ to variables we know ($$E_{T}$$ and at least initially $$S$$) through the enzyme balance,
and a second assumption called the *pseudo-steady-state~assumption* for the reaction intermediate
$$\left[E:S\right]$$:
$$
	\frac{d\left[E:S\right]}{dt} = k_{1}\left[E\right]\left[S\right] - k_{2}\left[E:S\right] - k_{3}\left[E:S\right]\simeq{0}
$$
Rearranging Eqn. \eqref{eqn:pssa-simple} and solving for $$\left[E:S\right]$$ gives the relationship:
$$
	\left[E:S\right]\simeq\frac{k_{1}}{k_{2}+k_{3}}\left[E\right]\left[S\right]
$$where the ratio of rate constants is defined as the Michaelis Menten saturation coefficient or $$K_{M}$$:
$$
	\frac{1}{K_{M}}\equiv\frac{k_{1}}{k_{2}+k_{3}}
$$
Substituting Eqn. \eqref{eqn:es-simple} into the overall rate yields:
$$
	v = k_{3}\frac{\left[E\right]\left[S\right]}{K_{M}}
$$
However, in $$v$$ we still do not know $$\left[E\right]$$, the free enzyme concentration. To get $$\left[E\right]$$ we have to use the total enzyme balance.
Substituting Eqn. \eqref{eqn:es-simple} into the enzyme balance Eqn. \eqref{eqn:total-enzyme-balance-simple} and solving for $$\left[E\right]$$ yields:
$$
	\left[E\right] = \frac{\left[E_T\right]K_{M}}{K_{M}+\left[S\right]}
$$Lastly, we can substitute Eqn. \eqref{eqn:eqn-finally-simple} into Eqn. \eqref{eqn:final-v-simple} to arrive at the final expression for $$v$$:
$$
	v = V_{max}\frac{\left[S\right]}{K_{M}+\left[S\right]}
$$
where $$V_{max}\equiv{k_{3}}\left[E_{T}\right]$$. Michaelis Menten kinetics are a type of saturation kinetics where the change in the reaction rate as a function of substrate concentration
saturates (slows down) as we increase substrate beyond a critical limiting value (Fig. \ref{fig-mm-plot}).  Similar to Monod growth kinetics, when $$S\gg{K}_{M}$$ the rate becomes close to $$V_{max}$$. Conversely,
when $$S\ll{K}_{M}$$ the rate appears to be linear with respect to substrate concentration.
Lastly, it is easy to show that when $$K_{M}\simeq S$$ the reaction rate equals $$v\simeq 1/2V_{max}$$.

__How do we estimate $$V_{max}$$ and $$K_{M}$$ from data__?
There is no general first-principles methodology to estimate $$V_{max}$$ and $$K_{M}$$ for an arbitrary enzyme catalyzed reaction.
Thus, we must estimate these parameters from experimental measurements.
For the simple reactions we have derived we can make a *Lineweaver-Burk* plot (LBP) \citep{LWBPlot}.
LBPs are a double reciprocal plot that allows us to estimate *both* the $$K_{M}$$ and the $$V_{max}$$ of
an enzyme substrate pair. Suppose we could measure the overall rate of reaction for a given substrate level.
If we invert Eqn. \eqref{eqn:mmequation-simple} and collect terms we arrive at:
$$
	\frac{1}{v} = \frac{K_{M}}{V_{max}}\frac{1}{S} + \frac{1}{V_{max}}
$$
Eqn. \eqref{eqn:inverse-rate} is a *linear* equation; if we let $$1/v$$ equal the dependent variable (y-axis), and $$1/S$$ equal the independent variable (x-axis),
then $$1/V_{max}$$ is the y-intercept and
$$K_{M}/V_{max}$$ equals the slope (Fig \ref{fig-lwb-plot}).
