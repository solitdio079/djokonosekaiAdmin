# Source-backed API → design map

Inspected 11 September 2026. Base hostname remains unverified. Paths below are mounted paths in `src/app.ts`; this is descriptive documentation, not executable code. Source root: `/Users/djokokeita/repos/API/djokoNoSekai`. Routes, controllers, validators, middleware and Prisma schema were read. No endpoints were mutated.

## Endpoint inventory
| Method and path | Observed access / behavior | Design destination |
|---|---|---|
| POST /auth/signup | Public; name/email/password/confirmPassword; creates USER; success message | C05 |
| POST /auth/login | Public; email/password; token response with 6-hour expiry | C04, A01 |
| POST /posts/media | Before JWT middleware; up to 4 multipart media files; returns filenames | Future A04 attachments |
| GET /posts/:postId | Public; returns post and comments; no status filter | C03, A04/A05 |
| GET /posts/:postId/comments | Public; flat comments for post | C03, A06 |
| GET /posts | JWT + ADMIN; all posts, no query filtering/paging | A02/A03 |
| POST /posts | JWT + ADMIN; title/content/status/mediaString/topicString | A04 create |
| PUT /posts/:postId | JWT + ADMIN; validated post fields; changes author to current admin | A04 edit |
| PATCH /posts/:postId | JWT + ADMIN; status; handler does not send success response | Visibility concept; unresolved |
| DELETE /posts/:postId | JWT + ADMIN | A03/A04 confirmation |
| POST /comments | JWT; content and postId | C03 |
| PUT /comments/:commentId | JWT + author ownership; content and postId validation | C03/C07, own A06 |
| DELETE /comments/:commentId | JWT + author ownership; admin has no bypass | C03/C07, own A06 |
| GET /users | JWT + ADMIN; password omitted | A02/A07 |
| GET /users/:userId | JWT; self or ADMIN | C06, A08/A09 |
| GET /users/:userId/posts | JWT; queried user’s posts; no self/status check in handler | A08; no public author page |
| GET /users/:userId/comments | JWT; queried user’s comments; no self check in handler | C07, A08 |
| PUT /users/:userId | JWT + self; name/email/optional password; email change clears verification | C06, A09 |
| PUT /users/role/:userId | JWT + ADMIN; ADMIN or USER | A08 |
| DELETE /users/:userId | JWT + ADMIN | A08 confirmation |
| GET /users/sendEmailVerify/:userId | JWT + self; sends email; password query flag selects password-link message | C08/C09, A09 |
| POST /users/verifyEmail/:userId | JWT + self; verifies token and marks email verified | C08, A09 |
| PATCH /users/password/:userId | JWT + self; token/password/confirmPassword | C09, A09 |
| GET / | JWT because mounted after authentication; greeting only | No dedicated UI |

## Data shaping the design
Post: ID, title, nullable content, author ID, status PRIVATE/PUBLIC, separate published boolean, media array, topics array, created and updated timestamps. Comment: ID, content, post ID, author ID and timestamps. User: ID, email, nullable name, verified, ADMIN/USER role and timestamps; never show password data. The UI should use status as the proposed visibility control, while the separate published flag needs clarification. Do not show both as independent switches.

## Known constraints and design consequences
1. **Public discovery missing.** GET /posts is admin-only. C01 and C02 are intended-state designs, not currently supported public data flows. No search, pagination, topic catalog, featured flag or dedicated analytics endpoint exists. Admin filtering/counts may derive from loaded lists; do not imply server search or scale guarantees.
2. **Privacy not enforced by public reads.** GET /posts/:postId and its comments do not check PRIVATE/PUBLIC. User-post listing also lacks status filtering. “Private” is an intended experience; hiding a card in the UI is not security. Public launch and confidential drafts require backend resolution.
3. **Status completion missing.** updateStatus changes the record but does not send a success response. The status-only action cannot be presented as verified. The full post update accepts status, but neither route establishes correct public-read protection.
4. **Identity handoff incomplete.** Login returns token and message, not a user profile. Token payload includes user ID; there is no /me route. The design needs a trustworthy self-profile/role resolution step before deciding between admin and client navigation. Token decoding alone must not be treated as authorization.
5. **Media inconsistent.** Upload names contain hyphens and an extension; mediaString validation permits only word characters separated by commas. Upload writes ../public while static serving uses public relative to the working directory. No file-size/type policy is evident. Keep launch designs text-led; uploaded previews do not prove a post attachment will save or load.
6. **Comment moderation limited.** Only authors may edit/delete their comments. No global comments list, report/approve/spam/reply functionality exists. Public comment responses contain author IDs, not joined display names; public user profile access is unavailable.
7. **Password recovery is authenticated.** The email sender accepts a password query flag but still requires the current signed-in user; callback update also requires authentication. Do not promise anonymous forgotten-password recovery.
8. **Email callbacks need final routing.** Source email links use verifyEmail/token=… and newPassword/token=… appended to CLIENT_LINK. Account handoff should define matching pages and preserve callback context; production CLIENT_LINK and live routing were not inspected.
9. **Post editing behavior needs clarity.** Updates assign current admin as author. Empty media/topic strings fail validation and absent values preserve existing arrays, so “remove every attachment/topic” is not a guaranteed save behavior. There is no revision history or undo.
10. **Errors differ from conventional status semantics.** Validation can return HTTP 500; missing post can return a message with HTTP 200; several comment auth errors have misleading copy. User-facing error wording should be based on the action/context, not copied verbatim from backend text.
11. **Deletion has no recovery contract.** No recycle bin/cascade policy is exposed. Related records can prevent deletion. Confirmation copy must not promise permanent cleanup of all related objects or an Undo action.
12. **Verification is informational today.** Email changes reset verified; registration does not automatically sign in or automatically send a verification link. No verified-only feature gating is present.

## Evidence files
- `src/app.ts`: route mounts and authentication order.
- `src/routes/auth.ts`, `post.ts`, `comment.ts`, `user.ts`: endpoint/access wiring.
- `src/controllers/auth.ts`, `post.ts`, `comment.ts`, `user.ts`: actual behavior and responses.
- `src/validation/validators.ts`: field requirements and topic/media limits.
- `src/utils/multerUpload.ts`, `passportLocal.ts`, `verifyIfAdmin.ts`, `authorCheck.ts`: upload/login/permission details.
- `prisma/schema.prisma`: entities, relations and enums.

These findings are design dependencies, not requested backend fixes. No API implementation, configuration or credentials were changed.
