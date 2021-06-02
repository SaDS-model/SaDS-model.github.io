# Startup guide
This guide will take you through downloading the model's code and getting set up to run the model. Once you get through this section you should have everything you need to follow along with the [tutorial](tutorial.md).

## Requirements
The model is written in MATLAB so you will need a license. If you are in Applied Mathematics, you can get a license from the department by emailing the AM Grad email (this is true as of June 2021). Otherwise, Christine can purchase a license for you.

You don't need to know much about MATLAB to run this model, and the analysis can be straightforward enough.

## Downloading and installing
The code is hosted on our GitHub group [here](https://github.com/uwglacier/SaDS). This means you will first need to become a member of the group. If you are not a member, ask Christine to add you.

Clone the code to a reasonable place (the code is small enough to work with locally, but can also be run on the Compute Canada (or other) servers):

```
git clone https://github.com/uwglacier/SaDS.git
```

You may have to follow the instructions in the Triangle package's README file (in the `mattri/triangle/` directory) to compile it for your system.

Edit the `set_paths.m` file in the root directory to match the packages you have and your file paths.

That should be all that you need to do!

## A note about the Compute Canada servers
This model is very easy to run on the compute canada severs. All you need to do is `module load StdEnv/2020` and `module load matlab/2020b` (or your preferred version).

Now is a good time to go through the [tutorial](tutorial.md) to make sure everything works.
