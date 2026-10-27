# Lesson 01 · Conversation evidence

AI-drafted task summary, not a transcript or grade. It may be public. Use actual
short quotes or labeled paraphrases, name any help supplied, and link actual
work. Leave missing contributions Pending. A learner can review, correct or
remove excerpts before publication; accuracy approval is not proof of learning.
Label role-play honestly rather than treating it as an actual learner response.

**Lesson:** STUDIO-001. **Available conversation context:** This chat (Claude
Code desktop), 2026-10-27.

## Prediction

Made before this chat explained the plan; a separate Claude chat earlier gave
guiding questions only. Paraphrase: Porkbun DNS
(an A record) maps `studio.bmctiernan.com` to the droplet's IP; Let's Encrypt
supplies the certificate and the request is redirected to the secure port; the
request reaches `hosting-web`, and Traefik's "host rule picks" the container.
They expected it to route to an "apache site" and pointed to their own
report.bmctiernan.com as where the path is outlined.

AI comparison afterward: the DNS, HTTPS and Host-rule steps match the plan.
Two points were clarified: the target is the calculator container itself, not
an Apache site, and Traefik reuses a stored certificate rather than getting a
new one for each request.

## Check interpretation

Check shown: launch API case `{"a": 6, "b": 0, "operation": "divide"}`,
expected HTTP 400, actual 400. Learner mapped a/b/operation to the form's two
number boxes and operation menu, and said it "establishes my calculator also
checks to see if the math is possible"; what it leaves open: "it wouldn't tell
me if it can actually correctly do the math". They expected a 400 to "crash the
entire page".

AI follow-up: this check called the API directly, not through the form, so it
leaves the browser journey open; a 400 is a deliberate answer, not a crash; the
separate 6 × 7 case returning 42 covers one correct calculation.

## Browser observation

Learner, in their own browser at https://studio.bmctiernan.com: 6 × 7 showed
42 for both the browser (JavaScript) result and the API result. 6 ÷ 0 showed
"a - for browser result from javascript, and a - for the python fastapi check",
with "Cannot divide by zero." in red at the bottom.

Classroom comparison (lesson step 1, done late): learner said the classroom
calculator at calc.mywebclass.org "looks the exact same". AI check: both report
commit `4600202`, but calc.mywebclass.org resolves to a different server
(159.203.182.71), so the difference is where it runs, not how it looks.

## Keep decision

Keep. Reason, from their browser test: "everything seems to be working just fine
for me." Possible later revision: "make it cuter to fit the rest of my site, and
use lowercase". That is a design change to the app, outside this fixed-image
lesson, so it fits a later app studio lesson rather than a revision here. They
first said they didn't understand what they would change or why, and AI
explained what a keep/revise decision is.

## Review

2026-10-27: learner read the full LEARNING.md, the SPEC.md changes and
studio/evidence.json and said "all those md are good to push and commit".
Accuracy review only, not proof of learning.

## Help received

Separate Claude chat, 2026-10-27 (as reported by the learner):

- reviewed the template and noted calc.bmctiernan.com runs my own image, so it
  couldn't be adopted; suggested a new hostname, and i chose studio.bmctiernan.com.
- explained my ssh command (my non-root user and the droplet's address) and that
  server-of-love is my repo name, not an ssh host.
- explained that sudo on the droplet uses the droplet account's password, not my
  mac's, and why `ssh -t` is needed to type it.
- explained that git over ssh moves code, while issues and prs need gh or the browser.

This chat (Claude Code):

- explained why docker needed sudo and how to list networks privately with `ssh -t`.
- explained why one-off `ssh host 'command'` closes the connection and why `-t` output staircases.
- compared my prediction with the plan (container not apache; certificate stored and reused).
- explained why the lesson issue and a feature branch come before launch.
- explained what an http status like 400 means and how the api check differs from the form.
- explained that the classroom and studio calculators run the same release on different servers.

## AI work and next step

AI ran setup, configure, plan and DNS lookups, drafted and posted
[issue #1](https://github.com/mcbridgeee/my-server-studio/issues/1) with the
learner's approval, and created branch `studio-001-calculator`. Learner ran the
sudo steps (network list, doctor, launch) privately after reviewing the plan.
AI exported [studio/evidence.json](studio/evidence.json) and ran the full local
`check` (Black, Pylint, 91 pytest, 2 E2E with local Docker; all passed). Learner
reviewed these excerpts; PR #2 merged after CI passed and issue #1 is closed.
