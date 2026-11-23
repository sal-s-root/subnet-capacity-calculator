# subnet-capacity-calculator

Calculate IPv4 address capacity with explicit provider reservations.

## Run

Python 3.8 or later; no third-party packages or cloud credentials are required.

```sh
python3 tool.py examples/input.json
cat examples/input.json | python3 tool.py -
python3 -m unittest -v
```

## Example

Input:

```json
{
  "cidr": "10.0.0.0/24",
  "reserved_addresses": 5
}
```

Result:

```json
{
  "network": "10.0.0.0/24",
  "total_addresses": 256,
  "allocatable_addresses": 251
}
```

The command writes JSON to standard output. Exit 0 means evaluation completed;
a finding in the output may still require attention. Invalid input returns exit 2,
with an error on standard error and no result on standard output.

## Operational scope

Reservation count is user supplied; point-to-point and provider-specific rules differ.

The tool evaluates supplied data locally. It does not change hosts, deploy
resources, or establish production compliance. Example identifiers and observations
are test fixtures. Keep credentials and private inventory out of Git.

## Design and verification

See [NOTES.md](NOTES.md) for the input contract, verification, and integration notes.
Related utilities: [network-throughput-estimator](https://github.com/sal-s-root/network-throughput-estimator), [http-access-log-summary](https://github.com/sal-s-root/http-access-log-summary).

## Project status

A small standalone learning exercise using supplied fixtures. The related
[infrastructure toolbox](https://github.com/sal-s-root/infra-toolbox) collects these
checks in one place.

The assigned historical dates form a retrospective learning schedule; this
exercise was created or reconstructed in 2026. See [history and scope](HISTORY.md).
