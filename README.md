# SCIP Website

Blogdown/Hugo site (R Markdown `.Rmd` sources under `content/`, knitted to
`.html`, built site in `docs/`). Edit the `.Rmd` files, not the `.html` next
to them or anything in `docs/` — those are generated output.

## Yearly conference-cycle pattern

`content/post/announcements.Rmd` and `content/post/conference.Rmd` both
cycle through the same two states each year, confirmed by git history
(`cc7bd85`, `b6f660b` did this swap for 2025):

1. **Call phase** (roughly July/August through the abstract deadline): a
   "### YYYY Conference Information" section with the Steering
   Committee/President-Elect nomination call, the submission-form link, the
   "Nth annual meeting... call for abstracts" paragraph (date, deadline,
   location, Psychonomic Society link), and the theme paragraph.
2. **Program phase** (once the program is finalized, historically mid/late
   November): that same section gets replaced with a `#### [Program](...)`
   link, `#### [Register and Pay Conference Fee](...)` link, and the
   registration pricing bullets/PayPal explanation. The nomination/CFA
   content is removed entirely, not appended.

Both files get updated together each time (same commits touch both). The
"### YYYY Student Award Information" section (Birnbaum Scholarship +
Castellan award) doesn't change between phases, just its year/deadline.

The `gmail_mailer/templates/` HTML email templates
(`submit_abstracts.html`, `submit_extension.html` = call phase;
`register_program.html`, `scip_thursday.html` = program phase) mirror this
same two-phase structure and should get the same content each cycle.

## 2026 status (as of 2026-08-12)

Both pages are currently in **call phase** with 2026 info filled in:
- 56th annual meeting, Thursday November 19, 2026
- Abstract deadline September 15, 2026
- San Diego, in tandem with the Psychonomic Society meeting
  (`psychonomic.org/page/2026annualmeeting`)
- Theme: "Scaling Up Cognition: Team Approaches to Cognitive Science"
- Submission form: `https://forms.gle/aFshQMiZEkgPHFpV9`
- Castellan award manuscript deadline: October 15, 2026

Note: the email templates (`submit_extension.html`) additionally say the
deadline was **extended to September 30, 2026** — the site pages here only
say September 15 (no extension announced on-site yet). Update both site
pages to mention the extension if/when that's actually announced.

### Still needed for the program-phase swap later this year

When the 2026 program is ready, swap both pages to program-phase content
(see pattern above) and update:
- Program doc link — currently still last year's Google Doc
  (`docs.google.com/document/d/1GZuYtkNH3Ex...`)
- Register/PayPal link (`hosted_button_id=D4PN39CWFS4NE`) — confirm still
  valid or needs a new button
- Registration pricing ($80 / $150 / $155) — confirm unchanged for 2026
- `register_program.html` email template also needs: late-breaking poster
  deadline (currently "November 10th", needs 2026 date) and poster
  submission form link (currently last year's Google Form)

## Mailing list signup

`content/subscribe.Rmd` and the "Subscribe to the Mailing List" section in
`content/post/announcements.Rmd` are a plain `mailto:` link to
compinpsych@gmail.com that pre-fills a subscribe request — this is a static
site with no backend to receive a form submission. When one of those emails
comes in, run `python3 add_subscriber.py <email>` in `gmail_mailer/` to add
them to `recipients.csv` — see that repo's README for details.
