buildEnv
========

Create Environments

Usage
-----

    buildEnv(collate , parent = as.environment(2), name = NULL, .name = NULL)

| Argument | Description                                    |
| -------: | :--------------------------------------------- |
|  collate | a data.frame (see Details)                     |
|   parent | an environment                                 |
|     name | assigned to the return's name attribute        |
|    .name | assigned to the return's parent name attribute |

Value
-----

An environment named `name` containing the components indicated by `collate`.

Details
-------

Two environments are created: the return (an "outer" environment) and
its parent (an "inner" environment).

The `collate` data.frame must contain
`logical` values (without `NA` elements) in the first column ("Export") and
full paths to R code (each a `character` string) in the second column ("R code").

For each `FALSE` element in the Export column,
the corresponding R code is sourced into the _inner_ environment.
For each `TRUE` element in the Export column,
the corresponding R code is sourced into the _outer_ environment.

The inner environment will be named according to the `.name` argument.

The nest of environment is outer -> inner -> `parent`.

