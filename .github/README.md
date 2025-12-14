# GitHub Project Board Setup

This directory contains the configuration for the DevOps Capstone Project Kanban board.

## Kanban Board Columns

The project uses a standard Kanban workflow with the following 7 columns:

1. **New issues** - Newly created issues that need to be triaged
2. **Icebox** - Ideas and future enhancements that are not currently prioritized
3. **Product backlog** - Prioritized features and tasks ready for sprint planning
4. **Sprint backlog** - Tasks committed for the current sprint
5. **In progress** - Tasks currently being worked on
6. **Review/QA** - Tasks under review or quality assurance testing
7. **Done** - Completed tasks

## Setting Up the Project Board

To create the project board with these columns:

### Using GitHub Web Interface

1. Go to the repository on GitHub
2. Click on the "Projects" tab
3. Click "New project"
4. Choose "Board" template
5. Name it "DevOps Capstone Project Kanban Board"
6. Create the following columns in order:
   - New issues
   - Icebox
   - Product backlog
   - Sprint backlog
   - In progress
   - Review/QA
   - Done

### Using GitHub CLI

You can also create the project board using the GitHub CLI (gh):

```bash
# Create a new project (replace REPO_ID with your repository ID)
gh api graphql -f query='
  mutation {
    createProjectV2(input: {
      ownerId: "REPO_ID"
      title: "DevOps Capstone Project Kanban Board"
    }) {
      projectV2 {
        id
      }
    }
  }
'
```

Then add the columns using the project ID returned from the above command.

## Workflow

Issues should flow through the board as follows:

```
New issues → Icebox/Product backlog → Sprint backlog → In progress → Review/QA → Done
```

- **New issues** serves as the entry point for all new items
- Items can be moved to **Icebox** if they're not currently prioritized
- **Product backlog** contains prioritized items ready for sprint planning
- During sprint planning, items move from Product backlog to **Sprint backlog**
- Active work moves items to **In progress**
- Completed work moves to **Review/QA** for testing and code review
- After approval, items move to **Done**
