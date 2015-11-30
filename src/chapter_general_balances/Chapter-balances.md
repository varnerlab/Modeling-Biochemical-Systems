### Material and energy balances in biochemical systems

__Review__: The basic building block of any biomolecular process is a cell.
Cells transformation nutrients e.g., sugar into valuable products such as proteins or organic molecules.
Cells differ in their size, shape, behavior and complexity. However, they all share the common thread of requiring nutrients to survive, and many of the
processes to utilize nutrients are conserved from the simplest bacteria to the most complex cells in our bodies.

__Objectives__: We grow cells in special chemical reactors called bioreactors. To understand how cells grow (and make products) in bioreactors,
we must first understand how to apply engineering principles such as conservation of mass and energy to biological systems.
In this chapter we will introduce:

1. Total macroscopic mass and mole balance equations
2. Species mass and mole balances equations
3. Energy balance governing the state of liquid in a bioreactor

#### Total macroscopic mass and mole balance equations.

![](./figs/Control-Volume.svg)

Consider an idealized control volume (Fig. \ref{fig-control-volume}).
The total macroscopic material balance around the control volume contains four terms, flow in, flow out, generation and accumulation:

$$
\sum_{s~=~1}^{\mathcal{S}}v_{s}\dot{m}_{s} + \dot{m}_{gen} = \dot{m}_{acc}
$$

where the summation term describes the net rate of material flow into and from the control volume. The term $$v_{s}$$ is a __direction parameter__.
We'll use the convention that streams *entering* the control volume have positive direction parameters ($$v_{s} = 1$$),
while streams exiting the control volume have negative direction parameters,
where $$\dot{m}_{s}$$ denotes the mass flow rate of stream s (typical units of kg/hr) and $$\mathcal{S}$$ denotes the total number of streams.
The term $$\dot{m}_{gen}$$ describes the rate of total mass generation inside the control volume, while the term $$\dot{m}_{acc}$$ describes the rate of total mass accumulation inside the control volume.
For biochemical processes, total mass is conserved (it is neither created or destroyed),
thus, the total mass generation term $$\dot{m}_{gen} = 0$$. This leaves the familiar in-out = change equation:

$$
\sum_{s~=~1}^{\mathcal{S}}v_{s}\dot{m}_{s} = \dot{m}_{acc}
$$

__Excercise__: Derive an expression that describes the height of water in a cylindrical tank as a function of time. [Solution](./tankexample.md).

Usually it is much more convenient to work in mole based units especially when modeling processes involving chemical reactions.  Just like total mass balances, we can write balances around the total number of moles in a process.
Total mole balances have the same four types of terms, input, output, accumulation and generation and take the form:

$$
\sum_{s = 1}^{\mathcal{S}}v_{s}\dot{n}_{s}+\dot{n}_{gen} = \dot{n}_{acc}
$$

where $$\dot{n}_{s}$$ denotes the rate of transport of total moles in stream $$s$$ (mol/time), $$\dot{n}_{gen}$$ denotes the rate of generation of total moles inside the control volume (mol/time),
and $$\dot{n}_{acc}$$ denotes the rate of accumulation of moles inside the process (mol/time), $$v_{s}$$ denotes our direction parameter.
However, unlike total mass balances, the generation term in total mole balances $$\dot{n}_{gen}\neq{0}$$ in most for reactive systems.
