#### Example: Height of water in a cylindrical tank

__Problem__: Derive an expression which describes how the height $$h$$ of water in a cylindrical tank of radius $$R$$ changes as a function of time. Assume the tank has two inputs, and a single output (numbered 1,2 and 3, respectively). Let $$\rho$$ denote the density of water and $$\dot{m}_{3}\simeq ch^{1/2}$$.

__Solution:__
The total mass balance is given by:

$$
\sum_{s~=~1}^{\mathcal{S}}v_{s}\dot{m}_{s} + \dot{m}_{gen} = \dot{m}_{acc}
$$

There is no mass generation term for the __total mass__ balance thus $$\dot{m}_{gen}=0$$. Expanding the derivative of the accumulation term gives:

$$
\dot{m}_{acc} = \frac{dm}{dt} = \frac{d}{dt}\left(\rho V\right)
$$

Thus, we can rewrite the general balance equation (expanding out the summation, and the derivative) as:

$$
\rho\frac{dV}{dt} =  \dot{m}_{1} + \dot{m}_{2} - \dot{m}_{3} - V\frac{d\rho}{dt}
$$

We know the density of water is not changing with time which implies:

$$
V d\rho/dt = 0
$$

and we know the volume of a cylindrical tank is given by:

$$
V = \pi R^{2} h
$$

thus:

$$
\left(\rho \pi R^{2}\right)\frac{dh}{dt} = \dot{m}_{1} + \dot{m}_{2} - ch^{1/2}
$$

Ordinary Differential Equation (ODE) whose solution $$h\left(t\right)$$ describes the height of water in the tank as a function of time. In general, we can not analytically solve the ODEs that we will encounter in this course. Instead we must approximate solution numerically.
