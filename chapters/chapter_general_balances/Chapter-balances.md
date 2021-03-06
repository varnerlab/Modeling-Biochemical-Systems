### Material and energy balances in biochemical systems

#### Introduction

As we have seen, the basic building block of any biomolecular process is a cell. Cells are biological agents which process nutrients into valuable products,
waste products and more cells. The chemical transformation of nutrients e.g., sugar to valuable products such as proteins or organic molecules uses a vast network of coupled chemical reactions collectively called metabolic~pathways. Cells differ in their size, shape, behavior and complexity. However, they all share the common thread of requiring nutrients to survive, and many of the
pathways that process nutrients are conserved from the simplest bacteria to the most complex cells in our bodies. We grow cells and use them to make products of interest in special chemical reactors called bioreactors. To understand how cells function in bioreactors, and ultimately how to manipulate them for societal benefit, we must first understand how to apply engineering principles such as conservation of mass and energy to biological systems. Toward this goal, we'll start by reviewing basic material balance concepts and use these concepts to write balance equations around extracellular nutrients (outside of the cell). Second, we'll begin to think about how cells process extracellular nutrients, and how to write material balances around cells in bioreactors.
___

#### Total macroscopic mass and mole balance equations.

![](/figs/chapter_1_images/Control-Volume.svg)

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
thus, the total mass generation term $$\dot{m}_{gen} = 0$$. Sometimes it is more convenient to work in mole based units especially when modeling processes with chemical reactions.  

Just like total mass balances, we can formulate a balance equation around the total number of moles in a process.
Total mole balances have the same four types of terms, input, output, accumulation and generation and take the form:

$$
\sum_{s = 1}^{\mathcal{S}}v_{s}\dot{n}_{s}+\dot{n}_{gen} = \dot{n}_{acc}
$$

where $$\dot{n}_{s}$$ denotes the rate of transport of total moles in stream $$s$$ (mol/time), $$\dot{n}_{gen}$$ denotes the rate of generation of total moles inside the control volume (mol/time),
and $$\dot{n}_{acc}$$ denotes the rate of accumulation of moles inside the process (mol/time), $$v_{s}$$ denotes our direction parameter.
However, unlike total mass balances, the generation term in total mole balances $$\dot{n}_{gen}\neq{0}$$ in most for reactive systems.
