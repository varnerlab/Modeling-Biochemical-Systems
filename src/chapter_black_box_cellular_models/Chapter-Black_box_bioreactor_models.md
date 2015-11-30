### Analysis of unstructured bioprocess models

#### Extracellular material balance equations
To analyze the behavior of cells in a bioreactor, we need to write material balances around nutrients, cells, metabolic products and the volume of media in the bioreactor.
For bioreactors we'll exclusively use mole-based units, however, other mass-based units systems can be found in the biochemical literature.
Let's begin writing our balances by expanding the generation term in the general mole-based species balance given in Eqn \eqref{eqn:general-species-mole-balance}:

$$
\dot{n}_{j,gen} = \left(\sum_{r}^{\mathcal{R}}\sigma_{jr}\hat{r}_{r}\right)V+\left(\sum_{k}^{\mathcal{T}}\tau_{j,k}q_{k}\right)XV
$$
We have two sets of reaction terms, the first describes $$\mathcal{R}$$ chemical reactions that can occur in the absence of cells (in the bulk fluid in the reactor), while the second
describes those $$\mathcal{T}$$ reactions that occur because of cells (cell-associated reactions). For bulk fluid phase reactions, $$\sigma_{jr}$$ denotes the stoichiometric coefficient governing species j in reaction r; if $$\sigma_{jr}<0$$ species j is *consumed* by reaction r, if $$\sigma_{jr}>0$$ species j is *produced* by reaction r and if $$\sigma_{jr}=0$$ species j is not connected with reaction r. The quantity $$\hat{r}_{r}$$ denotes the reaction rate per unit volume for reaction r (mmol/L-hr). Similarly, for the cell-associated reaction terms, $$\tau_{j,k}$$ denotes the stoichiometric coefficient describing how species j is connected with cell-associated reaction k. Reactions associated with cells have a unique unit system called specific~units which means we write all quantities per unit cell abundance (grams dry weight, or mmol of cells).
Thus, $$q_{k}$$, the kth cell-associated reaction rate, has units of mmol/mmol-hr or mmol/gdw-hr etc. Substituting our reaction terms into Eqn \eqref{eqn:general-species-mole-balance} gives:

$$
\frac{d}{dt}\left(C_{j}V\right) = \sum_{s}^{N}v_{s}F_{s}C_{j,s} + \left(\sum_{r}^{\mathcal{R}}\sigma_{jr}\hat{r}_{r}\right)V+\left(\sum_{k}^{\mathcal{T}}\tau_{j,k}q_{k}\right)XV \qquad j=1,2,...,\mathcal{M}
$$

where $$\mathcal{M}$$ denotes the number of metabolites, $$X$$ denotes the cellmass level in the reactor (gdw/L or mmol/L), and $$V$$ denotes the volume (L) of the reactor.
Similarly, the cellmass balance is given by:

$$
\frac{d}{dt}\left(XV\right) = \sum_{s}v_{s}F_{s}X_{s}+\left(\mu - k_{d}\right)XV
$$

where $$\mu$$ denotes the specific growth rate of cells, (hr$$^{-1}$$) and $$k_{d}$$ denotes the cell death constant (hr$$^{-1}$$).
Lastly, both the cellmass and metabolite balances involve the volume $$V$$ which is governed by:

$$
\frac{dV}{dt} = \sum_{s~=~1}^{\mathcal{S}}v_{s}\frac{\rho_{s}}{\rho}F_{s} - \frac{V}{\rho}\frac{d\rho}{dt}
$$

Putting all three types of equations together, expanding all derivatives and dividing both sides of the extracellular metabolite and cellmass balances by the volume gives:

$$
	\frac{dC_{j}}{dt} = \sum_{s~=~1}^{\mathcal{S}}v_{s}D_{s}C_{j,s} + \left(\sum_{r~=~1}^{\mathcal{R}}\sigma_{jr}\hat{r}_{r}\right) + \left(\sum_{k~=~1}^{\mathcal{T}}\tau_{j,k}q_{k}\right)X  - \frac{C_{j}}{V}\frac{dV}{dt}\qquad j=1,2,...,\mathcal{M}
$$
$$
	\frac{dX}{dt} = \sum_{s~=~1}^{\mathcal{S}}v_{s}D_{s}X_{s}+\left(\mu - k_{d}\right)X - \frac{X}{V}\frac{dV}{dt}
$$
$$
	\frac{dV}{dt} = \sum_{s~=~1}^{\mathcal{S}}v_{s}\frac{\rho_{s}}{\rho}F_{s} - \frac{V}{\rho}\frac{d\rho}{dt}
$$
where the quantity $$D_{s}$$,  called a dilution~rate (hr$$^{-1}$$), is given as:

$$
	D_{s} \equiv \frac{F_{s}}{V}\qquad s=1,2,...,\mathcal{S}
$$
The cellmass, metabolite and volume balances are a coupled system of $$\mathcal{M}+2$$ nonlinear ordinary differential equations, which depending upon the functional forms of the specific growth, death and uptake rates, has no analytic solution. However, these equations can be easily solved numerically using common algorithms included in packages and languages such as MATLAB or Python.
To see this, let's consider three special cases of the bioreactor balances, batch (no flow), fed-batch (flow in, no flow out) and continuous (flow in = flow out).


#### References
Karr et al (2012) A whole-cell computational model predicts phenotype from genotype. *Cell* __150__:389-401. [doi: 10.1016/j.cell.2012.05.044.](http://www.ncbi.nlm.nih.gov/pubmed/22817898)


[Karr:2012v]: http://www.ncbi.nlm.nih.gov/pubmed/22817898
