# Drury International — project conventions

## Writing
Keep every page concise. No repetition: if a rule is stated in an intro paragraph, do not
restate it in a callout, a bullet, and a card. Each element on the page should add something
the reader does not already have. Sections should flow in the order a student would act on
them. Cut wordy lead-ins and hedging; say the thing once, in the place it is most useful.
No em dashes. Use a comma, a colon, or a second sentence instead.

## File downloads
Any standalone downloadable file (PDF, form, matrix) uses the **download block**, not a plain
link or secondary button. Pattern (as on the SEVIS page, "Program Extension Application"):

```html
<div style="background:#F3F0EB;border:1px solid #E3DFD9;padding:clamp(18px,2.2vw,24px);margin-top:clamp(20px,2.5vw,26px);display:flex;flex-wrap:wrap;gap:18px;align-items:center;justify-content:space-between">
<div style="flex:1 1 280px;min-width:0">
<div style="font-size:10.5px;font-weight:600;letter-spacing:.14em;color:#A6192E">DOCUMENT NAME IN CAPS</div>
<p style="font-size:14.5px;line-height:1.65;color:#4A4640;margin:9px 0 0">One sentence on what it is and what to do with it.</p>
</div>
<a href="…" target="_blank" rel="noopener noreferrer" style="flex:none;background:#A6192E;color:#fff;font-size:14px;font-weight:600;padding:13px 22px;text-decoration:none" style-hover="background:#8A1426">Download … (PDF)<span style="position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap;border:0">(opens in a new tab)</span></a>
</div>
```

Exception: a file referenced mid-sentence inside prose or a checklist step stays an inline
link — use the block when the download is the point of the element.

## Clickable tiles and cards
Every clickable tile or card — a row of links to other pages, external resources, or
downloadable references — uses the **card link** pattern (as on the Campus Life page,
"College Park", "Jefferson Park"): a flex-wrap row, `gap:12px`,
`margin-top:clamp(20px,2.5vw,26px)`, with each card

```html
<a href="…" style="display:flex;flex-direction:column;gap:5px;flex:1 1 200px;min-width:0;background:#fff;border:1px solid #E3DFD9;border-left:3px solid #A6192E;padding:16px 18px;color:#1C1B19;text-decoration:none" style-hover="border-color:#A6192E;color:#A6192E"><span style="font-size:15px;font-weight:600">Label</span><span style="font-size:13px;color:#6B6560">Short qualifier</span></a>
```

The second span is a short qualifier, not a sentence; omit it only when the label needs no
gloss. External links add `target="_blank" rel="noopener noreferrer"` and the visually hidden
"(opens in a new tab)" span. Do not use bare buttons, plain lists, or a CSS grid for these rows.

## Navigation rows
A vertical list of links — a page directory, or a summary whose items jump to sections
further down — uses the **navigation row** pattern (as on the Student Support page's
directory, and "Staying in status" on the Immigration page): a column container with
`margin-top:clamp(20px,2.5vw,26px);border-top:1px solid #E3DFD9`, each row

```html
<a href="…" style="display:flex;flex-wrap:wrap;gap:8px clamp(16px,2vw,28px);align-items:baseline;padding:20px 0;border-bottom:1px solid #EDE9E3;color:#1C1B19;text-decoration:none" style-hover="color:#A6192E"><span style="flex:1 1 200px;min-width:0;font-size:16px;font-weight:600">Label</span><span style="flex:2 1 260px;min-width:0;font-size:14px;line-height:1.6;color:#4A4640">One sentence.</span><span style="flex:none;font-size:15px;color:#A6192E">→</span></a>
```

The arrow is what marks the row as clickable — never omit it, and never use this pattern for
rows that are not links (a two-column table of terms and explanations keeps the same layout
without the arrow and without the anchor). Use the card link pattern instead when the items
belong side by side in a row rather than stacked.

## Card footer links
When a row of cards ends in a link on each card ("Full instructions →", "Payment plan
information →"), the link is the card's **footer**: pinned to the bottom of the card above a
hairline rule, so every card in the row ends on the same baseline regardless of body length.
In the Astro codebase this is `InfoCard`'s `footer` slot:

```astro
<InfoCards>
  <InfoCard eyebrow="ACCEPT YOUR AWARDS" tone="ink">
    <p>Body copy…</p>
    <ExtLink slot="footer" href="…">Full instructions with screenshots →</ExtLink>
  </InfoCard>
</InfoCards>
```

Do not hand-place a link as the last paragraph of a card; use the slot so the rule, spacing,
and bottom alignment stay consistent. One link per footer; the arrow marks it as the card's
action.
