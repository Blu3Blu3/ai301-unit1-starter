---
name: issue-rubric
description: The rubric to which a candidate open-source issue is graded against in terms of viability and worthiness as a first open-source contribution. Used when evaluating a GitHub issue URL or an eval snapshot file as a potential first issue.
---

# Rubric: is this a good first issue?

The following checks to use in grading a candidate open-source issue. Their format is:

- *Check*: A short name used as an attribute in the output JSON.
- *Evidence*: What to look at and where it's located; this is the source (repo-facts block, issue body, comment thread, or the locations in references/evidence-guide.md). Valid sources would be things like "the last 5 recent commits", not "the repo" or "commits about 'x' feature".
- *Pass condition*: A condition to apply to the check, probably written by someone else. Prefer thresholds with numbers ("a maintainer commented within 30 days") over adjectives ("maintainer is responsive").
- *Weight*: `required` (a fail here rejects the issue) or `preferred` (never changes the verdict, but helps in improving an issue's spot in your ranking).

## Checks

| Check | Evidence | Pass condition | Weight |
| --- | --- | --- | --- |
| ai-allowed | Any AI-use policy file in the repo that addresses AI or agent contributions; Repo facts: contribution policy line(s); Issue section: body, tags about AI use permissions | Pass if no such policy file exists, or if the file permits AI-assisted contribution with or without stated conditions. Fail if any file, or line in the repo facts, disallows AI use for contributions. | required |
| issue-unclaimed | Repo facts: open issues and "PR"/"pull request" states; Comments section | Pass if nobody is currently assigned, no linked pull request is open, and no comment in the Comments section has claimed the PR within the past 60 days. Fail otherwise. | required |
| issue-unplanned | Repo facts: open issues and "PR"/"pull request" states; Issue section: submission checklist, body; Comments section | Pass if the issue is not currently in a planned feature timeline or is otherwise noted as being looked at or worked on by the maintainer. If unclear, pass only if similar issues have been mentioned as already checked. Fail if the issue is explicitly stated to be worked on currently. | required |
| maintainer-alive | Repo facts: author names in "last 5 default-branch commits"; the author_association of each comment in the Comments section | Pass if at least 1 of the last 5 commits is by a non-bot author (username not ending in `[bot]`) OR an Owner, Member, or Collaborator commented in the thread. Fail if all 5 commits are bot-authored and no maintainer commented. | required |
| scope-suitable | Issue section: title, body; Comments section | Pass if the issue is labeled with a tag or other mention of being "good first issue", "easy", or similar labels about being suitable for a first PR to take on. If unclear, pass only if the issue body describes an observed/desired behavior of the program, and no maintainer says a key input or decision for a plan of action is still open (e.g., "TBD", "maybe"). | required |
| scope-pulled | Repo facts: most recent pull requests, linked PRs; Issue section: title, body | Pass if, out of the 5 most recent pull requests, there are less then 2 closed-unmerged linked pull requests, or one or less closed-unmerged linked PRs dated within the last 6 months of the captured date. If a closed PR has no date, disregard it. | required |
| scope-focused | Issue section: title, body | Fail if the issue is an umbrella, tracking, or "megaissue" list, or asks for changes spread across unrelated areas of the codebase. Pass a batch of same-kind changes in one area (several docs pages, several similar previews, several causes of one bug) as a single task. Pass otherwise. | required |
| repo-alive | Repo facts: "archived:" on the repo line, and the dates in "last 5 default-branch commits", compared with the capture date | Pass if the repo is not archived AND the newest of the last 5 default-branch commits is within 60 days of the capture date. | required |
| maintainer-responsive | Repo facts: "maintainer first-response sample" (days to first owner/member/collaborator comment on 5 recently updated issues) | Pass if at least 3 of the 5 sampled issues got a comment from the maintainer first, and those comments were made within 120 days. Fail otherwise. | preferred |
| scope-language | Repo facts: "description" line, and any language list or README text in the bundle | Pass if the repo uses fewer than 5 languages AND at least 1 is a common programming language (e.g., Python, C++, Java). If no languages are mentioned, allow this to pass.| preferred |
| comments-punctual | Repo facts: "maintainer first-response sample" | Pass if at least 3 of the 5 sampled issues got a first maintainer comment within 30 days. | preferred |

## Verdict rule

Accept an issue only if every required check passes. Reject if any required check fails or is unclear. Preferred checks never change the verdict; they only rank accepted issues. If a preferred check is unclear, count it as a pass.

