# Model configuration
This page describes the configuration options available. These options are all specified in a simple structure (let's call it `params`).

## Specifying your domain and forcing
Specify melt rates (in m w.e./year) as function handles with a call signature `melt(t)`, as fields:

| Name | Size | Description |
| - | - | - |
| `ms` | `n_elements x 1` | Sheet melt rate |
| `mc` | `n_edges x 1` | Channel melt rate |
| `msc`| `n_edges x 1` | Sheet melt rate interpolated to edges, used to lower channel lips |

The mesh is specified as `params.dmesh`. The elevation is used to calculate initial conditions.

## Initial conditions
Initial conditions are specified in a structure `Y0` with fields

| Name | Size | Description |
| - | - | - |
| `hs` | `n_elements x 1` | Sheet water depth |
| `zs` | `n_elements x 1` | Sheet elevation |
| `hc` | `n_edges x 1` | Channel water depth |
| `Hc` | `n_edges x 1` | Channel incision depth (set >0 to avoid `NaN`) |
| `phic` | `n_edges x 1` | Channel potential |
| `Vm` | `n_moulins x 1` | Moulin storage |

The moulin storage (`Vm`) is just used to keep track of the total volume transferred through moulins, unlike in GlaDS where the englacial storage is an important part of the model formulation.

## Default values

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
| `r` | 3 | Ratio of channel width to incision depth | |
| `Hmin` | 1e-3 | Minimum incision depth before channel melts at same rate as sheet. | |
| `exchange_ratio` | 0.2 | Channel exchange ratio. | |

**Switches**

These options turn on and off features or switch between different methods.

| Name | Default Value | Other choices | Description | Notes |
| ---- | ------------- | ------------- | ----------- | ----- |
| `exchange` | `true`  | `false` | Choose whether to allow mass exchange between sheet and channels | |
| `model` | `coupled` | `sheet`, `channel` | Choose whether to run full (coupled) model, or sheet-only or channel-only. | |
| `Xi_s` | `true` | `false` | Heat dissipation in sheets. Set to 0 for no heat dissipation, 1 to allow dissipation. | |
| `overwrite` | `false` | `true` | Overwrite existing output files. If `false` and a file exists, append the time to the end of the filename. | |
| `stop_on_warning` | false | true | Switch to raise an error if parameter validation fails | |

**Solver parameters**

These options change the numerical ODE solver or control its behaviour.

| Name | Default Value | Description | Notes |
| ---- | ------------- | ----------- | ----- |
| `solver` | `odeRK` | Which ODE solver function to use. Could also be `ode45`, or any other Matlab solver. | `odeRK` runs the best. |
| `solver_opts` | | Options needed for solvers. For `odeRK`, this needs to have the timestep as field `dt` | |



**Output fields**

The model lets you choose which fields to save:

| Field | Description |
| ----- | ----------- |
| `dhsdt`  | Time derivative of water sheet thickness |
| `dhsdt_div` | Divergence term of water sheet thickness time derivative |
| `dhcdt`  | Time derivative of channel depth |
| `dhcdt_area`| Area-change component of channel depth rate of change |
| `dhcdt_div` | Divergence component of channel depth rate of change |
| `dHcdt`  | Time derivative of channel incision depth |
| `phis_x` | Sheet potential gradient x-component |
| `phis_y` | Sheet potential gradient y-component |
| `qx_sheet`  | Sheet flow in x-direction |
| `qy_sheet`  | Sheet flow in y-direction |
| `dphic_ds` | Channel potential slope |
| `qc` | Channel volume flow |
| `phic_node` | Potential on nodes |
| `Xi_c` | Potential energy dissipation |
| `exchange_frac` | Exchange fraction |
| `m_moulin` | Moulin input rates |
