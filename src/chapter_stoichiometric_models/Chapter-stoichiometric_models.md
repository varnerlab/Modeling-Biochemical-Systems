### Stoichiometric models of metabolic pathways

__Review__: Cells operate vast interconnected biochemical reaction networks which convert starting materials such as sugars into valuable products of interest, waste products and eventually more cells. We have already explored the kinetics of the special class of proteins (enzymes) that catalyze single transformations in these networks, now lets consider many enzymes interconnected together. As the number of enzymes becomes larger, the problem of
modeling metabolic networks becomes difficult.

__Objectives__: To explore the operation of metabolic networks, we must first write material balances around the reactants and products of each reaction in the network. Using these balances, we can then estimate the steady-state flow through the network using one of many possible techniques. Toward this objective, we will introduce:

1. General intracellular species balance equations
2. Metabolic flux balance analysis (MFA): a linear-algebra based approach to estimate flux through a metabolic network
3. Flux balance analysis (FBA): a linear programming technique to estimate flux through a metabolic network
4. Dynamic flux balance analysis (dFBA): a technique which allows time dependent modeling of metabolic networks
5. Regulatory flux balance analysis (rFBA): a technique to incorporate metabolic regulation and control into the estimation of metabolic flux

##### Intracellular species material balances
To derive the material balance governing the specific intracellular concentration of metabolite j, $$x_{j}$$ ([mmol/gdw]), in a metabolic network, we start from the general material balance:
$$
\dot{x}_{X,acc,j} = \dot{x}_{X,in,j} - \dot{x}_{X,out,j} + \dot{x}_{X,gen,j}\qquad{j=1,2,...,\mathcal{M}}
$$
where $$\mathcal{M}$$ denotes the number of metabolites and X denotes a specific cell from our population of cells. However, we have millions of cells in a bioreactor; we can't track metabolite levels in each individual cell. Instead, we make the well mixed assumption (WMA) for the cells in the reactor. The WMA for cells implies that the intracellular level of the metabolite $$x_{j}$$ does not vary between cells i.e., if we sample $$x_{j}$$ in many cells, the levels of $$x_{j}$$ would be the same to within measurement error. Second, WMA also implies that $$x_{j}$$ does not vary with position *inside* the cells. In reality, the WMA assumption for cells is incorrect; there are many interesting phenomena (both technological and human health related) that occur because of cellular diversity. Moreover, it is well known (especially in eukaroyotes) that the abundance of metabolites varies between the different cellular compartments. However, for now we'll make this assumption.

There are only two terms that we need to consider for intracellular balances, the accumulation and generation terms. This is because there is no *convective* transport into or from cells, i.e., cell walls block convective transport of $$x_{j}$$ into or from the cell. Thus, the transport terms vanish $$\dot{x}_{X,in,j} = \dot{x}_{X,out,j} = 0$$ and the intracellular material balance around metabolite $$x_{j}$$ becomes:
$$
\dot{x}_{X,acc,j} = \dot{x}_{X,gen,j}\qquad{j=1,2,...,\mathcal{M}}
$$
The well-mixed assumption simplifies the accumulation term to:
$$
\dot{x}_{X,acc,j} = \frac{d}{dt}\int_{X}x_{j}dX\simeq X\frac{dx_{j}}{dt} + x_{j}\frac{dX}{dt}
$$
while the generation term becomes:
$$
\dot{x}_{X,gen,j} = \int_{X}\left(\displaystyle\sum_{r}^{\mathcal{R}}\sigma_{jr}v_{r} + \displaystyle\sum_{k}^{\mathcal{T}}\tau_{jk}q_{k}\right)dX \simeq \left(\displaystyle\sum_{r}^{\mathcal{R}}\sigma_{jr}v_{r} + \displaystyle\sum_{k}^{\mathcal{T}}\tau_{jk}q_{k}\right)X
$$
We have split the reaction rates into those rates that occur completely within cells ($$v_{k}'s$$) and those that cross the cell boundary ($$q_{k}'s$$) where $$\sigma_{jr}$$ and $$\tau_{jk}$$ denote the stoichiometric coefficients.  These rates, called *metabolic fluxes*, have a special unit system called specific units. The most common example of specific units for fluxes is [mmol/gdw-hr], however other examples are possible [REF cmol system]. We know from our enzyme kinetics discussion that metabolic fluxes are complex functions of the concentration of the enzymes that catalyze the reactions, as well as substrates (starting materials) and sometimes even the products of other reactions.  Substituting the accumulation and generation terms into:

$$
\frac{dx_{j}}{dt} = \left(\displaystyle\sum_{r}^{\mathcal{R}}\sigma_{jr}v_{r} + \displaystyle\sum_{k}^{\mathcal{T}}\tau_{jk}q_{k}\right) - \frac{x_{j}}{X}\frac{dX}{dt}
\qquad{j=1,2,...,\mathcal{M}}
$$
The last term on the right-hand side of Eqn ?? is a dilution term.
This term accounts for the loss of $$x_{j}$$ because of the growth of the cellmass population.
The dilution term couples the intracellular metabolite balances to the extracellular cellmass balance in a bioreactor, and thus to the operation of the bioreactor.

##### How do we solve intracellular material balances?
We can solve intracellular material balance equations numerically using common software packages such as MATLAB, if we knew the functional form of the fluxes and values for the kinetic parameters which appear in the fluxes. However, the functional form of the fluxes or their associated parameter values are often difficult (sometimes impossible) to estimate. Two alternative strategies, metabolic flux analysis (MFA) and flux balance analysis (FBA), have been used to estimate the intracellular fluxes at or near an intracellular steady-state.

__Metabolic Flux Analysis (MFA)__: Metabolic flux analysis relies upon a pseudo steady-state assumption to reduce the intracellular material balance equations to algebraic equations given in matrix-vector form by:
$$
	\mathbf{S}\mathbf{v} + \mathbf{T}\mathbf{q} -\frac{1}{X}\frac{dX}{dt}\left(\mathbf{Ix}\right)\simeq\mathbf{0}
$$
The matrix $$\mathbf{S}$$ denotes the stoichiometric matrix ($$\mathcal{M}\times{\mathcal{R}}$$),
$$\mathbf{T}$$ denotes the transport (or exchange) matrix ($$\mathcal{M}\times{\mathcal{T}}$$) and the $$\mathbf{I}$$ denotes the ($$\mathcal{M}\times{\mathcal{M}}$$) identity matrix.
The steady-state material balances have two sets of unknowns, states (the x's) and the fluxes (v and q).
However, lets assume the dilution due to growth terms are small; thus, we drop these terms to arrive at:
$$
	\mathbf{S}\mathbf{v} + \mathbf{T}\mathbf{q} \simeq\mathbf{0}
$$
This is $$\mathcal{M}$$ algebraic equations in the unknown intracellular fluxes $$v_{1},...,v_{\mathcal{R}}$$ and transport fluxes $$q_{1},...,q_{\mathcal{T}}$$. Typically, $$\mathcal{M}<\mathcal{R}+\mathcal{T}$$ which means no *unique* flux solution can be found. However, we can potentially measure some of the transport fluxes that carry material into and from the cells. Let's denote the measured fluxes as $$\vartheta_{m}$$ ($$\mathcal{E}\times{1}$$ column vector), and all other fluxes as $$\vartheta_{u}$$ ($$\mathcal{U}\times{1}$$ column vector).
We can then redefine the stoichiometric balances as:
$$
	\mathbf{\Sigma}\vartheta_{u} + \mathbf{\Phi}\vartheta_{m} \simeq\mathbf{0}
$$
where $$\mathbf{\Phi}$$ contains the columns corresponding to the measured fluxes ($$\mathcal{M}\times\mathcal{E}$$), and $$\mathbf{\Sigma}$$ contains the columns corresponding to unmeasured fluxes ($$\mathcal{M}\times\mathcal{U}$$).
The material balances can now be solved for the unmeasured fluxes $$\vartheta_{u}$$ using linear algebra:
$$
	\vartheta_{u}\simeq-\mathbf{\Sigma}^{\#}\mathbf{\Phi}\vartheta_{m}
$$
The matrix $$\mathbf{\Sigma}^{\#}$$ is a $$\mathcal{U}\times\mathcal{M}$$ *generalized* inverse of the stoichiometric matrix corresponding to the unmeasured fluxes. The form of $$\mathbf{\Sigma}^{\#}$$ depends
upon the shape and the rank of $$\mathbf{\Sigma}$$. The definition of the $$\mathbf{\Sigma}$$ and $$\mathbf{\Phi}$$ arrays influences our ability to solve the intracellular material balances. The structure of these arrays is controlled by which fluxes are measured. Measurement selection is influenced by technical concerns regarding the measurement technology, the cost of measurements as well as the time required to make measurements.

* $$\mathcal{M}>\mathcal{U}$$: __Overdetermined system of equations__:
Overdetermined systems are characterized by more equations than unknowns and have no single regular solution, in other
words, no single solution will simultaneously satisfy all the equations. The problem of determining the solution to an overdetermined
system can be recast as a least-squares problem of the form:
$$
\min_{\mathbf{\vartheta_{u}}}\bigl(\mathbf{\Sigma\vartheta_{u}}-\mathbf{b}\bigr)^{T}\bigl(\mathbf{\Sigma\vartheta_{u}}-\mathbf{b}\bigr)
$$
where
$$
\mathbf{b}\equiv-\mathbf{\Phi\vartheta_{m}}\left(t\right)
$$
Equation ?? can be analytically solved by standard calculus to yield the solution:
$$
\mathbf{\vartheta_{u}}=\left(\mathbf{\Sigma^{T}\Sigma}\right)^{-1}\mathbf{\Sigma^{T}b}
$$
In this case the quantity $\mathbf{\Sigma}^{\#}$ is given by:
$$
\mathbf{\Sigma}^{\#} = \mathbf{\Sigma^{L}}\equiv\left(\mathbf{\Sigma^{T}\Sigma}\right)^{-1}\mathbf{\Sigma^{T}}
$$
denotes a left inverse (sometimes called the Moore-Penrose inverse, generalized inverse or pseudo inverse). For the least-squares solution Equation
\eqref{eq-right} to exist, the condition
$$
\det\mathbf{\Sigma^{T}\Sigma}\neq{0}
$$ must be satisfied.

* $$\mathcal{M}<\mathcal{U}$$: __Underdetermined system of equations__:
Underdetermined systems are characterized by an $$\infty$$-solutions as $$n$$ unknowns can be written in terms of the remaining $$m-n$$
unknowns which in the general case take on arbitrary values. The solution of an underdetermined system of LAEs can be posed
as a constrained least-squares minimization problem of the form:
$$
\min_{\mathbf{u}}\frac{1}{2}\mathbf{\vartheta_{u}}^{T}\mathbf{\vartheta_{u}}
$$
subject to:
$$
\mathbf{\Sigma\vartheta_{u}}=\mathbf{b}
$$
where
$$
\mathbf{b}\equiv-\mathbf{\Phi\vartheta_{m}}\left(t\right)
$$
Problem ?? has been solved analytically using standard techniques from calculus to yield the solution:
$$
\mathbf{\vartheta_{u}}=\mathbf{\Sigma}^{T}\left(\mathbf{\Sigma\Sigma}^{T}\right)^{-1}\mathbf{b}
$$
The quantity
$$
\mathbf{\Sigma}^{\#} = \mathbf{\Sigma^{R}}\equiv\mathbf{\Sigma^{T}}\left(\mathbf{\Sigma\Sigma^{T}}\right)^{-1}
$$
denotes a right inverse. For the least-squares solution to exist, the condition
$$
\det\mathbf{\Sigma\Sigma^{T}}\neq{0}
$$
must be satisfied.

* $$\mathcal{M}=\mathcal{U}$$: __Square systems__:
When the number of equations equals the number of unknowns the system is said to be \emph{square}. Square systems can be
solved by several different techniques, including directly determining the matrix inverse $$\mathbf{S}^{-1}$$, i.e.,
$$
\mathbf{\vartheta_{u}}=-\mathbf{\Sigma}^{-1}\mathbf{\Phi\vartheta_{m}}\left(t\right)
$$
Solution ?? exists as along as:
$$
\det\left(\mathbf{\Sigma}\right)\neq{0}
$$
The direct computation of the inverse for square systems is \emph{very} computationally expensive, so in practice
other techniques, such as Gauss Elimination, Gauss Jordan Elimination or iterative techniques are used to calculate the flux
vector $$\mathbf{\vartheta_{u}}$$.

##### MFA Examples:
* [Estimate the flux through a simple metabolic network for different measurement choices using MFA](./SimpleMFAExample.md).

__Flux Balance Analysis (FBA)__: Flux balance analysis (FBA) is another strategy to estimate intracellular fluxes.
FBA was developed by Palsson and coworkers to estimate fluxes of genome scale models of *E. coli* [(Edwards and Palsson, 2000)][Edwards2000]. The FBA problem recasts the estimation of intracellular fluxes as a Linear Programming (LP) problem.  Linear programming is a type of convex optimization problem in which a linear objective function is maximized (or minimized) subject to linear algebraic constraints.
LPs can be solved easily for genome scale problems with thousands of unknown fluxes on standard hardware using packages such as MATLAB in a few seconds. Mathematically, FBA is less restrictive than MFA, and is not as directly tied to measurement selection as MFA.

#### References
Edwards J, and B.O Palsson (2000) The Escherichia coli MG1655 in silico metabolic genotype: its definition, characteristics, and capabilities. Proc Natl Acad Sci U S A. __97__:5528-33. [doi: 10.1073/pnas.97.10.5528](http://www.ncbi.nlm.nih.gov/pubmed/10805808)

[Edwards2000]: http://www.ncbi.nlm.nih.gov/pubmed/10805808
