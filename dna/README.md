# Happ Developer Setup

This folder has an example DNA.

To change the code, you can work either opening VSCode inside the root folder of the repo or in this folder, you should have rust intellisense either way.

## Requirements

- Have [`holochain-run-dna`](https://www.npmjs.com/package/@holochain-open-dev/holochain-run-dna) installed globally.
- Having the holochain binaries installed.

## Building

```bash
CARGO_TARGET=target cargo build --release --target wasm32-unknown-unknown
dna-util -c todo_rename_dna.dna.workdir/
```

## Testing

After having built the DNA:

```bash
cd tests
npm install
npm test
```

## Running

After having built the DNA:

```bash
holochain-run-dna todo_rename_dna.dna.gz
```

Now `holochain` will be listening at port `8888`;

Restart the command if it fails (flaky holochain start).

## Adding a new zome

1. Copy the crate folder from one of the zomes.
2. Rename the folder to the name of the zome.
3. Rename the name of the crate in the `Cargo.toml` inside the crate.
4. Add the crate as a member of the `Cargo.toml` of this folder.
5. Add the zome in the `_.dna.workdir/dna.json` with the name of the zome.

Zome name convention: snake_case, plural (eg: `calendar_events`, `resource_bookings`).

## Adding a new DNA

1. Create a `dnas` folder on the root folder of the repository.
2. Copy and paste this `dna` folder for as many DNAs you want.
3. Change the `dna` folders name to new names that identifies each DNA.
