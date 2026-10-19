# contract-summary-skill

A Cerase skill that has the assistant read a contract in full and write the summary a person keeps beside it: parties and object, duration and notice, a table of dates, each party's obligations, money, how it ends, liability, confidentiality, law, and what is missing or unusual, every point citing its clause.

## What the assistant does

1. Reads the whole text with `cerase-docreader.read_document`, from a mail attachment saved with `gmail.download_attachment`, from a Google Doc with `google-workspace.readGoogleDoc`, or from a scan with `cerase-media.ocr`.
2. Writes the summary, every point with its clause, and a computed date shown with the dates it comes from.
3. On request, schedules a reminder before a date with `cerase-schedule.create_once`, which waits for the person's approval.

## What it never does

- Gives a legal opinion.
- Invents a clause, a date, a figure or a party.
- Signs, sends or changes the contract.

## Requirements

The document reader (`cerase-docreader`); Gmail (`gmail`), Google Workspace (`google-workspace`) and the media reader (`cerase-media`) for contracts that arrive that way.

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | The instructions the assistant loads. |
| `cerase.json` | Marketplace manifest: namespace `studio.guidance`, name `contract-summary`, display name, description, licence. |
| `i18n.yaml` | Italian display name and description for the Marketplace; not sent to the assistant. |
| `LICENSE` | MIT licence text. |

## Installation

Published in the Cerase Marketplace as `studio.guidance/contract-summary`.
A Cerase appliance also ships it in its image.

## License

MIT. See [LICENSE](LICENSE).
