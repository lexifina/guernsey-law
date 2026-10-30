# Guernsey: law history in git

The law of Guernsey as a git history: one file per provision, one commit per law on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every paragraph; `git log` lists every change; picking a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

**What is in it now (a first build, not complete)**

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `catalogue/` | Catalogue of the UK statutory instruments with "Guernsey" in their title: number, title, date made and link to each (facts only) | one per day | Each version adds the instruments made on one day, from the 1960s to 2026 |
| `*-si-YYYY-N/` | The full text, as made, of the UK Orders in Council and regulations about Guernsey that state their coming-into-force date: Orders extending UK Acts to the Bailiwick (for example the Geneva Conventions Act, the Territorial Sea Act 1987, the Immigration Act 1971 and the Civil Aviation Act 1982), and UK instruments about Guernsey | 1 each | Each is dated by the day it came into force. Later amendments are not applied. |
| `legal-system/` | Guernsey's legal system: open facts from Wikidata | 1 | A snapshot of Wikidata taken on 30 October 2026 |

**Language.** English.

**Sources.** [legislation.gov.uk](https://www.legislation.gov.uk/uksi), The National Archives: UK statutory instruments with "Guernsey" in their title, as made, read from the publisher's XML on 30 October 2026. They are Crown copyright, reused under the Open Government Licence v3.0. The legal-system facts are from [Wikidata](https://www.wikidata.org/wiki/Q25230) (CC0).

**This repository holds no Guernsey Law or Ordinance.** The Bailiwick's own legislation (Laws approved by Order in Council, Ordinances of the States of Deliberation, and statutory instruments made in Guernsey) is published by Guernsey Legal Resources, whose terms do not allow reuse, and the Copyright (Bailiwick of Guernsey) Ordinance, 2005 has no clear exemption for legislation. What is here is UK legislation that applies to or concerns Guernsey.

## Dates

Catalogue entries are dated by the day each instrument was made, as legislation.gov.uk records it. Each text is dated by the single coming-into-force date the instrument states; instruments that come into force on another event (for example on registration by the Royal Court of Guernsey) are catalogued but not given as text.

## How it is built

Lexifina reads the sources listed here and records each act's dated versions, and the laws that made each change, in one corpus file. `tools/build.py` writes this repository from that file, and the same corpus always gives the same commit hashes; `REPRODUCE.md` gives the details and the checks. A model (Claude) wrote Lexifina's code; it wrote no legal text, and no model runs when the history is built.

## How it is checked

Every version is read back from git on the day it took effect and on the day before (`tools/check_repo.py`) and must match `corpus.json`; results are in `REPRODUCE.md`.

## What "author" means

The author of a commit is the law that made the change, with an e-mail address that cannot exist. Each text is credited to its statutory instrument; catalogue entries to a catalogue key for the day; the legal-system snapshot to the publisher (oldest version available). The committer is always Lexifina.

## Limits

Not complete and not current. Guernsey's own Laws and Ordinances are not included. The instruments are as made: later amendments and revocations are not applied, so an Order here may since have been amended or revoked. The catalogue covers only instruments with "Guernsey" in their title; UK Acts and instruments that extend to Guernsey without naming it are not listed. Footnotes and explanatory notes are left out. This repository is not legal advice and not an official publication; for anything that matters, read the original.
