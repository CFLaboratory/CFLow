# Roadmap

The initial design for CFLow is to solve the (un)steady incompressible Navier-Stokes equations using
a dual-timstepping approach.
A roadmap to achieve this is outlined below:

- v0.1 Load a mesh
- v0.2 Solve the diffusion equation (steady)
- v0.3 Solve the advection-diffusion equation (steady)
- v0.4 Solve Stokes flow (steady, lid-driven cavity)
- v0.5 Solve Navier-Stokes flow (steady, lid-driven cavity)
- v1.0 Solve Navier-Stokes flow (unsteady, Taylor-Green vortex)

Following v1.0 optimisations such as hyperbolic diffusion, multigrid-accelerated dual-timestepping
and optimal pseudo timestepping schemes will be investigated.
