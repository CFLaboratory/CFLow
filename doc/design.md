# Design

`CFLow` is designed to solve fluid dynamics problems in complex geometries, running on traditional
CPU-based and modern accelerated architectures from individual workstation to supercomputer scale.

The design of `CFLow` is centred around several major components:
- [Simulation](#sim) is the main component that orchestrates initialising, running and finalising
  the analysis
- [Model](#mod) description of the problem to be solved numerically
- [Solver](#sol) advances the discretised problem
- [Mesh](#mesh) discretised represention of the space the problem is defined on
- [Boundary Conditions](#bc) sets the value of the solution at the domain boundaries
- [Initial Conditions](#ic) sets the initial value of the solution
- [Postprocessing/Analysis](#postproc) performs analyses of the solution

![Component diagram of CFLow](CFLow.png)

## Simulation {#sim}

The `Simulation` component is the main component that orchestrates initialising, running the
simulation to advance the solution of the Model problem and performing Postprocessing/Analysis I/O.

- `initialising` the `Simulation` sets up the `Mesh`, the `Model` and sets the `Initial Conditions`
- `running` the `Simulation` performs the outer loop (single step for steady problems), calling the
  `Solver` to advance at each step, and performing any `Postprocessing/Analysis` and I/O required
- `finalising` the `Simulation` performs any cleanup required, for example ensuring any outstanding
  I/O has completed and collating any logging data

## Model {#mod}

The `Model` component describes the problem to be solved numerically, specifying the `Field`s that
comprise the `Solution` which should satisfy (to some given tolerance) the `Model` equation.

- `querying` the `Model` specification returns the list of `Field`s it requires in the `Solution`
- `evaluating` the `Model` with a given `Solution` determines the residual of the equation, i.e.
  \f[
    f(\phi) = \frac{\partial\phi}{\partial t} - \nabla\cdot\Gamma\nabla\phi - S
  \f]

## Solver {#sol}

The `Solver` component solves the discretised problem, advancing it to the next step.

- `stepping` the `Solver` uses a dual/pseudo-timestepping method to march the `Model` to a
  steady-state `Solution` in pseudo-time (\f$\tau\f$)
  \f[
    \lim_{\tau\rightarrow\infty} \frac{d\phi}{d\tau} = -f(\phi) \rightarrow 0
  \f]
  this stepping continues until some user-specified tolerance is achieved

## Mesh {#mesh}

The `Mesh` component represents the discretisation of the space the `Model` is defined on.
It combines the `Topology` of the discretisation (how it is connected/indexed) with the `Geometry`
of how it occupies physical space.

## Boundary Conditions {#bc}

The `Boundary Conditions` component controls the solution at the domain boundaries.

- `evaluating` a `Boundary Condition` returns either the value or the gradient of the field on the
  boundary

## Initial Conditions {#ic}

The `Initial Conditions` component sets the initial value of the solution.

- `evaluating` an `Initial Condition` returns the value of a `Field` at a given location, this may
  be given as either a function or by reading a solution file (for instance to restart a simulation)

## Postprocessing/Analysis {#postproc}

The `Postprocessing/Analysis` component is responsible for performing analyses on the solution, for
instance evaluating some functional of interest.

- `analysing` a `Solution` applies the specified analyses, returning their results
