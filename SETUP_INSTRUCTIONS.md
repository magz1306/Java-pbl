# Setup Instructions

## 1. Extract this zip
Extract it to your Desktop, next to (not inside) your existing `leadpipeline` and `B2BLeadPipeline` folders. You should end up with a new folder called `leadpipeline2`.

## 2. Copy the Maven wrapper files
This project needs three small files that let you run `.\mvnw` without installing Maven separately. Copy them from your **existing** `leadpipeline` project (the one you already built) into this new `leadpipeline2` folder:

From:
```
Desktop\leadpipeline\leadpipeline\mvnw
Desktop\leadpipeline\leadpipeline\mvnw.cmd
Desktop\leadpipeline\leadpipeline\.mvn\   (the whole folder)
```

To:
```
Desktop\leadpipeline2\mvnw
Desktop\leadpipeline2\mvnw.cmd
Desktop\leadpipeline2\.mvn\
```

Easiest way: open both folders side by side in File Explorer, select those three items in the old project, copy, paste into the new one.

## 3. Open in VS Code
Open a **new** VS Code window (`Ctrl+Shift+N`), then File → Open Folder → select `leadpipeline2`.

## 4. Database
No changes needed. This project connects to the exact same MySQL database (`b2b_lead_pipeline`, port 3307) you already have running — it just uses two new tables (`leads2` and `sales_reps2`) so it never touches your existing data from the first project.

## 5. Run it
Open a terminal in VS Code (`` Ctrl+` ``), confirm you're in the `leadpipeline2` folder (check with `dir pom.xml` — it should show the file), then run:

```
.\mvnw spring-boot:run
```

Wait for "Started LeadPipeline2Application" with no red ERROR text.

**If it says port 8080 is already in use:** your first web app project is probably still running in its own terminal. Either close that terminal/stop that app first, or run this project on a different port by adding this line to `src/main/resources/application.properties`:
```
server.port=8081
```
and then open `http://localhost:8081` instead.

## 6. Open in browser
```
http://localhost:8080
```
(or `:8081` if you changed the port)

## What's New in This Version
Compared to the first web app, this one adds:
- **Editable deal value** directly in the leads table (type a new number, click Save)
- **Stage dropdown** on each lead row — change NEW/CONTACTED/QUALIFIED/WON/LOST directly, no separate form
- **Assign to Rep dropdown** on each lead row — pick any sales rep, or "Unassigned"
- **View Performance button** on each rep row — shows their assigned leads and total pipeline value

Everything else (Priority Score, Analytics, Overdue Follow-ups) works the same as before.
