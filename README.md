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

