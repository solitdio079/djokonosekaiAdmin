# djokonosekai — Shared visual system

## Brand foundation
Match the live Bysolitdio visual language, not its marketing content. Use the lowercase djokonosekai wordmark in Space Grotesk 700. Retain sparse orbital line art as a decorative brand gesture on the journal hero and authentication backgrounds. Do not put orbit artwork behind body text or in dense admin work areas.

| Token | Exact value | Use |
|---|---|---|
| Canvas | #080909 | Page background |
| Panel | #111313 | Cards, forms, sidebar |
| Ink | #EEF8F7 | Primary text |
| Muted | #AAAEAD | Descriptions, metadata |
| Divider | #2A2D2C | Decorative rules and card separators |
| Action | #E35F21 | Primary button fill |
| Gold | #FAAB05 | Eyebrows, selected indicators, focus ring |
| Action text | #111111 | Text on orange/gold |
| Control border, proposed | #737A78 | Input boundaries requiring stronger contrast |
| Error, proposed | #FF8D86 | Error copy, destructive outline |
| Success, proposed | #7DCEA3 | Saved/verified icon with text |

The first seven colors and action text come from the existing portfolio source. The final three are proposed functional extensions. Thin Divider is decorative; do not use it as the only visible boundary for an input. Never rely on color alone for private/public, verified/unverified or errors. Orange buttons use dark text; ordinary body copy uses Ink or Muted. Check final contrast in the editable design at real sizes; raster previews do not certify accessibility.

## Type
Use **Space Grotesk** weights 500/600/700 for headings and wordmark; **Inter** 400/500/600/700/800 for body and controls. These are the font families loaded by the reference site's root file. Use system sans-serif fallback. Do not substitute a serif or monospaced editor font as seen in incidental generated text.

| Role | Desktop size/line | Mobile size/line | Weight |
|---|---|---|---|
| Client hero | 88/84 px | 44/46 px | 700 |
| Article title | 64/68 | 36/40 | 700 |
| Admin page title | 32/38 | 28/34 | 600 |
| Section title | 28/34 | 24/30 | 600 |
| Card title | 24/30 | 22/28 | 600 |
| Reading text | 20/34 | 18/30 | 400 |
| UI body | 16/26 | 16/26 | 400 |
| Label / button | 14/20 | 14/20 | 600 |
| Metadata | 13/20 | 13/20 | 400–500 |
| Eyebrow | 11/16, tracking 0.14em | 11/16 | 800 |

Headings use modest negative tracking (roughly -0.035em), normal sentence case, short lines. Reserve all-caps for eyebrows and workspace labels. Body line length target 55–75 characters.

## Shape, space, components
Spacing scale: 4, 8, 12, 16, 24, 32, 48, 64, 80, 96px. Cards 24px padding; mobile 20px. Page sections 64–96px client, 32–48px admin. Square corners, 0–4px radius; reserve circles for small identity initials and orbit art. Avoid drop shadows; use tonal panels and fine rules.

Buttons: 44px minimum height, 16–20px horizontal padding. Primary solid Action/dark text; hover Gold/dark text. Secondary transparent with Control border and Ink text. Danger transparent with Error border/text; filled danger only inside final confirmation. Disabled uses muted treatment plus a clear reason when needed. Pending keeps width stable and shows progress text. Focus is a visible 2px gold ring, offset 3px. Use one dominant primary per work area.

Inputs: at least 48px height; label above; helper/error below; Panel background and Control border; 16px entry text. Multiline fields at least 120px; editor at least 400px desktop. Password show/hide is a named control. Required fields are identified in text.

Chips: compact rectangles, 4px radius; topic chips include readable labels. A removable chip needs a separate 44px target in touch layouts. Status badges always say Public/Private or Verified/Unverified. Tables: 48px header, 64px default row, left-aligned text. Mobile uses cards with labels rather than clipped tables.

Dialogs: maximum 480px wide, specific title, short consequence text, Cancel first and named action second. Restore focus to the invoking control on dismissal. Escape cancels. Do not present destructive actions through icon-only controls. Mobile menu is a labelled sheet with a visible close action.

## Accessibility and motion
Minimum 44×44px touch targets; keyboard focus on every action; logical heading order; visible labels and error text; focus trap for modal dialogs; reading order follows visual order; text can expand without overlap. At 200% text size content must remain available. Verify contrast against WCAG AA targets (4.5:1 normal text; 3:1 large text and essential control boundaries). Hover is never the only way to reveal actions. Use a short 120–180ms color transition, and honor reduced motion. Avoid the reference site's upward hover shift on dense admin controls.

## Figma handoff structure
Create one design file per frontend with pages: 00 Read me; 01 Foundations; 02 Components; 03 Desktop; 04 Mobile; 05 States; 06 Prototype flows. Name frames C01…C10 and A01…A10 as in the briefs. Desktop baseline 1440px, tablet 768px, mobile 390px, narrow test 320px. Place PNG concept sheets on a locked References page; they are visual references, not editable components.

Components: Header (guest/member), Sidebar (expanded/drawer), Button (primary/secondary/danger × default/hover/focus/disabled/pending), Field (default/focus/error/disabled), StatusBadge, TopicChip, StoryCard, Comment (guest/own/other/editing), TableRow, EmptyState, InlineAlert, ConfirmDialog, Toast. Specify auto layout, wrapping text and content-driven heights when rebuilding in Figma. The PNGs do not contain those properties.

Prototype flow annotations: read → authenticate → return → comment; account → change email → verification; admin → new private post → preview → save; user detail → role confirmation → success or failure. Include error branches. None of these flows is an executable implementation in this package.
