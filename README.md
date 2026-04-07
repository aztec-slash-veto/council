## What is the Aztec slashVeto Council?

The Aztec slashVeto Council is a group of [nine Aztec community members](https://github.com/aztec-slash-veto/council/blob/main/council-members.md) committed to the long term health of Aztec Protocol. It is expected that the Council will operate and exist for the first year of the protocol's life and be sunset after that.

The slashVeto Council is permissioned to execute two actions in the Aztec protocol:
1. Pausing slashing across the network for 72 hours 
2. Vetoing the outcome of a specific slashing vote up to 72 hours after the voting period ends

The Council is represented by a [5/9 multisig](https://app.safe.global/settings/setup?safe=eth:0xBbB4aF368d02827945748b28CD4b2D42e4A37480) and will take requests for either of two activities in the [issues section of this repo](https://github.com/aztec-slash-veto/documentation/issues).

## Why does the slashVeto Council exist?

The power to veto or pause slashing across the network addresses the extremely unlikely case of slashing events that fall outside the scope of an operator's responsibility to run a resilient service for the network.

The scope of incidents for which the slashVeto Council will entertain requests is narrow by design. The decision to halt or veto a slashing vote is a serious intervention in the decentralized protocol and will only be used for events that threaten the integrity of the network.

Examples of events that are **in scope** for slashVeto requests:
- A confirmed bug in the Aztec node software or the onchain smart contracts that leads to slashing events (while there is no widespread client diversity)
- A network launch or relaunch that requires an initial 72hr halt as the network starts/restarts
- Upstream bugs that affect a large amount of Sequencers at the same time (e.g. in a library or a programming language the Sequencer uses)

Examples of events that are **out of scope** for slashVeto requests:
- Software bugs in specific L1 consensus or execution clients (while there is widespread client diversity)
- Any slashing that is a consequence of not following [operator best practices](https://docs.aztec.network/the_aztec_network/setup/high_availability_sequencers)
- Bugs affecting a certain operating system and by extension the operators that run on that OS

## How do I contact the slashVeto Council?

Formal requests to veto or pause slashing must be made using the [issue tracker](https://github.com/aztec-slash-veto/council/issues) in the Council github repo. Once a request is made, the [on-duty request lead](https://github.com/aztec-slash-veto/council/blob/main/request-lead-rota.md) for that month is responsible for managing the assessment process as outlined in [request-process.md](https://github.com/aztec-slash-veto/council/blob/main/request-process.md)

If you need guidance on making a request you can contact the current Council member on duty as shown in the [request-lead.md](https://github.com/aztec-slash-veto/council/blob/main/request-lead-rota.md) document. Failing that, you can reach out to any of the Council members using their contact details listed [here](https://github.com/aztec-slash-veto/council/blob/main/council-members.md)

The slashVeto Council is a fallback for unforeseen emergencies that were not accounted for by the protocol, so we try to be as thorough and individual as possible when assessing requests, but reserve our independence and internal 5/9 consensus in making the ultimate decision.

The SlashVeto Council reserves the right to change the documented processes during the lifetime of the Council and in the interests of protecting the protocol.

## Default Offense types
Offenses and slashing amounts are configured in the aztec sequencer software. Here is an example config (the default config of v4.1.2). 

| `offenseType` | Name | Description | Time Unit | Detection | Target |
|---|---|---|---|---|---|
| **0** | `UNKNOWN` | Default/unknown offense type | Epoch | — | — |
| **1** | `DATA_WITHHOLDING` | The data required for proving an epoch was not made publicly available | Epoch | `EpochPruneWatcher` detects when an epoch cannot be proven due to missing data | Committee members of the affected epoch |
| **2** | `VALID_EPOCH_PRUNED` | An epoch was not successfully proven within the proof submission window | Epoch | `EpochPruneWatcher` monitors epochs that expire without valid proofs | Committee members of the unpruned epoch |
| **3** | `INACTIVITY` | A proposer failed to attest or propose blocks during their assigned slots | Epoch | `Sentinel` tracks validator performance and identifies validators who miss attestations beyond threshold | Individual inactive validator |
| **4** | `BROADCASTED_INVALID_BLOCK_PROPOSAL` | A proposer broadcast an invalid block proposal over the p2p network | Slot | Validators detect invalid proposals during attestation validation | Proposer who broadcast the invalid block |
| **5** | `PROPOSED_INSUFFICIENT_ATTESTATIONS` | A proposer submitted a block to L1 without sufficient committee attestations | Slot | `AttestationsBlockWatcher` checks L1 blocks for attestation count | Block proposer |
| **6** | `PROPOSED_INCORRECT_ATTESTATIONS` | A proposer submitted a block to L1 with signatures from non-committee members | Slot | `AttestationsBlockWatcher` validates attestation signatures against committee membership | Block proposer |
| **7** | `ATTESTED_DESCENDANT_OF_INVALID` | A committee member attested to a block built on top of an invalid ancestor | Slot | `AttestationsBlockWatcher` tracks invalid blocks and their descendants | Committee members who attested to the descendant block |
| **8** | `DUPLICATE_PROPOSAL` | A proposer sent multiple block/checkpoint proposals for the same position with different content (equivocation) | Slot | P2P layer; `AttestationPool` flags when a second proposal arrives for the same position with a different archive | Proposer who broadcast the duplicate |
| **9** | `DUPLICATE_ATTESTATION` | A validator signed attestations for different proposals at the same slot (equivocation) | Slot | P2P layer | Attesting validator | [2](#0-1) 


