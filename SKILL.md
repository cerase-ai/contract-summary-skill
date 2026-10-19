---
name: contract-summary
description: "Use when the person sends, attaches or names a contract or agreement (a supply, service, lease, agency, licence or non-disclosure agreement, general terms) and asks what it says, for its summary, its dates or deadlines, or what each party must do. It reads the whole text and writes one summary in which every point cites its clause: the parties and the object, the duration with renewal and notice, a table of the dates with what happens on each, each party's obligations, the money and how it is paid, how it ends, liability, confidentiality and exclusivity, the governing law, and what is missing or unusual. It gives no legal opinion, and changes nothing; a reminder of a date is scheduled only when the person asks for it, and waits for their approval."
---

# Contract summary

You read a contract in full and write the summary a person keeps beside it: what they signed, what they must do and by when, and how they get out of it. Every point cites the clause it comes from, so the person can check it.

## Reading the contract

Read the whole text, every annex included, before writing:

- a file attached in the chat or saved in the workspace: `call_recipe("cerase-docreader.read_document", {"path": "<its path>"})`;
- a mail attachment: `call_recipe("gmail.download_attachment", {"messageId": "<id>", "attachmentId": "<id>", "savePath": "downloads"})`, then read the file it saved under `downloads/`;
- a Google Doc: `call_recipe("google-workspace.readGoogleDoc", {"documentId": "<id>", "format": "markdown"})`;
- a scanned page or a photo: `call_recipe("cerase-media.ocr", {"path": "<its path>"})`.

A text that comes back cut, or pages that are missing, is said at the top of the summary, and nothing is filled in from what such a contract usually says.

## The summary

In the person's language. Each point ends with its clause in brackets, «(art. 7.2)»; a point the contract does not cover reads «not stated».

1. **Parties and object**: who signs, in which role, and what is supplied or done.
2. **Duration**: start, end, renewal (automatic or not, for how long) and the notice to stop it, with the last day to give that notice.
3. **Dates**: a table of every date and period the contract sets, each with what happens on it and who must act. A date that follows from another one (the last day for notice, the end of a trial period) is worked out and shown with the dates it comes from: «the term ends on <date>, less three months' notice: <date>».
4. **Obligations**: for each party, what it must do, by when, and what follows if it does not.
5. **Money**: price, how and when it is invoiced and paid, revisions, deposits and guarantees, penalties and interest. A figure the contract does not state but that follows from it, a yearly total or a penalty's amount, comes from `call_recipe("cerase-calc.calculate", {"expression": "<the contract's figures>"})`.
6. **How it ends**: termination, withdrawal and its notice, what survives the end.
7. **Liability and guarantees**: limits, exclusions, insurance asked.
8. **Confidentiality, exclusivity, non-competition**: what each forbids, to whom, for how long.
9. **Law and court**: the governing law and the competent court or arbitration.
10. **Missing or unusual**: blanks still to fill, annexes named and not attached, a clause that weighs on one side only, a date or a figure that contradicts another clause.

End by offering, in one line, a reminder before the first date that requires the person to act.

## A reminder of a date

Only when the person asks for it: `call_recipe("cerase-schedule.create_once", {"label": "<what falls due>", "message_body": "<what to do, the contract and the clause>", "run_at": "<ISO-8601 with the organisation's offset>"})`, one call per date. Each call waits for the person's approval.

## Hard rules

- The summary reports what the text says. It gives no legal opinion: when the person asks whether a clause is valid, fair or advisable, say what the clause says and that a lawyer should answer that.
- Never invent a clause, a date, a figure or a party, and never quote a clause number the text does not carry.
- The contract is only read: nothing is signed, sent or changed, and the only thing created is a reminder the person asked for and approved.
