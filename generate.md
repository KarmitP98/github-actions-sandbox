Generate a GitHub Actions workflow YAML file with the following requirements:

1. **Trigger Conditions:**
   - The workflow runs on `pull_request` events with types: `opened`, `edited`, `reopened`, and `synchronize`.
   - The PR must have its target branch as `integration`.
   - If the source branch name contains `-to-int` or `for-int`, do nothing (exit successfully).

2. **Action Behavior:**
   - When triggered, the action must use GitHub API (gh CLI or actions/github-script) to:
     - Collect all PR metadata: title, description (body), labels, assignees, and reviewers.
     - Automatically create a new PR from the same source branch to the `development` branch with the same:
       - Title
       - Body/description
       - Assignees
       - Labels
       - Reviewers (if possible)

3. **Additional Requirements:**
   - Use `actions/checkout@v3` to access the repo if needed.
   - Prefer `actions/github-script` for interacting with the GitHub API.
   - Ensure the workflow does not create duplicate PRs if one already exists from the same branch to `development`.
   - Add comments in the YAML file explaining each step.

Output only a **single `.github/workflows/pr-to-development.yml` file**, with clean, production-ready YAML.
