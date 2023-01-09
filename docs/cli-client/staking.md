# Staking

Staking module provides a set of subcommands to query staking state and send staking transactions.

## Available Commands

| Name                                                                         | Description                                                                                   |
| ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [validator](#petri-query-staking-validator)                                   | Query a validator                                                                             |
| [validators](#petri-query-staking-validators)                                 | Query for all validators                                                                      |
| [delegation](#petri-query-staking-delegation)                                 | Query a delegation based on address and validator address                                     |
| [delegations](#petri-query-staking-delegations)                               | Query all delegations made from one delegator                                                 |
| [delegations-to](#petri-query-staking-delegations-to)                         | Query all delegations to one validator                                                        |
| [unbonding-delegation](#petri-query-staking-unbonding-delegation)             | Query an unbonding-delegation record based on delegator and validator address                 |
| [unbonding-delegations](#petri-query-staking-unbonding-delegations)           | Query all unbonding-delegations records for one delegator                                     |
| [unbonding-delegations-from](#petri-query-staking-unbonding-delegations-from) | Query all unbonding delegatations from a validator                                            |
| [redelegations-from](#petri-query-staking-redelegations-from)                 | Query all outgoing redelegatations from a validator                                           |
| [redelegation](#petri-query-staking-redelegation)                             | Query a redelegation record based on delegator and a source and destination validator address |
| [redelegations](#petri-query-staking-redelegations)                           | Query all redelegations records for one delegator                                             |
| [pool](#petri-query-staking-pool)                                             | Query the current staking pool values                                                         |
| [params](#petri-query-staking-params)                                         | Query the current staking parameters information                                              |
| [historical-info](#petri-query-staking-historical-info)                       | Query historical info at given height                                                         |
| [create-validator](#petri-tx-staking-create-validator)                        | Create new validator initialized with a self-delegation to it                                 |
| [edit-validator](#petri-tx-staking-edit-validator)                            | Edit existing validator account                                                               |
| [delegate](#petri-tx-staking-delegate)                                        | Delegate liquid tokens to an validator                                                        |
| [unbond](#petri-tx-staking-unbond)                                            | Unbond shares from a validator                                                                |
| [redelegate](#petri-tx-staking-redelegate)                                    | Redelegate illiquid tokens from one validator to another                                      |

## petri query staking validator

### Query a validator by validator address

```bash
petri query staking validator <iva...>
```

## petri query staking validators

### Query all validators

```bash
petri query staking validators
```

## petri query staking delegation

Query a delegation based on delegator address and validator address.

```bash
petri query staking delegation [delegator-addr] [validator-addr]
```

### Query a delegation

```bash
petri query staking delegation <iaa...> <iva...>
```

Example Output:

```bash
Delegation:
  Delegator:  iaa13lcwnxpyn2ea3skzmek64vvnp97jsk8qrcezvm
  Validator:  iva15grv3xg3ekxh9xrf79zd0w077krgv5xfzzunhs
  Shares:     1.0000000000000000000000000000
  Height:     26
```

## petri query staking delegations

Query all delegations delegated from one delegator.

```bash
petri query staking delegations [delegator-address] [flags]
```

### Query all delegations of a delegator

```bash
petri query staking delegations <iaa...>
```

## petri query staking delegations-to

Query all delegations to one validator.

```bash
petri query staking delegations-to [validator-address] [flags]
```

### Query all delegations to one validator

```bash
petri query staking delegations-to <iva...>
```

Example Output:

```bash
Delegation:
  Delegator:  iaa13lcwnxpyn2ea3skzmek64vvnp97jsk8qrcezvm
  Validator:  iva1yclscskdtqu9rgufgws293wxp3njsesxxlnhmh
  Shares:     100.0000000000000000000000000000
  Height:     0
Delegation:
  Delegator:  iaa1td4xnefkthfs6jg469x33shzf578fed6n7k7ua
  Validator:  iva1yclscskdtqu9rgufgws293wxp3njsesxxlnhmh
  Shares:     1.0000000000000000000000000000
  Height:     26
```

## petri query staking unbonding-delegation

Query an unbonding-delegation record based on delegator and validator address.

```bash
petri query staking unbonding-delegation [delegator-addr] [validator-addr] [flags]
```

### Query an unbonding delegation record

```bash
petri query staking unbonding-delegation <iaa...> <iva...>
```

## petri query staking unbonding-delegations

### Query all unbonding delegations records of a delegator

```bash
petri query staking unbonding-delegations <iaa...>
```

## petri query staking unbonding-delegations-from

### Query all unbonding delegations from a validator

```bash
petri query staking unbonding-delegations-from <iva...>
```

## petri query staking redelegations-from

Query all outgoing redelegations of a validator

```bash
petri query staking redelegations-from [validator-address] [flags]
```

### Query all outgoing redelegatations of a validator

```bash
petri query staking redelegations-from <iva...>
```

## petri query staking redelegation

Query a redelegation record based on delegator and source validator address and destination validator address.

```bash
petri query staking redelegation [delegator-addr] [src-validator-addr] [dst-validator-addr] [flags]
```

### Query a redelegation record

```bash
petri query staking redelegation <iaa...> <iva...> <iva...>
```

## petri query staking redelegations

### Query all redelegations records of a delegator

```bash
petri query staking redelegations <iaa...>
```

## petri query staking pool

### Query the current staking pool values

```bash
petri query staking pool
```

Example Output:

```bash
Pool:
  Loose Tokens:   1409493892.759816067399143966
  Bonded Tokens:  590526409.65743521209068061
  Token Supply:   2000020302.417251279489824576
  Bonded Ratio:   0.2952602076
```

## petri query staking params

### Query the current staking parameters information

```bash
petri query staking params
```

## petri query staking historical-info

### Query historical info at given height

```bash
petri query staking historical-info <height>
```

## petri tx staking create-validator

Send a transaction to apply to be a validator and delegate a certain amount of petri to it.

```bash
petri tx staking create-validator [flags]
```

**Flags:**

| Name, shorthand              | type   | Required | Default | Description                                                                                      |
| ---------------------------- | ------ | -------- | ------- | ------------------------------------------------------------------------------------------------ |
| --amount                     | string | Yes      |         | Amount of coins to bond                                                                          |
| --commission-rate            | float  | Yes      | 0.0     | The initial commission rate percentage                                                           |
| --commission-max-rate        | float  |          | 0.0     | The maximum commission rate percentage                                                           |
| --commission-max-change-rate | float  |          | 0.0     | The maximum commission change rate percentage (per day)                                          |
| --min-self-delegation        | string |          |         | The minimum self delegation required on the validator                                            |
| --details                    | string |          |         | Optional details                                                                                 |
| --genesis-format             | bool   |          | false   | Export the transaction in gen-tx format; it implies --generate-only                              |
| --identity                   | string |          |         | Optional identity signature (ex. UPort or Keybase)                                               |
| --ip                         | string |          |         | Node's public IP. It takes effect only when used in combination with                             |
| --node-id                    | string |          |         | The node's ID                                                                                    |
| --moniker                    | string | Yes      |         | Validator name                                                                                   |
| --pubkey                     | string | Yes      |         | Go-Amino encoded hex PubKey of the validator. For Ed25519 the go-amino prepend hex is 1624de6220 |
| --website                    | string |          |         | Optional website                                                                                 |
| --security-contact           | string |          |         | The validator's (optional) security contact email                                                |

### Create a validator

```bash
petri tx staking create-validator --chain-id=petri --from=<key-name> --fees=0.3petri --pubkey=<validator-pubKey> --commission-rate=0.1 --amount=100petri --moniker=<validator-name>
```

:::tip
Follow the [Mainnet](../get-started/mainnet.md#create-validator) instructions to learn more.
:::

## petri tx staking edit-validator

Edit an existing validator's settings, such as commission rate, name, etc.

```bash
petri tx staking edit-validator [flags]
```

**Flags:**

| Name, shorthand       | type   | Required | Default | Description                                           |
| --------------------- | ------ | -------- | ------- | ----------------------------------------------------- |
| --commission-rate     | float  |          | 0.0     | Commission rate percentage                            |
| --moniker             | string |          |         | Validator name                                        |
| --identity            | string |          |         | Optional identity signature (ex. UPort or Keybase)    |
| --website             | string |          |         | Optional website                                      |
| --details             | string |          |         | Optional details                                      |
| --security-contact    | string |          |         | The validator's (optional) security contact email     |
| --min-self-delegation | string |          |         | The minimum self delegation required on the validator |

### Edit validator information

```bash
petri tx staking edit-validator --from=<key-name> --chain-id=petri --fees=0.3petri --commission-rate=0.10 --moniker=<validator-name>
```

### Upload validator avatar

Please refer to [How to upload my validator's logo to the Explorers](../concepts/validator-faq.md#how-to-upload-my-validator-s-logo-to-the-explorers)

## petri tx staking delegate

Delegate tokens to a validator.

```bash
petri tx staking delegate [validator-addr] [amount] [flags]
```

```bash
petri tx staking delegate <iva...> <amount> --chain-id=petri --from=<key-name> --fees=0.3petri
```

## petri tx staking unbond

Unbond tokens from a validator.

```bash
petri tx staking unbond [validator-addr] [amount] [flags]
```

### Unbond some tokens from a validator

```bash
petri tx staking unbond <iva...> 10petri --from=<key-name> --chain-id=petri --fees=0.3petri
```

## petri tx staking redelegate

Transfer delegation from one validator to another.

:::tip
There is no `unbonding time` during the redelegation, so you will not miss the rewards. But you can only redelegate once per validator, until a period (= `unbonding time`) exceed.
:::

```bash
petri tx staking redelegate [src-validator-addr] [dst-validator-addr] [amount] [flags]
```

### Redelegate some tokens to another validator

```bash
petri tx staking redelegate <iva...> <iva...> 10petri --chain-id=petri --from=<key-name> --fees=0.3petri
```
