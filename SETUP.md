# 🛠️ GitHub Profile Automation - Setup Guide

This guide details how to set up the automation workflows for your GitHub profile repository (`PatilRohit03/PatilRohit03`). Once configured, these workflows will run automatically via GitHub Actions schedules to keep your profile dynamic and maintenance-free.

---

## 📁 Repository Folder Structure

Ensure your repository has the following file structure:

```
PatilRohit03/
├── README.md
├── SETUP.md
└── .github/
    └── workflows/
        ├── snake.yml
        ├── metrics.yml
        ├── leetcode-stats.yml
        └── wakatime.yml
```

---

## 🔑 Required Repository Secrets

To enable these workflows, navigate to your repository on GitHub:
**Settings ➡️ Secrets and variables ➡️ Actions ➡️ New repository secret**.

Create the following secrets:

### 1. `METRICS_TOKEN`
* **Purpose:** Allows the `lowlighter/metrics` workflow to query repository details, achievements, and statistics.
* **How to get it:**
  1. Go to your GitHub account settings **Developer Settings ➡️ Personal Access Tokens ➡️ Tokens (classic)**.
  2. Click **Generate new token (classic)**.
  3. Select scopes: `repo` (all), `read:user`, `read:org`, `write:packages`.
  4. Copy the generated token and save it as a secret named `METRICS_TOKEN` in your repository.

### 2. `WAKATIME_API_KEY`
* **Purpose:** Allows the WakaTime workflow to fetch your weekly coding activity.
* **How to get it:**
  1. Register/Login to [WakaTime](https://wakatime.com/).
  2. Navigate to **Account Settings** and copy your **Secret API Key**.
  3. Save it as a secret named `WAKATIME_API_KEY` in your repository.

---

## ⚙️ Step-by-Step Setup Instructions

### Step 1: Push All Workflow Files
Make sure to commit and push all `.yml` files in the `.github/workflows/` directory to the `main` branch of your repository.

### Step 2: Grant Workflow Write Permissions
For the workflows to commit updates (like LeetCode and WakaTime stats) directly back to your `README.md`, you need to grant the runners write permissions:
1. Go to your repository **Settings ➡️ Actions ➡️ General**.
2. Scroll down to **Workflow permissions**.
3. Select **Read and write permissions**.
4. Check **Allow GitHub Actions to create and approve pull requests**.
5. Click **Save**.

### Step 3: Trigger the First Run
You don't need to wait for the daily scheduled runs to verify everything is working. You can trigger them manually:
1. Go to the **Actions** tab of your repository.
2. Select a workflow from the left sidebar (e.g., `Generate Contribution Snake`).
3. Click the **Run workflow** dropdown on the right and select **Run workflow**.
4. Repeat for the other workflows.
