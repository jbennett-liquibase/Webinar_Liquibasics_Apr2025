<p align="left">
  <img src="img/liquibase.png" alt="Liquibase Logo" title="Liquibase Logo" width="324" height="72">
</p>

# 👋 Welcome to Liquibase!
This repository contains the demo scenario for the "Liquibasics" webinar originally delivered on April 24th, 2025. Recordings of all webinars can be found [here](https://www.liquibase.com/videos).

# 🔧 Demo Requirements
Liquibase Pro is a java based application with [minimal requirements](https://docs.liquibase.com/start/install/liquibase-requirements.html).

A Pro key is required to utilize Liquibase Flows. A temporary key is provided for webinar attendees in the [liquibase.properties](liquibase.properties) file.

If you need a new Pro key, you can request one [here](https://www.liquibase.com/trial).

# ✔️ Pre-Demo Steps
1. Clone this repository
    * [Instructions](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)
1. Download and install Liquibase CLI
    * [Installation Link](https://www.liquibase.com/download)
1. Open a command prompt (Windows) or terminal (Linux/Mac) and start an [H2 Database](https://contribute.liquibase.com/extensions-integrations/directory/database-tutorials/h2/)<br>
  H2 is a temporary in-memory database suitable for testing
    ```
    liquibase init start-h2
    ```
    *Safe to close browser window but leave command prompt/terminal open*
# 📋 Demo Steps

1. Command/Terminal Prompt<br>
    Open a new command prompt/terminal window and change to the folder were the repository was cloned.
1. Status Command<br>
    The status command allows us to view pending database changes.
    ```
    liquibase status
    ```
    The output should look similar to this:
    ```
    4 changesets have not been applied to TEST@jdbc:h2:tcp://localhost:9090/mem:dev
    changelog.xml::ddl_create_table_organizations::jbennett
    changelog.xml::dml_insert_data_organizations::jbennett
    changelog.xml::ddl_create_table_addresses::jbennett
    changelog.xml::ddl_create_constraint_addresses::jbennett
    Liquibase command 'status' was executed successfully.
    ```
1. Flow Command<br>
Liquibase workflows allow you to define a standard set of deployment steps for your database changes. In this way you can always ensure your deployments are done consistently following your best practices, regardless of automation tool or database platform.
    ```
    liquibase flow --flow-file=developer.flowfile.yaml
    ```
    The flow will run several Liquibase commands. At the end, you should see this:
    ```
    Liquibase command 'flow' was executed successfully.
    ```
    🎉 Congratulations!!! You have deployed your first set of database changes with Liquibase!

1. New Release<br>
Liquibase tracks all database changes it deploys. Lets deploy some additional changes as part of a new release. In the [changelog.main.xml](changelog.main.xml) file, remove lines 58 and 79 and save the file. Then we'll run our flow again.
    ```
    liquibase flow --flow-file=developer.flowfile.yaml
    ```
    As before, the flow will run several Liquibase commands. At the end, you should see this:
    ```
    Liquibase command 'flow' was executed successfully.
    ```
    The history command, run at the end of the flow, displays all the database changes Liquibase has deployed. Notice we have two deployments now: four changes from step three and two changes from our our most recent deployment.
1. 🎉 Congratulations!!!<br>
    This concludes the interactive demo. You can continue to experiment or simply close the command prompt/terminal windows.
1. 🌟 Bonus!!!<br>
    View the [operation reports](https://docs.liquibase.com/liquibase-pro/observability/operation-reports.html) Liquibase Pro creates. They will be named "Update-report-*.html" in the directory where Liquibase ran.

# 📒 Liquibase Documentation
* [Documentation Home](https://docs.liquibase.com/home.html)
* [Liquibase University](https://learn.liquibase.com/)

# 💡 Core Concepts
If you are unfamilar with Liquibase concepts, here is some information to get you started.

* [Changeset](https://docs.liquibase.com/concepts/changelogs/changeset.html): basic unit of database work
* [Changelog](https://docs.liquibase.com/concepts/changelogs/home.html): text file containing collection of changesets
* [Tracking tables](https://docs.liquibase.com/concepts/tracking-tables/tracking-tables.html): tables created and maintained by Liquibase

# ❓ Helpful Liquibase Commands
|Command |Description|Documentation
|----------|------------|------------|
| connect | Test database connection | [Link](https://docs.liquibase.com/commands/change-tracking/connect.html)
| flow | Execute a Liquibase workflow | [Link](https://docs.liquibase.com/commands/flow/flow.html)
| status | Show undeployed changes | [Link](https://docs.liquibase.com/commands/change-tracking/status.html)
| update | Run changes against target database | [Link](https://docs.liquibase.com/change-types/update.html)
| history | Show deployed changes | [Link](https://docs.liquibase.com/commands/change-tracking/history.html)
| rollback-one-update | Rollback the last or a specified update | [Link](https://docs.liquibase.com/commands/rollback/rollback-one-update.html)
| checks | Show or view policy checks | [Link](https://docs.liquibase.com/liquibase-pro/policy-checks/workflows/home.html)

# 🔦 Troubleshooting
* [Installation issues](https://docs.liquibase.com/start/install/liquibase-installation-troubleshooting.html)
* [Common issues](https://support.liquibase.com/hc/en-us/sections/27504481958555-Troubleshooting)
* [Liquibase University](https://learn.liquibase.com/catalog/info/id:127)

# ☎️ Contact Liquibase
* Liquibase sales: https://www.liquibase.com/contact

# ⭐ Thank you!
Thank you for evaluating Liquibase Pro! We hope to be a part of your DevOps journey.