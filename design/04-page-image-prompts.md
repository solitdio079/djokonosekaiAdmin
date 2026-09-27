# Per-page image production

Each page gets its own image containing desktop and mobile versions of that same page. Generated with the built-in image tool. These prompts are saved for reproducibility.

## Shared direction

Use case: ui-mockup. Create ONE polished page design image, landscape 1536x1024 or larger. Exactly TWO views of THE SAME PAGE: a wide DESKTOP view on the left occupying about 72% width and a narrow MOBILE view on the right. Both must show the same page, content and state, responsively adapted. Not a multi-page collage. No physical devices or perspective. Small page title outside the views, with Desktop and Mobile captions. Use the attached image ONLY as aesthetic reference, not its multi-page composition. Brand exact lowercase word djokonosekai. Faithful Bysolitdio styling: flat solid #080909 canvas, #111313 surfaces, #eef8f7 text, #aaaead metadata, thin #2a2d2c dividers, flat #e35f21 orange primary buttons with #111111 text, #faab05 gold accents. Space Grotesk headings, Inter body. Square corners, generous editorial spacing, no gradients or glow. One dominant primary action, secondary actions outlined, destructive actions red outline. Readable text. No photographs, likes, bookmarks, newsletter, notifications, imaginary statistics, or extra navigation. User-facing screens must not show technical API notes; dependency notes belong only in tiny captions outside screen frames. This is a raster design, not code.  IMPORTANT: follow the page-specific navigation exactly, no extra Sign in on signed-in pages. No inferred extra buttons. Desktop and mobile must use the identical state and same text. Do not write pixel dimension captions; simply Desktop and Mobile.

## A01-sign-in — Admin sign in

Admin login page WITHOUT sidebar. Wordmark djokonosekai, small gold ADMIN. Centered form heading Sign in to your workspace. Labelled Email and Password with Show; orange Sign in. Secondary Back to journal. Mobile same. No registration, forgot-password, social login or metrics.

## A02-overview — Overview

Admin shell: left 220px sidebar wordmark djokonosekai, gold ADMIN, Overview selected, Posts, Users, My account, Sign out bottom. Main heading Overview, orange New post. Three modest count cards Public posts 8, Private posts 3, Users 12. Recent posts table Title Status Updated with three realistic stories and September 2026 dates. Mobile sidebar becomes Menu header; count cards compact and recent posts labelled cards. Only content counts, no charts or percentages. External caption: Sample data; counts derived from loaded records.

## A03-posts — Posts

Admin sidebar Overview, Posts selected, Users, My account, Sign out. Main Posts heading, orange New post. All/Public/Private tabs. Table Title Status Updated Actions, three rows Building with intention PRIVATE; Small details. Lasting impact. PUBLIC; Designing a quieter web PRIVATE. September 2026 dates, secondary Edit per row. Mobile labelled stacked cards with same content/tabs and New post. No views, metrics, schedule or search promises.

## A04-editor — Post editor

Admin sidebar Posts selected. Main heading Write a post. Title field Building with intention, large plain-text Body textarea with three short paragraphs. Settings column on right: Visibility radios Private SELECTED and Public; Topics chip Design and Add topic field. Orange Save post, outlined Preview. No media panel, rich text toolbar, autosave, schedule or author assignment. Mobile settings stack BELOW title and body; all controls visible. External note: Private visibility requires API correction; creation defaults to Private.

## A05-preview — Post preview

Admin sidebar Posts selected. Top thin gold-outlined Preview — unsaved changes banner, outlined Back to editor. Reader-like title Building with intention, DESIGN label, date, three paragraphs in narrow reading column. No editor controls or publish button. Mobile Menu header and same preview banner/title/body/back link. No public navigation or comments composer.

## A06-post-comments — Post comments

Admin sidebar Posts selected. Back to post link. Heading Post comments, context Building with intention. Two flat comments, Member #12 date and thoughtful sample text; Member #18 date and short sample text. These belong to other members, so no edit/delete/reply/approve/spam actions. Mobile same list. Empty space should be intentional. External caption: Other members’ comments are read-only in the current API.

## A07-users — Users

Admin sidebar Users selected. Heading Users, subheading Accounts in your community. Table Name Email Role Email status, three users Alex Tan alex@example.test ADMIN Verified; Jamie Park jamie@example.test USER Verified; Taylor Kim taylor@example.test USER Unverified. View details secondary row links. Mobile three labelled cards containing same four fields. No invite, new user, suspend, filter icons without function, or inline destructive controls.

## A08-user-detail — User details

Admin sidebar Users selected. Back to users. Heading Taylor Kim, member details Name Taylor Kim and Email taylor@example.test read-only text; Unverified status; Role dropdown USER selected with ADMIN alternative. Orange Save role. Secondary Posts and Comments tabs below, Comments selected with one short sample comment and post context. Separate red-outline Delete user button at bottom. Mobile same full-page details. No edit name/email, verify button or suspension. No confirmation dialog yet.

## A09-my-account — My account

Admin sidebar My account selected. Heading My account. Name Alex Tan and Email alex@example.test labelled editable fields, orange Save changes. Verified green text badge with icon. Secondary Password link and Sign out link. Mobile Menu header, same form and badge. No avatar uploader, third-party connections or delete account.

## A10-delete-confirmation — Delete confirmation

Admin sidebar Posts selected, posts list dimmed behind accessible centered confirmation dialog. Dialog title Delete this post? Body: Building with intention will be deleted. This action cannot be undone. Outlined Cancel, red filled Delete post with DARK text readable. Desktop modal 480px; mobile same dialog with 20px screen margins and stacked buttons, same dimmed posts screen behind. No success state or unrelated dialogs. External caption: Confirmation concept; deletion can fail when related records exist.

