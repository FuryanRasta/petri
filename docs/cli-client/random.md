# Random

Rand module allows you to post a random number request to the PETRI Hub and query the random numbers or the pending random number requests.

## Available Commands

| Name                                | Description                                                      |
| ----------------------------------- | ---------------------------------------------------------------- |
| [request](#petri-tx-random-request)  | Request a random number with an optional block interval          |
| [random](#petri-query-random-random) | Query the generated random number by the request id              |
| [queue](#petri-query-random-queue)   | Query the pending random number requests with an optional height |

## petri tx random request

Request a random number.

```bash
petri tx random request [flags]
```

**Flags:**

| Name, shorthand   | Type   | Required | Default | Description                                                                  |
| ----------------- | ------ | -------- | ------- | ---------------------------------------------------------------------------- |
| --block-interval  | uint64 | true     | 10      | The block interval after which the requested random number will be generated |
| --oracle          | bool   |          | false   | Whether to use the oracle method                                             |
| --service-fee-cap | string |          | ""      | Max service fee, required if "oracle" is true                                |

### Request a random number

Post a random number request to the PETRI Hub, the random number will be generated after `--block-interval` blocks.

```bash
# without oracle
petri tx random request --block-interval=100 --from=<key-name> --chain-id=petri --fees=0.3petri

# with oracle
petri tx random request --block-interval=100 --oracle=true --service-fee-cap=1petri --from=<key-name> --chain-id=petri --fees=0.3petri
```

:::tip
You will get a unique request id if the tx is committed, which can be used to query the status of the request. You can also [query the tx detail](./tx.md#petri-query-tx) to get the request id.
:::

## petri query random random

Query the generated random number by the request id.

```bash
petri query random random <request-id> [flags]
```

## petri query random queue

Query the pending random number requests with an optional block height.

```bash
petri query random queue <gen-height> [flags]
```

### Query random number request queue

Query the pending random number requests with an optional block height at which random numbers will be generated or request service.

```bash
petri query random queue 100000
```
