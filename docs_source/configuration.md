# Model configuration
SaDS has an extensive list of input parameters and options to configure your model runs. The table below lists the parameters, default values, and some notes about changing their values. Parameters are changable as `params.Name`, where `Name` is the name given in the tables below.


**Tunable parameters**
These are physical parameters that you can tune to adjust the model's behaviour (in contrast to physical constants that should not be changed).

| Name | Default Value | Description | Notes |
| ---- | ------------- | ----------- | ----- |
| `alphac` | 5/3 | Channel flow exponent | |
| `betac`  | 3/2 | Channel flow exponent | |
| `kc` | 10 | Channel hydraulic conductivity | |
| `alphas` | 5/4 | Sheet flow exponent | |
| `betas`  | 3/2 | Sheet flow exponent | |
|`ks`      | 0.5 | Sheet hydraulic conductivity | |
| `lc` | 2 | Width of sheet contribution to channel melt | |
| `wc` | 0.1 | Width of channels | Can have size `n_edges x 1`. Only used if `width = constant`. |
| `r` | 5 | Ratio of channel width to incision depth | Only used if `width = ratio`. |
| `mf` | 0 | Channel melt factor | |
| `Hmin` | 1e-3 | Minimum incision depth before channel melts at same rate as sheet. | |

**Switches**
These options turn on and off features or switch between different methods.

| Name | Default Value | Other choices | Description | Notes |
| ---- | ------------- | ------------- | ----------- | ----- |
| `exchange` | `true`  | `false` | Choose whether to allow mass exchange between sheet and channels | |
| `model` | `coupled` | `sheet`, `channel` | Choose whether to run full (coupled) model, or sheet-only or channel-only. | |
| `advection` | `upwind` | `central` | Choose numerical flux scheme | `upwind` is strongly preferred and is much more stable. |
| `width` | `constant` | `ratio` | Choose whether channel width is constant or a ratio of incision depth | |
| `Xi_s` | 0 | 1 | Heat dissipation in sheets. Set to 0 for no heat dissipation, 1 to allow dissipation. | |

**Solver parameters**
These options change the numerical ODE solver or control its behaviour.

| Name | Default Value | Description | Notes |
| ---- | ------------- | ----------- | ----- |
| `solver` | `odeRK` | Which ODE solver function to use. Could also be `ode45`, or any other Matlab solver. | `odeRK` runs the best. |
| `opts` | `odeset` | Options to pass to the solver, e.g. `opts = odeset('RelTol', 1e-4)`. | |
| `tol` | 1e-1 | Numerical tolerance, see (???) | Always check the convergence! |

