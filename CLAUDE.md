# Drury International — project conventions

## Writing
Keep every page concise. No repetition: if a rule is stated in an intro paragraph, do not
restate it in a callout, a bullet, and a card. Each element on the page should add something
the reader does not already have. Sections should flow in the order a student would act on
them. Cut wordy lead-ins and hedging; say the thing once, in the place it is most useful.

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
