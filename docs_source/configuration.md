# Model configuration
SaDS has an extensive list of input parameters and options to configure your model runs. The table below lists the parameters, default values, and some notes about changing their values.


**Tunable parameters**

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
