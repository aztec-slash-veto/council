# Aztec SlashVeto Council

The Aztec SlashVeto Council is a temporary safety body of [nine Aztec community members](council-members.md), intended to protect the protocol from incorrect, systemic slashing during its first year.

The Council controls the mainnet `Slasher` vetoer through a [5-of-9 Safe](https://app.safe.global/settings/setup?safe=eth:0xBbB4aF368d02827945748b28CD4b2D42e4A37480). It can:

1. Permanently veto a slashing payload for a round. A payload may contain slashes for several validators; the Council cannot remove only one action from it.
2. Temporarily disable all slashing for three days. The Council can re-enable it early or extend the pause with another transaction.

Mainnet slashing rounds normally have an execution delay of about three days. A payload can only be vetoed before it is executed, so submit requests immediately.

## When the Council may intervene

The Council is a last-resort safeguard for incorrect slashing caused by a systemic event outside an operator's reasonable control.

Examples that may be in scope:

- A confirmed bug in Aztec node software or the on-chain contracts that causes incorrect offenses.
- A network-wide or shared dependency failure that affects many sequencers at once.
- A network launch or restart that requires a temporary slashing pause.

Examples that are out of scope:

- Downtime, missed duties, misconfiguration, or other failures within an operator's control or that could have been prevented by [available monitoring](https://slashveto.me/?view=pingme).
- Failure to follow the [current sequencer guidance](https://docs.aztec.network/operate/operators/sequencer-management/slashing_and_offenses#best-practices).
- Failures isolated to one operating system, infrastructure provider, or L1 client when reasonable alternatives are available.

The Council assesses each request independently. Any on-chain action requires at least five Council signatures.

## Request help or monitor slashing

[Open a formal intervention request](https://github.com/aztec-slash-veto/council/issues/new?template=veto-request.yml) and include the requested action, slashing round, affected validator addresses, offense type, node version, and supporting evidence. See the [decision process](request-process.md), [request-lead rota](request-lead-rota.md), and [Council contacts](council-members.md).

To monitor your sequencers with notifications, or follow network-wide slashing activity, use [SlashVeto Monitor](https://slashveto.me/?view=pingme).

## Current Aztec v5 offenses

Aztec sequencers automatically detect offenses and vote on them when proposing. In mainnet round `N`, proposers vote on offenses from round `N-2`; a round is 128 L2 slots, or about 2.6 hours at 72 seconds per slot. Penalties and activation status are network configuration, so consult the [current Aztec slashing documentation](https://docs.aztec.network/operate/operators/sequencer-management/slashing_and_offenses) for live values.

| ID | Offense | What triggers it | Responsible validator(s) |
|---:|---|---|---|
| 1 | `DATA_WITHHOLDING` | Transaction data for a published checkpoint is unavailable after the tolerance window. | Checkpoint attesters |
| 3 | `INACTIVITY` | A committee member repeatedly misses required attestations or proposals above the configured threshold. | Inactive validator |
| 4 | `BROADCASTED_INVALID_BLOCK_PROPOSAL` | An invalid block proposal is broadcast over P2P. | Block proposer |
| 11 | `BROADCASTED_INVALID_CHECKPOINT_PROPOSAL` | An invalid checkpoint proposal is broadcast over P2P. | Checkpoint proposer |
| 5 | `PROPOSED_INSUFFICIENT_ATTESTATIONS` | A checkpoint is published to L1 without enough valid committee attestations. | Checkpoint proposer |
| 6 | `PROPOSED_INCORRECT_ATTESTATIONS` | A checkpoint is published to L1 with invalid signatures or non-committee signers. | Checkpoint proposer |
| 7 | `PROPOSED_DESCENDANT_OF_CHECKPOINT_WITH_INVALID_ATTESTATIONS` | A checkpoint published to L1 descends from one with invalid or insufficient attestations. | Descendant checkpoint proposer |
| 10 | `ATTESTED_TO_INVALID_CHECKPOINT_PROPOSAL` | A committee member attests to a checkpoint covering a slot with a detected invalid block proposal. | Attesting committee members |
| 8 | `DUPLICATE_PROPOSAL` | A proposer broadcasts conflicting block or checkpoint proposals for the same position. | Proposer |
| 9 | `DUPLICATE_ATTESTATION` | A validator signs conflicting attestations for the same slot. | Attester |

The Council may update this process when necessary to protect the protocol.
