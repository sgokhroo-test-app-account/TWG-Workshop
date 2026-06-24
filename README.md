# TWG-Workshop
Instructions for TWG Workshop
# Workshop FAQ: Setting Up Forge & CLI

Welcome, workshop participants! **This guide covers prerequisites, installation, first-app creation, local development, and common troubleshooting for Atlassian Forge.**

## 📦 CLI Installation & Authentication

**Install Forge CLI globally:**

```
npm install -g @forge/cli
```

**Verify installation:**

```
forge --version
```

**Login:**

```
forge login
```

**API Token needed for login:**

Generate at: id.atlassian.com/manage/api-tokens

Verify session:

```
forge whoami
```

## 🚀 Create, Deploy & Install Your First App

1. **Create a new app:** forge create — Follow prompts: name, product (Jira/Confluence), template

**Deploy (compile & upload):**

```
forge deploy
```

1. **Install on your dev site:**

```
forge install
```


## 🧑‍💻 Workshop Path: Clone the Bitbucket Repo and Continue Building

For this workshop, participants should start from the shared Bitbucket repository instead of creating everything from scratch. Replace the placeholders below with the repository URL and folder name shared by the facilitator.

### 1. Clone the workshop app

```bash
git clone <BITBUCKET_REPO_URL>
cd <APP_DIRECTORY>
```

### 2. Install dependencies

```bash
npm install
```

### 3. Register your own Forge app ID

```bash
forge register
```

This creates a new app ID in `manifest.yml` and links the app copy to your Atlassian developer account. If the workshop uses Teamwork Graph API access, share this app ID with the facilitator if allowlisting is required.

### 4. Validate, deploy, and install

```bash
forge lint
forge deploy
forge install
```

When prompted, choose the workshop product and enter the target site or workspace URL. For Bitbucket apps, use a shared team workspace URL such as `bitbucket.org/<workspace-id>`; Forge apps are not supported on personal Bitbucket workspaces.

### 5. Start building locally

```bash
forge tunnel
```

Keep this running while editing the app. If you change `manifest.yml`, scopes, modules, or dependencies, stop the tunnel and run:

```bash
forge deploy
forge install --upgrade
forge tunnel
```

## 🔁 Local Development & Tunneling

**Run app locally with hot reload:**

```
forge tunnel
```

Code changes sync automatically (hot reload enabled)

Docker must be installed & running

**⚠️ If you modify manifest.yml or package.json:**

Stop tunnel → forge deploy → restart tunnel

## ⚡ Quick Reference: Key Commands

| Need | Command | Notes |
| --- | --- | --- |
| Check Node.js version | `node --version` | Use a supported LTS version before installing Forge. |
| Install/use Node.js with nvm | `nvm install --lts nvm use --lts` | Recommended for macOS/Linux to avoid permission issues. |
| Check npm version | `npm --version` | npm is installed with Node.js. |
| Check Git version | `git --version` | Required to clone the workshop repository. |
| Install Forge CLI | `npm install -g @forge/cli@latest` | Installs the latest supported Forge CLI globally. |
| Verify Forge CLI | `forge --version` | Confirms the CLI is installed. |
| View Forge help | `forge --help` | Shows all available commands. |
| Log in | `forge login` | Use your Atlassian email and API token. |
| Check logged-in account | `forge whoami` | Confirms the CLI is authenticated. |
| Clone the workshop app | `git clone <BITBUCKET_REPO_URL> cd <APP_DIRECTORY>` | Replace with the Bitbucket repository URL shared during the workshop. |
| Install app dependencies | `npm install` | Run from the cloned app directory. |
| Register cloned app to your account | `forge register` | Creates a new app ID in `manifest.yml` for your copy of the app. |
| Lint the app | `forge lint` | Validates manifest and source before deployment. |
| Fix lint issues where possible | `forge lint --fix` | Use before deploying if lint reports fixable issues. |
| Deploy to development | `forge deploy` | Builds and uploads the app to the default development environment. |
| Install on a site or workspace | `forge install` | Select the relevant product and enter the target site/workspace URL. |
| Install with explicit product/site | `forge install -p <product> -s <site-or-workspace-url>` | Example products: Jira, Confluence, Bitbucket, Compass. |
| Upgrade an installed app | `forge install --upgrade` | Run after manifest, module, or scope changes. |
| Start local development tunnel | `forge tunnel` | Requires Docker running. Use for live local code changes. |
| View recent logs | `forge logs -e development --since 15m` | Useful for debugging without an active tunnel. |
| Set app environment variable | `forge variables set MY_KEY my-value` | For values used by your app at runtime. |
| Set encrypted variable | `forge variables set --encrypt MY_SECRET my-secret-value` | Use for secrets and tokens. |
| List variables | `forge variables list` | Encrypted values are not shown in plaintext. |
| Unset variable | `forge variables unset MY_KEY` | Removes an environment variable. |
| Create a new app from template | `forge create` | Use this if you are not starting from the workshop repo. |
| List installations | `forge install list` | Shows where your app is installed. |
| List environments | `forge environments list` | Shows app environments. |
| Create a separate development environment | `forge environments create` | Useful if multiple people are working on the same app. |
| Deploy to a named environment | `forge deploy -e <environment>` | Example: `forge deploy -e staging`. |
| Tunnel to a named environment | `forge tunnel -e <environment>` | Use separate environments to avoid interrupting others. |
| Uninstall app | `forge uninstall` | Removes the app from a site/workspace. |
| Log out | `forge logout` | Clears the current CLI session. |
| Upgrade Forge CLI | `npm uninstall -g @forge/cli npm install -g @forge/cli@latest` | Recommended when the CLI is out of date. |
