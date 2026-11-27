# tiny-stack-vm-loader

A 20-byte loader that runs a tiny stack VM from an entry secret. Built for make.fun's "Build a tiny stack virtual machine" bounty (22 November 2026, $100 in USDC).

## The code

`main.ts` — the whole loader, 20 bytes:

```ts
eval
(process.env.Q)
```

The entry secret is passed via the `Q` environment variable and evaluated as the VM program.

## How it works

- The make.fun Tiny Stack VM runs an entry program supplied as a secret.
- This loader reads that secret from `process.env.Q` and `eval`s it — nothing else. The 20-byte size is the point: the loader itself is minimal, the program lives entirely in the secret.

## Run it

Set `Q` to the entry secret, then run `main.ts` with any TypeScript runner (e.g. `tsx`, `ts-node`, or Deno):

```sh
Q='<entry secret>' npx tsx main.ts
```

## License

MIT — see [LICENSE](LICENSE).
