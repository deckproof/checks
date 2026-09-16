# deckproof-checks

The checks [Deckproof](https://deckproof.dev) explains publicly, as machine-readable data: what each one looks for, in English and German, and which standard or law it points at.

44 checks here, out of 84 distinct findings the scanner can emit. The rest are variants and "we looked and found nothing" rows that are not worth their own explanation.

## Why this exists

Most write-ups about AI-built ("vibe-coded") websites stop at "it might be insecure". If you build for a German or EU audience, the interesting part is more specific: the site is live, it is a business, and a handful of concrete obligations now apply to it. § 5 DDG wants an imprint that is easy to find and actually resolves at the address you linked. Art. 13 GDPR wants a privacy notice that names who receives the data, which includes the third parties your page quietly loads. § 25 TDDDG wants consent before non-essential trackers fire, not after. The German Accessibility Act has applied since 28 June 2025, and good intentions do not waive it.

This file is the list of things we check for, written so a person can read it and a machine can parse it. Take it, disagree with it, build your own.

## Format

`checks.json`:

```json
{
  "total_finding_ids": 84,
  "explained_here": 44,
  "checks": [
    {
      "id": "A-01",
      "category": "security",
      "severity": "critical",
      "standard": "OWASP A01:2025",
      "slug": "supabase-rls-anon-read",
      "en": { "title": "...", "what": "..." },
      "de": { "title": "...", "what": "..." }
    }
  ]
}
```

- `category` is one of `security`, `legal`, `quality`.
- `severity` in this file is one of `critical`, `high`, `medium`, `low`. The scanner also emits `info` rows; those are not explained here.
- `standard` is the norm, CWE entry or paragraph the check points at. `Reliability`, `SEO` and `Web performance` mark checks that answer to no formal standard.
- `slug` is a stable, human-readable key for the check. It is not a URL: there is no page per check today. Use `id` to join against a Deckproof report, and `slug` if you want a readable key that does not look like a code.

## What this is not

It is not the scanner. The engine is not in here, and this list will not tell you how any individual check is implemented.

It is not legal advice, and neither is the product. A missing imprint is not automatically an offence: private pages are exempt, and whether an obligation applies at all depends on the case. Everything here reports the presence or absence of a technical feature. What follows from that is a question for a lawyer.

Nothing in here is a promise of completeness. The set of things that can be wrong with a website is larger than any list.

## Kurzfassung auf Deutsch

Das sind die Prüfpunkte, die Deckproof öffentlich erklärt, als maschinenlesbare Datei: was geprüft wird, auf Deutsch und Englisch, und auf welche Norm oder welchen Paragraphen sich der Punkt jeweils bezieht. 44 Einträge von insgesamt 84 möglichen Befunden.

Das ist keine Rechtsberatung und kein Scanner. Berichtet wird, ob ein technisches Merkmal vorhanden ist oder nicht. Ob daraus im Einzelfall eine Pflichtverletzung folgt, entscheidet das nicht.

## Licence

The data in `checks.json` and this README are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use them, change them, publish them, including commercially. Name the source: "Deckproof, deckproof.dev".

## Regenerating

`checks.json` is generated from the catalogue behind `deckproof.dev/checks`. If a check changes there, this file is regenerated, not edited by hand.
