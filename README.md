# WheelOS Simulation

Independent `wheelos_simulation` Bzlmod module. The Cyber simulation component,
MuJoCo/kinematic backends, vehicle models and fixtures retain their
`modules/simulation` paths. It depends on shared Core/Common/messages and
MuJoCo, not the Apollo product. Local Planning consumes its engine separately.

From `/apollo`, in the mapped-user managed development container:

```bash
python3 scripts/bzlmod.py dev build --config=cpu --config=opt @wheelos_simulation//modules/simulation:libsimulation_component.so
python3 scripts/bzlmod.py dev test --config=cpu --config=opt @wheelos_simulation//...
```

See [configuration and runtime contracts](modules/simulation/README.md).
Tests use declared runfiles for the packaged MuJoCo model. Starting a simulator
or operating hardware is not part of package migration validation.

Like `transform`, this ignored checkout must accompany the product changes.
Its Git source is registered in `wheelos.repos`; no Bzlmod registry release
has been published.
