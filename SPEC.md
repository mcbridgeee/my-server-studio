# Lesson 01 specification

## STUDIO-001 · Launch a tested calculator on an existing server

**Status:** New launch running and verified; learner keep decision recorded.
**Next step:** Review excerpts, then PR, CI and issue closure.
**Instructor implementation:** [issue #9](https://github.com/kaw393939/373_hosting/issues/9).
Create your own issue from the [lesson template](.github/ISSUE_TEMPLATE/studio-calculator.md).

## Agreed result

Launch the supplied published calculator image through your existing Traefik
network and a nonconflicting HTTPS hostname. Preserve unrelated services and
host access. Do not add another proxy/updater or build a substitute image.
The [release selection](studio/calculator-release.json) supplies the expected
commit and multi-platform digest independently of the running website.
An explicitly agreed adoption of a matching existing deployment is recorded
as adoption, not a fresh launch. This bounded lesson does not certify the whole
server baseline or a vulnerability-free image.

- **Public hostname:** `https://studio.bmctiernan.com` (new Porkbun A record to
  the existing droplet).
- **New launch or adopted deployment, and reason:** New launch. `bmctiernan.com`
  and `calc.bmctiernan.com` route to the learner's own `mcbridgeee/is373-ci-cd`
  image (learner-reported), so neither matches the pinned release or can be adopted. Pre-launch
  `doctor` reported `ready` / `launch-new`.
- **Own issue / feature branch:** [issue #1](https://github.com/mcbridgeee/my-server-studio/issues/1)
  / `studio-001-calculator`.
- **Agreed scope or actual access/configuration gap:** One pinned image
  (`studio/calculator-release.json`) in Compose project `is373-studio-calculator`
  on the existing `hosting-web` Traefik network. Preserve the apex, calc, quiz,
  qa, www and report sites and the existing `is373-ci-cd` app. Gap: Docker
  requires sudo for the non-root SSH user, so sudo steps run in the learner's
  own terminal.

Private SSH targets and configuration stay in ignored local state. Share only
reviewed, selected evidence; never commit credentials or raw server output.

## Evidence to keep

| Evidence | Actual result / link |
|---|---|
| Prepared Black/Pylint/pytest and real-image browser checks | Passed locally 2026-10-27 with local Docker: Black, Pylint, 91 pytest, 2 E2E. PR CI pending |
| Hosted image/commit, trusted HTTPS, valid and rejected API cases | Passed at new launch 2026-10-27T20:43Z: digest and commit match, trusted HTTPS, 6 × 7 = 42, ÷0 → 400, numeric string → 422. [evidence.json](studio/evidence.json) |
| Preservation of unrelated services | 7 existing containers unchanged (identity, state, published ports); not a whole-host audit |
| Own prediction, check interpretation, browser observation and keep/revise reason | [LEARNING.md](LEARNING.md), all four recorded; assistance disclosed |
| Accuracy review before publishing learner excerpts | Learner reviewed 2026-10-27; see [LEARNING.md](LEARNING.md#review) |
| Actual PR, latest CI, merge and issue closure | Pending |

Link the exported `studio/evidence.json`, actual CI and issue/PR when available.
CI does not deploy this server. A fixture, green check, timestamp, closed issue
or AI assertion alone does not establish the full result. `status` reports
recorded evidence and readiness for instructor review; it does not grade,
certify authorship or establish understanding.

## Optional instructor history

The records below are background, not steps to repeat. Their original anchors
remain here so earlier links continue to work.

## HOST-001 · Keep the Traefik dashboard private

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-001--keep-the-traefik-dashboard-private).

## HOST-002 · Controlled host maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-002--controlled-host-maintenance).

## HOST-003 · Companion image security maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-003--companion-image-security-maintenance).
