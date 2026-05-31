# Development Timeline Dashboard

## Purpose

This Notion dashboard exists to show the portfolio development history at a glance.

It answers the following questions:

- What was developed?
- When did it start and end?
- Which feature or system does it belong to?
- What phase was it in?
- What is the current status?
- Which Markdown, PlantUML, Git commit, blog draft, and interview notes are connected?
- Can the user click one item and move to the full development context?

## Notion Pages

### Schedule Dashboard

```text
https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da
```

Role:

- Calendar planning
- Sprint planning
- Patch day / no development day management
- Reschedule history
- Development timeline dashboard

### Development Hub

```text
https://www.notion.so/3714bccaf9eb8020bc85e39638c56d7b
```

Role:

- Concept study
- Architecture design
- Implementation notes
- Core code summary
- Markdown / PlantUML links
- Blog draft
- Interview notes
- Weekly review

## Timeline Database

Database:

```text
Portfolio Development Timeline
```

URL:

```text
https://www.notion.so/fa259baed449460693fcdfbd2d0dc4b2
```

Data Source:

```text
collection://99f867b4-09cd-43c3-9f47-0b5e86cde399
```

## Views

### Development Timeline

```text
view://3714bcca-f9eb-81f5-b331-000cbf492a5e
```

Purpose:

- Shows each development item by start and end date.
- Used as the main visual schedule and history view.
- The user can click each item to open the full development summary.

### Timeline Table

```text
view://3714bcca-f9eb-81be-bb8c-000cd7ab8f10
```

Purpose:

- Shows all timeline records in a dense table.
- Useful for editing status, links, commits, risk, and KPI level.

### By Feature

```text
view://3714bcca-f9eb-812e-b61f-000cf1e71fa2
```

Purpose:

- Groups development items by feature area.
- Useful for checking whether Skill System, Skill Tool, Animation Tool, Shader Showcase, Optimization, Rendering Debug, Lua Scripting, Docs, and Automation are balanced.

## Database Schema

| Property | Type | Purpose |
| --- | --- | --- |
| Task | Title | Development item name |
| Feature | Select | Feature category |
| Phase | Select | Development cycle phase |
| Status | Select | Planned, In Progress, Blocked, Review, Done, Deferred |
| Start | Date | Start date |
| End | Date | End date |
| KPI Level | Select | Completion or maturity level from 0 to 5 |
| Development Hub | URL | Link to detailed Notion development page |
| Docs | URL | Link to Markdown document |
| PlantUML | URL | Link to PlantUML diagram |
| Git Commit | Rich text | Related commit hash or commit list |
| Calendar Event | URL | Related Google Calendar event link |
| Blog Draft | URL | Related Tistory blog draft |
| Interview Notes | URL | Related interview summary |
| Summary | Rich text | Short explanation of what was done |
| Risk | Select | Low, Medium, High |

## Initial Records

### Portfolio Documentation Foundation

Status: Done

Connected commits:

```text
a0f6342, 0128bf2, 66cf663
```

Page:

```text
https://www.notion.so/3714bccaf9eb81b88aaec4325f65af35
```

### MVP Scope and Learning Workflow

Status: Done

Connected commits:

```text
4b7cb37, 5187b73
```

Page:

```text
https://www.notion.so/3714bccaf9eb81878796dcf6f6955503
```

### Feature Toggle and Before/After Architecture

Status: Done

Connected commit:

```text
95e53af
```

Page:

```text
https://www.notion.so/3714bccaf9eb81469c52c1ca4804c725
```

### NY Module Naming Governance

Status: Done

Connected commits:

```text
73dee5a, 4ddfba7
```

Page:

```text
https://www.notion.so/3714bccaf9eb819caa7ce0cdfa06c3ca
```

### Selective Lua Scripting Layer

Status: Done

Connected commit:

```text
9832585
```

Page:

```text
https://www.notion.so/3714bccaf9eb810e96b4face76831b98
```

### Google Calendar and Notion Schedule Workflow

Status: Done

Connected commits:

```text
77630e9, 98fb355, 0777d4f
```

Page:

```text
https://www.notion.so/3714bccaf9eb813e81a1ee6af0ec5034
```

### Portfolio Automation Strategy

Status: Done

Connected commits:

```text
180bceb, dc52721
```

Page:

```text
https://www.notion.so/3714bccaf9eb819fb8a7eace8dcbf666
```

## Operating Rule

Every meaningful development item must be recorded in this database.

A record is valid only when it has at least:

- Task
- Feature
- Phase
- Status
- Start
- End
- Summary

When the work becomes explainable as a portfolio asset, also add:

- Docs
- PlantUML
- Git Commit
- Blog Draft
- Interview Notes

## Codex Update Rule

When Codex completes or plans a development item:

1. Update the Notion timeline database.
2. Link the item to the Development Hub when detailed notes exist.
3. Update the local Markdown docs.
4. Update `CODEX_WORK_MEMORY.md`.
5. Commit the documentation update.

## User Workflow

Use `Development Timeline` when you want to see the schedule visually.

Use `Timeline Table` when you want to edit metadata quickly.

Use `By Feature` when you want to check feature balance.

Click a timeline item to see:

- What was developed
- Why it was developed
- Related commits
- Related docs
- Related architecture notes
- Blog and interview follow-up
