# Git + Azure DevOps + GitHub Actions — Interview Guide
### Top 30 Questions Each (Simple English) + Ready Pipeline Templates

---

# SECTION 1: GIT — TOP 30 INTERVIEW QUESTIONS

**1. What is Git?**
Git is a distributed version control system. It tracks every change made to code, lets many developers work on the same project at the same time, and keeps full history so you can go back to any previous version.

**2. What is the difference between Git and GitHub?**
Git is the tool (software) that tracks versions on your computer. GitHub is a website/service that hosts Git repositories online and adds collaboration features like pull requests, issues, and access control.

**3. What is a repository?**
A repository (repo) is a folder that Git is tracking. It contains all your files plus the full history of changes (stored in a hidden `.git` folder).

**4. What is the difference between `git pull` and `git fetch`?**
`git fetch` downloads new data from the remote but does not change your working files. `git pull` = `git fetch` + `git merge` — it downloads AND merges the changes into your current branch.

**5. What is a commit?**
A commit is a saved snapshot of your project at a specific point in time, with a unique ID (hash), author, timestamp, and message.

**6. What is a branch?**
A branch is an independent line of development. It lets you work on a feature or fix without affecting the main code until you are ready to merge.

**7. What is the default branch usually called?**
`main` (older repos may use `master`).

**8. What is merging?**
Merging combines changes from one branch into another, creating a new commit that joins both histories.

**9. What is a merge conflict? How do you resolve it?**
A conflict happens when two branches change the same line(s) of the same file differently. Git cannot decide automatically, so you manually open the file, choose/edit the correct code, then `git add` and commit to mark it resolved.

**10. What is rebase? How is it different from merge?**
Rebase moves your branch's commits to sit on top of another branch, rewriting commit history to look linear (no merge commit). Merge keeps both histories and adds a merge commit. Rebase = cleaner history; Merge = safer, preserves true history.

**11. When should you NOT use rebase?**
Never rebase a branch that others have already pulled/shared — it rewrites history and will cause conflicts for everyone else.

**12. What is `git stash`?**
It temporarily saves your uncommitted changes so you can switch branches with a clean working directory, then bring the changes back later with `git stash pop`.

**13. What is the difference between `git reset` and `git revert`?**
`git reset` moves the branch pointer backward, removing commits from history (can be dangerous on shared branches). `git revert` creates a NEW commit that undoes a previous commit's changes, keeping history intact — safe for shared/public branches.

**14. What is `cherry-pick`?**
It applies one specific commit from another branch onto your current branch, without merging the whole branch.

**15. What is a detached HEAD state?**
When HEAD points directly to a commit instead of a branch. You can look around or test things, but any new commits made here can be lost if you switch branches without saving them to a new branch.

**16. What is the staging area (index)?**
It's a middle zone between your working files and your commit history. `git add` moves changes here; `git commit` saves what's staged into permanent history.

**17. What is `.gitignore`?**
A file listing file/folder patterns that Git should NOT track (e.g., `node_modules/`, `.env`, build outputs, secrets).

**18. What is a fork vs a clone?**
A clone is a full local copy of a repo you have access to. A fork is your own copy of someone else's repo on the server (e.g., GitHub), usually used for contributing to projects you don't own.

**19. What is a pull request (PR) / merge request?**
A request to merge changes from one branch into another, which triggers code review, automated checks, and discussion before merging.

**20. What are Git hooks?**
Scripts that run automatically at certain Git events (e.g., pre-commit, pre-push) — often used to run linting, tests, or block bad commits.

**21. What is `git blame`?**
A command that shows who last changed each line of a file, and in which commit — useful for tracking down when/why a bug was introduced.

**22. How do you undo the last commit but keep the changes?**
`git reset --soft HEAD~1` — moves the commit back but keeps your changes staged.

**23. What is squashing commits?**
Combining multiple small commits into one clean commit, usually done before merging a PR to keep history readable.

**24. What is the difference between `git diff` and `git status`?**
`git status` shows which files are changed/staged/untracked. `git diff` shows the exact line-by-line changes.

**25. What are tags in Git, and why use them?**
Tags are fixed pointers to a specific commit, usually used to mark release versions (e.g., `v1.0.0`). Unlike branches, tags don't move.

**26. What is a shallow clone?**
A clone with limited history (e.g., `git clone --depth 1`) — faster, used in CI/CD pipelines where full history isn't needed.

**27. What happens internally when you run `git commit`?**
Git creates a blob for each changed file's content, a tree object representing the folder structure, and a commit object pointing to that tree plus the parent commit.

**28. What is the difference between a fast-forward merge and a three-way merge?**
Fast-forward: target branch has no new commits since the source branched off, so Git just moves the pointer forward (no merge commit). Three-way merge: both branches have diverged, so Git creates a new merge commit combining both.

**29. How do you find which commit introduced a bug?**
`git bisect` — a binary search tool that helps you test commits between a known-good and known-bad point to isolate the exact commit that caused the issue.

**30. What is a submodule?**
A way to include one Git repository inside another as a subdirectory, keeping its own separate history — used when a project depends on another repo (e.g., a shared library).

---

# SECTION 2: AZURE DEVOPS — TOP 30 INTERVIEW QUESTIONS

**1. What is Azure DevOps?**
A Microsoft platform that provides tools for the full software delivery lifecycle: planning (Boards), source control (Repos), CI/CD (Pipelines), package management (Artifacts), and testing (Test Plans) — all in one place.

**2. What are the core services in Azure DevOps?**
Boards, Repos, Pipelines, Artifacts, Test Plans.

**3. What is the difference between Azure DevOps Server and Azure DevOps Services?**
Services is the cloud-hosted (SaaS) version; Server is the on-premises, self-hosted version companies install on their own infrastructure.

**4. What is a Pipeline in Azure DevOps?**
An automated workflow (defined in YAML or Classic editor) that builds, tests, and deploys code whenever triggered (e.g., by a code push).

**5. What is the difference between Build pipeline and Release pipeline?**
Build pipeline compiles code, runs tests, and produces an artifact. Release pipeline takes that artifact and deploys it to environments (Dev/Staging/Prod) — often with approval gates. Modern YAML pipelines can combine both into "multi-stage pipelines."

**6. What is a Service Connection?**
A secure, saved set of credentials that lets Azure DevOps pipelines connect to external services (Azure subscription, AWS, Docker registry, etc.) without hardcoding secrets in the pipeline.

**7. What is an Agent and Agent Pool?**
An agent is the machine that actually runs your pipeline jobs (build, test, deploy commands). An agent pool is a group of agents that pipelines can be assigned to run on.

**8. Difference between Microsoft-hosted and Self-hosted agents?**
Microsoft-hosted: Microsoft provides and manages the VM, fresh every run, limited customization, time-limited runtime. Self-hosted: your company's own machine, you control installed tools, no time limit, but you maintain/patch it.

**9. What is a Variable Group?**
A reusable set of variables (including secrets) that can be shared across multiple pipelines, managed centrally in Library.

**10. What is an Environment in Azure DevOps?**
A logical target for deployments (e.g., "Dev", "Staging", "Prod") that can have approval checks, gates, and deployment history tracking attached to it.

**11. What are Approvals and Gates?**
Approvals require a human to manually sign off before deployment proceeds. Gates are automated checks (e.g., query a monitoring tool, check work item status) that must pass before deployment continues.

**12. What is the difference between YAML pipelines and Classic pipelines?**
YAML pipelines are defined as code (version-controlled alongside the app, easier to review/audit). Classic pipelines are built using a GUI, harder to track changes on, and considered legacy today.

**13. What is a Trigger in a pipeline?**
A trigger defines what causes a pipeline to run automatically — e.g., a push to a branch, a PR, a schedule, or completion of another pipeline.

**14. What is a Stage, Job, and Task (hierarchy in YAML pipelines)?**
Pipeline → contains Stages → each Stage contains Jobs → each Job contains Steps/Tasks. Stages usually represent big phases (Build, Test, Deploy); Jobs run on an agent; Tasks/Steps are individual commands.

**15. What is Azure Artifacts used for?**
Storing and sharing packages (NuGet, npm, Maven, Python packages) privately within an organization, and storing build outputs between pipeline stages.

**16. What is a Deployment Group vs Deployment Environment?**
Deployment Groups (older/classic) target VM-based deployments. Environments (modern) are more flexible, support Kubernetes namespaces, VMs, and give richer tracking + approval features.

**17. How do you handle secrets securely in Azure DevOps?**
Store them in Variable Groups or Azure Key Vault (linked via Key Vault task), mark variables as "secret" (they get masked in logs), and avoid hardcoding them in YAML.

**18. What is a Branch Policy?**
Rules enforced on a branch (usually `main`) — e.g., require PR review, require passing build, require linked work item — before code can be merged.

**19. What is the purpose of Azure Boards?**
Agile project management — tracking work items, sprints, backlogs, and Kanban boards, linkable directly to commits and PRs for full traceability.

**20. What is a multi-stage pipeline, and why use it?**
A single YAML pipeline that defines multiple stages (Build → Test → Deploy to Dev → Deploy to Prod) in one file, giving end-to-end visibility and version control of the entire delivery process.

**21. What is the difference between a Pipeline template and a regular pipeline?**
A template is a reusable YAML file containing common steps/jobs that other pipelines can call/extend — avoids duplicating the same pipeline logic across projects.

**22. How does Azure DevOps integrate with Azure Key Vault?**
Through a "Azure Key Vault" task or by linking a Variable Group directly to a Key Vault, so secrets are pulled at runtime instead of stored in the pipeline itself.

**23. What is Continuous Integration (CI) in Azure DevOps context?**
Automatically building and testing code every time it's pushed, so integration issues are caught early instead of piling up.

**24. What is Continuous Deployment vs Continuous Delivery?**
Continuous Delivery: code is always in a deployable state, but deployment to production needs manual approval. Continuous Deployment: every passing change is deployed to production automatically, no manual step.

**25. What happens if a pipeline fails at the deployment stage?**
Depends on setup: pipeline stops, notifies owners, deployment history logs the failure; teams typically roll back to the last known-good release or fix and redeploy. Root cause is checked via pipeline logs, agent logs, and app logs.

**26. What is the purpose of a Release Gate calling an external monitoring tool?**
To automatically verify system health (e.g., no active alerts, error rate under threshold) before allowing deployment to proceed to the next environment — prevents deploying into an already unhealthy system.

**27. What's the difference between Project-scoped and Organization-scoped resources?**
Some things (like Repos, Boards) live inside a single Project. Others (like Agent Pools, some Service Connections) can be shared at the Organization level across multiple projects.

**28. How do you roll back a failed deployment in Azure DevOps?**
Redeploy the last successful release/artifact through the pipeline (Azure DevOps keeps deployment history), rather than manually undoing changes on the server.

**29. What is RBAC (Role-Based Access Control) in Azure DevOps used for?**
Controlling who can view, edit, approve, or administer different parts (repos, pipelines, environments) — critical for compliance in regulated environments.

**30. How would you design a pipeline for a highly regulated client (bank/healthcare)?**
Use YAML pipelines for auditability, mandatory manual approvals before Prod, branch policies requiring PR + passing build, secrets only via Key Vault, environment-level approval checks, and full logging/monitoring integrated with the pipeline for compliance evidence.

---

# SECTION 3: GITHUB ACTIONS — TOP 30 INTERVIEW QUESTIONS

**1. What is GitHub Actions?**
GitHub's built-in CI/CD and automation platform. It lets you define workflows (in YAML) that run automatically in response to events in a GitHub repository (push, PR, issue created, schedule, etc.).

**2. What is a Workflow?**
A YAML file (stored in `.github/workflows/`) that defines one or more automated processes triggered by repository events.

**3. What is a Job?**
A set of steps that run on the same runner (machine). Jobs run in parallel by default unless dependencies are defined.

**4. What is a Step?**
A single task within a job — either running a shell command or using an "Action" (pre-built reusable unit).

**5. What is an Action?**
A reusable, packaged piece of automation (e.g., `actions/checkout`) that you can plug into any workflow instead of writing the logic yourself.

**6. What is a Runner?**
The machine that executes your workflow's jobs. Can be GitHub-hosted (managed by GitHub) or self-hosted (your own machine/server).

**7. Difference between GitHub-hosted and self-hosted runners?**
GitHub-hosted: fresh VM every run, no maintenance needed, limited runtime and specs. Self-hosted: your own infrastructure, full control over installed software and specs, but you maintain and secure it yourself.

**8. What triggers a workflow?**
Events like `push`, `pull_request`, `schedule` (cron), `workflow_dispatch` (manual trigger), `release`, or even another workflow completing.

**9. What are Secrets in GitHub Actions?**
Encrypted values (API keys, passwords, tokens) stored at repo/org/environment level, injected into workflows at runtime, never exposed in logs.

**10. What is an Environment in GitHub Actions?**
A named deployment target (e.g., "production") that can have protection rules like required reviewers or wait timers before a job targeting it can run.

**11. What is Matrix Strategy?**
A way to run the same job multiple times with different configurations in parallel (e.g., testing across Node.js 16, 18, 20, or multiple OSes) using one job definition.

**12. What is a Reusable Workflow?**
A complete workflow file that can be called from other workflows using `workflow_call` — avoids copy-pasting the same CI/CD logic across many repos.

**13. What is a Composite Action?**
A custom action made by combining multiple steps into one reusable unit, used within a single repo (or shared) instead of duplicating steps.

**14. How do you pass data between jobs?**
Using `outputs` from one job, referenced by later jobs, or by uploading/downloading artifacts between jobs.

**15. What is `actions/checkout`?**
The most commonly used action — it checks out (downloads) your repository's code onto the runner so subsequent steps can work with it.

**16. How do you cache dependencies in GitHub Actions?**
Using `actions/cache` — saves things like `node_modules` or dependency folders between runs to speed up builds instead of reinstalling every time.

**17. What is `workflow_dispatch`?**
A trigger that allows manually starting a workflow from the GitHub UI or API, optionally with input parameters.

**18. How do you restrict a workflow to run only on a specific branch?**
Using the `on: push: branches:` filter, specifying which branch names should trigger the workflow.

**19. What is the difference between `needs` and running jobs in parallel?**
By default, jobs run in parallel. Adding `needs: [job_name]` makes a job wait until the specified job(s) complete successfully before starting.

**20. How do you handle deployment approvals in GitHub Actions?**
By assigning the deployment job to a protected "Environment" that has required reviewers configured — the job pauses until someone approves it.

**21. What is `GITHUB_TOKEN`?**
An automatically generated token GitHub provides to every workflow run, scoped to that repository, used for common tasks like commenting on PRs or pushing tags — without needing a personal access token.

**22. How do you debug a failing GitHub Actions workflow?**
Check the workflow run logs step by step, enable debug logging (`ACTIONS_STEP_DEBUG` secret), and re-run failed jobs with debug logging enabled to see detailed output.

**23. What is an Artifact in GitHub Actions?**
A file or set of files produced by a job (e.g., build output, test reports) that can be uploaded and downloaded later within the same workflow run or kept for later use.

**24. How do you run a workflow on a schedule?**
Using the `schedule` trigger with cron syntax, e.g., `cron: '0 0 * * *'` for daily at midnight UTC.

**25. What is the difference between `pull_request` and `pull_request_target` triggers?**
`pull_request` runs with the PR's code and limited permissions (safe for forks). `pull_request_target` runs with the base branch's workflow file and full permissions/secrets — riskier, used carefully to avoid exposing secrets to untrusted PR code.

**26. How do you limit concurrent runs of a workflow?**
Using the `concurrency` key with a group name — e.g., to cancel older in-progress runs when a new push happens on the same branch.

**27. How would you set up a workflow that only deploys to production after tests pass and a manual approval?**
Structure it as multiple jobs with `needs`: build → test → deploy. The deploy job targets a protected "production" Environment requiring manual reviewer approval, ensuring it only runs after test job succeeds and a human approves.

**28. What are the security risks with third-party Actions, and how do you mitigate them?**
Third-party actions can contain malicious code with access to your secrets. Mitigate by pinning actions to a specific commit SHA (not just a tag), using actions only from verified/trusted publishers, and limiting secret scope.

**29. How do you share configuration/variables across multiple workflows?**
Using repository or organization-level "Variables" and "Secrets," or reusable/composite workflows that centralize shared logic.

**30. How would you design a CI/CD pipeline in GitHub Actions for a microservices project with multiple services in one repo?**
Use path filters (`on: push: paths:`) so only the changed service's workflow triggers, matrix strategy if services share similar build steps, reusable workflows for shared logic (e.g., common test/build steps), and separate protected Environments per service per stage (Dev/Staging/Prod).

---

# SECTION 4: READY PIPELINE TEMPLATES

## 4A. Azure DevOps — Infra Pipeline (Terraform-style, Best Practices)

```yaml
# azure-pipelines-infra.yml
trigger:
  branches:
    include:
      - main
  paths:
    include:
      - infra/*

pool:
  vmImage: 'ubuntu-latest'

variables:
  - group: infra-common-vars     # Variable Group (holds non-secret shared config)
  - name: terraformVersion
    value: '1.7.5'

stages:

- stage: Validate
  displayName: 'Validate Infra Code'
  jobs:
    - job: TerraformValidate
      steps:
        - task: TerraformInstaller@1
          inputs:
            terraformVersion: $(terraformVersion)

        - task: TerraformTaskV4@4
          displayName: 'Terraform Init'
          inputs:
            provider: 'azurerm'
            command: 'init'
            backendServiceArm: 'AzureServiceConnection'   # Service Connection
            backendAzureRmResourceGroupName: '$(tfStateRG)'
            backendAzureRmStorageAccountName: '$(tfStateSA)'
            backendAzureRmContainerName: 'tfstate'
            backendAzureRmKey: 'infra.tfstate'

        - task: TerraformTaskV4@4
          displayName: 'Terraform Validate'
          inputs:
            provider: 'azurerm'
            command: 'validate'

        - script: |
            terraform fmt -check
          displayName: 'Check Terraform Formatting'

- stage: Plan
  displayName: 'Terraform Plan'
  dependsOn: Validate
  jobs:
    - job: TerraformPlan
      steps:
        - task: TerraformTaskV4@4
          inputs:
            provider: 'azurerm'
            command: 'plan'
            environmentServiceNameAzureRM: 'AzureServiceConnection'
            commandOptions: '-out=tfplan'

        # Publish plan as artifact so Apply stage uses the SAME reviewed plan
        - publish: '$(System.DefaultWorkingDirectory)/tfplan'
          artifact: 'tfplan'

- stage: ApplyDev
  displayName: 'Apply to Dev'
  dependsOn: Plan
  jobs:
    - deployment: TerraformApplyDev
      environment: 'Dev'          # No approval gate needed for Dev
      strategy:
        runOnce:
          deploy:
            steps:
              - download: current
                artifact: 'tfplan'
              - task: TerraformTaskV4@4
                inputs:
                  provider: 'azurerm'
                  command: 'apply'
                  commandOptions: '$(Pipeline.Workspace)/tfplan/tfplan'

- stage: ApplyProd
  displayName: 'Apply to Production'
  dependsOn: ApplyDev
  jobs:
    - deployment: TerraformApplyProd
      environment: 'Production'   # Environment configured with manual approval + Key Vault-backed secrets
      strategy:
        runOnce:
          deploy:
            steps:
              - download: current
                artifact: 'tfplan'
              - task: TerraformTaskV4@4
                inputs:
                  provider: 'azurerm'
                  command: 'apply'
                  commandOptions: '$(Pipeline.Workspace)/tfplan/tfplan'
```

**Best practices baked into this template:**
- Plan and Apply are separate stages — never auto-apply without a reviewed plan.
- The exact same `tfplan` artifact is applied (not a freshly regenerated plan) — avoids "plan drift" between review and execution.
- Secrets/backend config come from Variable Groups + Service Connections, never hardcoded.
- Production requires an `environment` with manual approval configured in Azure DevOps UI.
- Path trigger filter (`paths: include: infra/*`) so this pipeline only runs when infra code actually changes.

---

## 4B. GitHub Actions — Infra Pipeline (Terraform-style, Best Practices)

```yaml
# .github/workflows/infra-pipeline.yml
name: Infra Pipeline

on:
  push:
    branches: [main]
    paths:
      - 'infra/**'
  workflow_dispatch:

env:
  TF_VERSION: '1.7.5'

jobs:

  validate:
    name: Validate & Format Check
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: hashicorp/setup-terraform@v3
        with:
          terraform_version: ${{ env.TF_VERSION }}

      - name: Terraform Init
        run: terraform init
        working-directory: infra

      - name: Terraform Format Check
        run: terraform fmt -check
        working-directory: infra

      - name: Terraform Validate
        run: terraform validate
        working-directory: infra

  plan:
    name: Terraform Plan
    needs: validate
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: hashicorp/setup-terraform@v3
        with:
          terraform_version: ${{ env.TF_VERSION }}

      - name: Terraform Init
        run: terraform init
        working-directory: infra

      - name: Terraform Plan
        run: terraform plan -out=tfplan
        working-directory: infra
        env:
          ARM_CLIENT_ID: ${{ secrets.ARM_CLIENT_ID }}
          ARM_CLIENT_SECRET: ${{ secrets.ARM_CLIENT_SECRET }}
          ARM_SUBSCRIPTION_ID: ${{ secrets.ARM_SUBSCRIPTION_ID }}
          ARM_TENANT_ID: ${{ secrets.ARM_TENANT_ID }}

      - name: Upload Plan Artifact
        uses: actions/upload-artifact@v4
        with:
          name: tfplan
          path: infra/tfplan

  apply-dev:
    name: Apply to Dev
    needs: plan
    runs-on: ubuntu-latest
    environment: dev
    steps:
      - uses: actions/checkout@v4
      - uses: hashicorp/setup-terraform@v3
        with:
          terraform_version: ${{ env.TF_VERSION }}

      - name: Download Plan Artifact
        uses: actions/download-artifact@v4
        with:
          name: tfplan
          path: infra

      - name: Terraform Init
        run: terraform init
        working-directory: infra

      - name: Terraform Apply
        run: terraform apply -auto-approve tfplan
        working-directory: infra
        env:
          ARM_CLIENT_ID: ${{ secrets.ARM_CLIENT_ID }}
          ARM_CLIENT_SECRET: ${{ secrets.ARM_CLIENT_SECRET }}
          ARM_SUBSCRIPTION_ID: ${{ secrets.ARM_SUBSCRIPTION_ID }}
          ARM_TENANT_ID: ${{ secrets.ARM_TENANT_ID }}

  apply-prod:
    name: Apply to Production
    needs: apply-dev
    runs-on: ubuntu-latest
    environment: production   # Configure "Required reviewers" on this environment in repo settings
    steps:
      - uses: actions/checkout@v4
      - uses: hashicorp/setup-terraform@v3
        with:
          terraform_version: ${{ env.TF_VERSION }}

      - name: Download Plan Artifact
        uses: actions/download-artifact@v4
        with:
          name: tfplan
          path: infra

      - name: Terraform Init
        run: terraform init
        working-directory: infra

      - name: Terraform Apply
        run: terraform apply -auto-approve tfplan
        working-directory: infra
        env:
          ARM_CLIENT_ID: ${{ secrets.ARM_CLIENT_ID }}
          ARM_CLIENT_SECRET: ${{ secrets.ARM_CLIENT_SECRET }}
          ARM_SUBSCRIPTION_ID: ${{ secrets.ARM_SUBSCRIPTION_ID }}
          ARM_TENANT_ID: ${{ secrets.ARM_TENANT_ID }}
```

**Best practices baked in:**
- `needs:` chains jobs so Apply never runs before Plan/Validate succeed.
- Same plan artifact is downloaded and applied — no re-planning at apply time.
- Secrets pulled from GitHub encrypted secrets, never hardcoded.
- Production job uses a protected `environment: production` — set "Required reviewers" in GitHub repo Settings → Environments for a manual approval gate.
- Path filter so workflow triggers only on infra code changes.

---

## 4C. Azure DevOps — Application Pipeline (Build → Test → Scan → Deploy)

```yaml
# azure-pipelines-app.yml
trigger:
  branches:
    include:
      - main
      - develop

pool:
  vmImage: 'ubuntu-latest'

variables:
  - group: app-secrets           # holds API keys, connection strings (as secret variables)
  - name: buildConfiguration
    value: 'Release'

stages:

- stage: Build
  jobs:
    - job: BuildAndUnitTest
      steps:
        - task: UseDotNet@2      # example uses .NET; swap for Node/Python/Java as needed
          inputs:
            version: '8.x'

        - script: dotnet restore
          displayName: 'Restore Dependencies'

        - script: dotnet build --configuration $(buildConfiguration)
          displayName: 'Build'

        - script: dotnet test --logger trx
          displayName: 'Run Unit Tests'

        - task: PublishTestResults@2
          inputs:
            testResultsFormat: 'VSTest'
            testResultsFiles: '**/*.trx'

        - task: PublishBuildArtifacts@1
          inputs:
            pathToPublish: '$(Build.ArtifactStagingDirectory)'
            artifactName: 'drop'

- stage: SecurityScan
  dependsOn: Build
  jobs:
    - job: SAST
      steps:
        - script: |
            echo "Run SAST tool here (e.g., SonarQube, Checkmarx, Trivy for containers)"
          displayName: 'Static Security Scan'

- stage: DeployStaging
  dependsOn: SecurityScan
  jobs:
    - deployment: DeployToStaging
      environment: 'Staging'
      strategy:
        runOnce:
          deploy:
            steps:
              - download: current
                artifact: 'drop'
              - task: AzureWebApp@1
                inputs:
                  azureSubscription: 'AzureServiceConnection'
                  appType: 'webApp'
                  appName: 'myapp-staging'
                  package: '$(Pipeline.Workspace)/drop/**/*.zip'

- stage: DeployProd
  dependsOn: DeployStaging
  jobs:
    - deployment: DeployToProduction
      environment: 'Production'    # Manual approval configured here
      strategy:
        runOnce:
          deploy:
            steps:
              - download: current
                artifact: 'drop'
              - task: AzureWebApp@1
                inputs:
                  azureSubscription: 'AzureServiceConnection'
                  appType: 'webApp'
                  appName: 'myapp-prod'
                  package: '$(Pipeline.Workspace)/drop/**/*.zip'
```

---

## 4D. GitHub Actions — Application Pipeline (Build → Test → Scan → Deploy)

```yaml
# .github/workflows/app-pipeline.yml
name: Application Pipeline

on:
  push:
    branches: [main, develop]

jobs:

  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Runtime
        uses: actions/setup-node@v4     # swap for setup-python / setup-java / setup-dotnet as needed
        with:
          node-version: '20'

      - name: Install Dependencies
        run: npm ci

      - name: Run Unit Tests
        run: npm test

      - name: Build App
        run: npm run build

      - name: Upload Build Artifact
        uses: actions/upload-artifact@v4
        with:
          name: app-build
          path: dist/

  security-scan:
    needs: build-and-test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run SAST / Dependency Scan
        run: echo "Run tools like Trivy, Snyk, or CodeQL here"

  deploy-staging:
    needs: security-scan
    runs-on: ubuntu-latest
    environment: staging
    steps:
      - uses: actions/download-artifact@v4
        with:
          name: app-build
          path: dist

      - name: Deploy to Staging
        run: echo "Deploy dist/ to staging server or Azure Web App via azure/webapps-deploy action"

  deploy-prod:
    needs: deploy-staging
    runs-on: ubuntu-latest
    environment: production    # Set "Required reviewers" for manual approval
    steps:
      - uses: actions/download-artifact@v4
        with:
          name: app-build
          path: dist

      - name: Deploy to Production
        run: echo "Deploy dist/ to production server or Azure Web App via azure/webapps-deploy action"
```

---

## Quick Best-Practice Checklist (say this in interviews when asked "how do you design pipelines")

1. Separate stages: Build → Test → Security Scan → Deploy Staging → Deploy Prod.
2. Never re-plan/re-build at the Prod stage — reuse the exact artifact/plan validated earlier.
3. Secrets always from Key Vault / GitHub Secrets / Variable Groups — never hardcoded.
4. Production always behind a manual approval gate.
5. Path filters so pipelines don't trigger unnecessarily.
6. Branch policies (PR + passing build required) before merge to main.
7. Full audit trail: pipeline logs + deployment history + approval history — required for compliance-heavy clients like healthcare/finance.
