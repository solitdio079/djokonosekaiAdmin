# djokonosekai — Admin design brief

11 September 2026 · Design handoff · No frontend implementation

## Intent
A focused publishing workspace for administrators. Make writing, visibility and user management legible without turning the product into a generic analytics dashboard. Share the Bysolitdio palette and typography with the reader experience, using denser spacing and a stable sidebar.

The brand is **djokonosekai**, one lowercase word. “ADMIN” is a small gold workspace label. Existing application files remain untouched. API evidence comes from `/Users/djokokeita/repos/API/djokoNoSekai`, commit `20a8ee8` plus inspected working-tree source. Live brand reference: https://bysolitdio.com/, inspected 11 September 2026; exact tokens from the local `bysolitdio-portfolio/app/app.css` and `app/root.tsx`. The spoken API hostname was not verified; this is a source-based brief, not a live API audit.

Raster mockups illustrate the direction. Page specifications and wireframes define the exact behavior. This package is ready to recreate in Figma, but is not a native editable Figma file.

## Workspace navigation
A 232px sidebar holds wordmark, ADMIN label, Overview, Posts, Users and My account. Sign out sits at the bottom. Comments are opened in the context of a post or user; there is no global comments/moderation queue endpoint. A small “Open journal” link is a future connection once the public client works.

Primary journey: Sign in → Posts → New post → save private → preview → choose public → save. Secondary: Users → user details → review role → confirm role change. There is no admin signup flow; ordinary signup creates USER accounts.

## Screen inventory
| ID | Screen | Layout and content | Actions and states |
|---|---|---|---|
| A01 | Admin sign-in / denied | Centered 440px form, email and password; ADMIN eyebrow; neutral orbital corner | Sign in; loading; invalid credentials; non-admin access denied with return to client |
| A02 | Overview | Page title; three restrained summary blocks Public posts, Private posts, Users; recent posts list | New post; open post; counts derived from loaded lists only |
| A03 | Posts | Title and New post; All/Public/Private tabs; title/status/updated/actions table | Open editor; Preview; Delete confirmation; client-side filtering of loaded list |
| A04 | New post / edit post | Title; large plain-text body; 280px side panel for visibility and topics; save area | Save post; local preview; unsaved, saving, saved, failed; leave-with-unsaved-changes prompt |
| A05 | Post preview | Reader-like title, topics, date and body within admin shell; preview banner | Back to editor; preview current unsaved form; no server preview endpoint needed |
| A06 | Post comments | Post context at top, flat comment list with member ID/date/content | Read; edit/delete only if own; no approve, reject or admin-wide deletion |
| A07 | Users | Name/email/role/verified/joined table; row opens detail | Filter loaded rows; view detail; no create-user or invitation action |
| A08 | User detail | Drawer 400px wide or dedicated mobile page; name/email read-only; role; verification; Posts/Comments tabs | Change role after confirmation; delete after confirmation; view associated content |
| A09 | My account | Self name/email edit; verification; password flow | Same self-account behavior as client; cannot edit other users’ profile data |
| A10 | Confirmation / error states | Compact dialogs for deletion, role change, unsaved navigation; full-page denied/not found | Explicit Cancel and named action; preserve context on failure |

## Detailed visual treatment
Overview should have no charts, traffic, revenue, unread counters or trend percentages. Counts are derived summaries, not analytics. Posts uses 64px rows with visible status text and a subtle gold or neutral badge. The entire title is a link; the overflow menu has an accessible label. At most one orange primary action per work area. Edit and Preview are secondary outlined or text actions. Deletion is red text with a red outline; it must never use the same orange styling as Save.

The editor is calm: 32px title, generous writing area, 16/26px body. No unsupported WYSIWYG toolbar, scheduling, revision history, slug, SEO settings or autosave claims. Topics are compact labelled chips with an add field. Current validation allows word characters only: present examples such as Design and Development, no spaces or punctuation. Title minimum is 3 characters; body is a string with no documented minimum. Creation defaults to PRIVATE. Use user-facing labels “Private” and “Public”; annotate the intended meanings in the design, but do not claim current security enforcement.

Save must include the chosen visibility rather than assuming the dedicated visibility endpoint is reliable. PATCH currently has no success response in the inspected handler. This brief describes interaction intent, not a proposed API fix. Updating another admin’s post also changes its author to the current admin in the source: flag for product resolution before offering unrestricted editorial reassignment.

Media attachments: show a separate future concept in the wireframes, not an active launch control. Upload is limited to four files per request, but validation of returned names and serving location are inconsistent. Do not promise file-size limits, supported media formats, alt-text persistence, a media library or deletion from storage.

## Users and comments
The users screen manages existing accounts. The API supports only ADMIN and USER roles. A role change dialog names the user and explains the destination role; avoid an instant toggle. A successful response is required before changing the badge. Self-demotion and deleting the final admin require a product policy; do not pretend the API already protects those cases.

Name/email are read-only for another user's detail. Verification is informational; no “mark verified” action exists. Associated posts and comments are context lists. Comments cannot be moderated by an admin unless they are the admin’s own comments. Do not show “Approve”, “Spam”, “Ban”, “Suspend” or “Delete any comment”. User deletion may fail when related records exist; describe the failure without inventing cascade deletion or undo.

## States and responsive behavior
Skeleton table on load; “No posts yet” with New post for a true empty collection; “No matching posts” with Clear filter for filtered emptiness. Distinguish a failed request from an empty collection. Save errors retain all inputs. Network uncertainty after an action should say “Could not confirm the change” rather than claiming success. No fake success toasts for hanging requests.

1440px frames: 232px sidebar, 40px main gutters, 24px column gap. Editor approximately 2:1 main-to-settings split. At 768px collapse sidebar to a drawer and stack settings below editor when necessary. At 390px header is 64–72px, gutters 20px, posts and users become labelled cards, drawers become full-screen pages. Save can use a bottom action bar with content clearance so it never obscures the last field. Dialogs max 480px desktop, 20px edge margins on mobile.

## Review criteria
An admin can distinguish stored versus unsaved content, identify public/private status, and understand exactly which destructive action is being confirmed. Every screen remains usable on mobile. The design contains only source-backed actions or clearly labelled future concepts. Visibility enforcement, identity resolution and media handling remain launch dependencies, not completed functionality.
