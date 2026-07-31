# Council request and decision process

## 1. Submit a request

Open the [slashing intervention form](https://github.com/aztec-slash-veto/council/issues/new?template=veto-request.yml) as soon as a potential incorrect slash is identified.

Include:

- Whether you request a veto of one round's complete payload or a temporary network-wide pause.
- The slashing round and affected validator addresses, if applicable.
- The offense type, exact Aztec node version, timeline, logs, and on-chain evidence.
- Why the event is systemic and outside the affected operators' reasonable control.

Do not include secrets, private keys, or credentials.

## 2. Initial review

The [on-duty request lead](request-lead-rota.md):

- Checks that the request is complete and that the payload has not been executed.
- Acknowledges the request and asks for any missing evidence.
- Alerts all Council members and coordinates time-sensitive review.

Submitting a request does not pause execution or guarantee intervention.

## 3. Assessment and decision

Council members assess:

- Whether the reported offenses and affected validators match on-chain data.
- Whether the cause is systemic, credible, and outside normal operator responsibility.
- The impact of vetoing the whole round payload or pausing all slashing.
- Whether a narrower protocol or operator response is available.

The request lead records an `APPROVED` or `DENIED` decision and a concise rationale in the issue. Any approved on-chain action requires at least five signatures from the 5-of-9 Council Safe.

## 4. Execution

For an approved request, the request lead:

- Coordinates the Safe transaction.
- Posts the transaction link and status in the issue.
- Confirms execution and closes the request.

A veto permanently blocks the complete payload for that slashing round. A global pause lasts three days unless the Council re-enables slashing earlier or extends the pause with another transaction.

## Roles

- **Request lead:** Monitors new requests, coordinates review, posts decisions, and tracks execution.
- **Council members:** Review evidence independently and, when approving an intervention, participate in the 5-of-9 Safe transaction.
