# Issue Templates - Markdown Format

This directory contains markdown versions of the GitHub issue form templates. These templates are designed to be used with CLI tools, APIs, or Raycast to create issues in other repositories.

## Available Templates

- **bug.md** - Report something that is broken or incorrect
- **feature.md** - Create a parent feature issue that tracks tasks and research
- **research.md** - Investigate unknowns before implementation
- **task.md** - Create a single, implementation-sized unit of work

## Usage

### Using GitHub CLI

```bash
# Create a bug report
gh issue create --repo owner/repo --template issue-templates-md/bug.md

# Or copy the template and fill it out
cat issue-templates-md/bug.md | gh issue create --repo owner/repo --body-file -
```

### Using with Raycast

1. Copy the contents of the desired template
2. Use Raycast's GitHub extension to create a new issue
3. Paste the template into the issue body
4. Fill in the required fields

### Using GitHub API

```bash
# Example using curl
curl -X POST \
  -H "Accept: application/vnd.github.v3+json" \
  -H "Authorization: token YOUR_TOKEN" \
  https://api.github.com/repos/owner/repo/issues \
  -d @- <<EOF
{
  "title": "bug: Your issue title",
  "body": "$(cat issue-templates-md/bug.md)",
  "labels": ["type:bug"]
}
EOF
```

### Manual Usage

Simply copy the template content and paste it into a new issue in any repository.

## Template Structure

Each template includes:
- **Front matter** - Metadata including name, description, title prefix, and labels
- **Sections** - Organized fields matching the YAML form structure
- **Comments** - Guidance on what to include in each section
- **Checklists** - Where applicable, for tracking completion

## Why Markdown Versions?

The YAML issue forms (`.github/ISSUE_TEMPLATE/*.yml`) are used by GitHub's web interface to create structured issue forms. However, these YAML forms are not supported when creating issues via:
- GitHub CLI (`gh`)
- GitHub REST API
- Third-party tools like Raycast
- Other automation tools

These markdown templates provide the same structure in a format that works with all issue creation methods.
