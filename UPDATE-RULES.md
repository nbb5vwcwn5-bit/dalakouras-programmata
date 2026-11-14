# Rules for updating programmata.json

This file is the standing brief for the scheduled update. Read it fully before changing anything.

## What the file is

`programmata.json` feeds the «Επιδοτήσεις» page of dalakouras.gr, the site of an accounting, insurance and energy office in Larisa. The site fetches the raw file once a day, sanitises it and renders it. Readers are business owners, professionals, farmers and private individuals in Thessaly.

## Scope

Keep programmes that a client in Thessaly can use:
- nationwide programmes (ΕΣΠΑ, Αναπτυξιακός νόμος, ΔΥΠΑ, Ελληνική Αναπτυξιακή Τράπεζα, ΚΑΠ / Υπουργείο Αγροτικής Ανάπτυξης);
- regional programmes for Thessaly (Περιφέρεια Θεσσαλίας, LEADER Λάρισας, Καρδίτσας, Τρικάλων, Μαγνησίας);
- ΔΥΠΑ programmes both for employers and for individuals (unemployed, training with allowance, new freelancers).

Leave out programmes limited to other regions, research consortia, and programmes for very large companies only. Aim for 10 to 25 entries in total.

## Sources

1. Prefer official pages: dypa.gov.gr, espa.gr, efepae.gr, ependyseis.mindev.gov.gr, hdb.gr, agrotikianaptixi.gr, minagric.gr, opske.gr, thessalia-espa.gr, aenol.gr, anka.gr, kenakap.gr, diavgeia.gov.gr.
2. Some official sites block automated requests. Then use established news and tax sites for the facts (taxheaven.gr, e-forologia.gr, forin.gr, naftemporiki.gr, agronews.gr, skai.gr). A fact from news sites needs two independent sources, or one source that quotes the official announcement.
3. Aggregator sites (for example vriskoepidotisi.gr, ilfconsult.com) may be used only as a lead for what exists. Never copy or paraphrase their wording, and never name them.
4. If a figure or date cannot be confirmed, leave it out. Never guess. An entry without a confirmed deadline says so in `until`.

## Writing

- Greek, polite plural, plain words, our own wording. No marketing language, no slogans, no exclamation marks.
- `title`: short and recognisable. `summary`: one or two sentences on what the reader gets.
- `facts`: at most three pairs `[label, value]`, short.
- `who`: who can apply. `note`: what it covers or what to watch out for.
- Plain text only. No HTML, no Markdown, no links inside text fields.
- Never mention a mobile phone number, tax numbers or any person's name.

## Fields

- `id`: stable lowercase slug. Never change the id of an existing entry.
- `cats`: any of `ep` (Επιχειρήσεις), `ag` (Αγρότες), `pr` (Προσλήψεις), `id` (Ιδιώτες και άνεργοι), `da` (Δάνεια).
- `status`: `auto` (the site decides from the dates) or `soon` (announced, not open yet).
- `opens`, `closes`: `YYYY-MM-DD` or empty. With `auto`, an entry whose `closes` has passed moves to «Έκλεισαν» on its own.
- `until`: short text shown when there is no closing date, for example «Μέχρι να καλυφθούν οι θέσεις» or «Χωρίς προθεσμία».
- `url`: the official page of the programme (https, one of the official domains above). `source`: the body's name.
- `verified`: date the entry was last confirmed.
- Top-level `checked`: date of this run. Update it on every run, even when nothing else changed.

## Each run

1. Re-check every open and upcoming entry: extensions, new deadlines, budget exhausted, opened.
2. Look for new programmes within scope and add them.
3. Keep closed entries for 60 days after `closes`, then remove them.
4. Validate: the file parses as JSON, every entry has all fields, dates are valid, ids are unique.
5. Commit to `main` with a short Greek message that says what changed. Push to `main` directly. Do not open a pull request.
6. Report to the owner only when something matters to him: a new programme worth promoting, a deadline within 10 days, or a source that could not be checked twice in a row. Otherwise stay silent.

If a run cannot confirm anything (network trouble), change only nothing and do not update `checked`.
