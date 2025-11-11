# Council Request & Decision Procedure

## Overview
This procedure outlines how requests are submitted, reviewed, and decided upon by the council using GitHub Issues.

## 1. Request Submission

- **Requester opens a GitHub issue** using the [request template](request-template.yml)
- Issue must include:
  - Clear title with `[REQUEST]` prefix
  - What they're requesting
  - Why it's needed
- Issue is automatically tagged with `request` and `pending-review` labels

## 2. Initial Review

- **Request Lead** (designated council member, rotates monthly) reviews new requests
- Request Lead performs initial assessment:
  - Verifies request is complete
  - Adds relevant labels as needed
  - Assigns all council members to the issue for visibility
- Posts acknowledgment comment: *"Under council review"*

## 3. Council Assessment

- All council members review the request independently
- Members interact via issue comments:
  - Ask clarifying questions
  - Raise concerns or considerations
  - Provide input and analysis
- **Voting via GitHub reactions** on the original issue:
  - 👍 = Approve
  - 👎 = Deny
  - 🤔 = Need more discussion

## 4. Decision

### If consensus is clear:
- Request Lead posts the decision directly in the issue

### If votes are split or unclear:
- Add `council-meeting` label to issue
- Discuss in next scheduled council meeting
- Reach consensus or majority vote
- Request Lead posts decision after meeting

## 5. Communication

Request Lead posts decision comment on the issue:

### If Approved:
- Add `approved` label
- Remove `pending-review` label
- Outline next steps and any conditions

### If Denied:
- Add `denied` label
- Remove `pending-review` label
- Provide brief, clear explanation
- Suggest alternatives if applicable
- Close the issue

### Decision comment should include:
- Clear statement: "APPROVED" or "DENIED"
- Reasoning summary
- Next steps (if approved)

## 6. Execution (If Approved)

- **Request Lead** takes ownership of implementation
- Provides progress updates via issue comments
- Links any related PRs or work items
- When complete:
  - Posts final comment: *"Completed: [brief summary]"*
  - Closes the issue
  - Adds `completed` label

## Labels Reference

- `request` - All incoming requests
- `pending-review` - Awaiting council decision
- `approved` - Request approved by council
- `denied` - Request denied by council
- `completed` - Approved request has been executed
- `needs-info` - Requires clarification from requester
- `council-meeting` - Needs discussion in meeting

## Roles

- **Request Lead:** Rotates monthly among council members
  - Monitors new requests
  - Facilitates review process
  - Posts official decisions
  - Executes approved requests
  - Provides status updates
  - Closes completed requests

- **Council Members:** All participate in every request
  - Review requests independently
  - Provide feedback and vote
  - Attend meetings for disputed items

## Best Practices

- Check for new requests regularly
- Respond to questions promptly
- Keep discussion focused and professional
- Document reasoning for decisions
- Update request status promptly
- Maintain a decision log for transparency