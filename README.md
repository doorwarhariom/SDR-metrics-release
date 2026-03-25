# SDR-metrics-release
# SDR Metrics Automation Tool

Automated Azure Infrastructure Metrics Collector for SDR Reporting.

This tool collects **last full calendar month** metrics from your Azure subscription and exports them into a structured **Excel file** with separate sheets per resource type.

---

## 📊 What Data Gets Collected

| Sheet | Resources | Metrics |
|-------|-----------|---------|
| **AKS** | Kubernetes Clusters | CPU %, Memory RSS %, Memory Working Set %, Disk Usage % |
| **Virtual Machines** | All VMs | CPU %, Available Memory %, Network In/Out, Disk Read/Write |
| **Application Gateway** | App Gateways | Unhealthy Host Count, Total Requests, Failed Requests |
| **MySQL Flexible** | MySQL Servers | CPU %, Memory %, IO %, Active Connections, Storage Used |
| **Redis** | Redis Caches | CPU %, Memory MB, Cache Hits, Connected Clients |
| **SQL Databases** | SQL Servers/DBs | CPU %, Memory %, DTU %, Failed Connections |

---

## ✅ Prerequisites

### 1. Install Azure CLI
Download and install from:
👉 https://aka.ms/installazurecliwindows

After installing, verify it works:
`
az --version
`

### 2. Login to Azure
Open Command Prompt and run:
`
az login
`
A browser window will open — sign in with your **Azure account** that has access to your subscription.

---

## ⬇️ Download

Download the latest version from the link below:

👉 **[Download SDR-Metrics.exe](https://github.com/doorwarhariom/SDR-metrics-release/releases/latest/download/SDR-Metrics.exe)**

---

## 🚀 How to Use

### Step 1 — Find your Subscription ID
1. Go to [portal.azure.com](https://portal.azure.com)
2. Search for **Subscriptions**
3. Copy your **Subscription ID**

### Step 2 — Open Command Prompt
1. Move SDR-Metrics.exe to any folder (e.g. Desktop or Downloads)
2. Open **Command Prompt** in that folder
   - Hold Shift + Right-click in the folder → **Open PowerShell/Command Prompt here**

### Step 3 — Run the tool

**Basic usage** (saves Excel in the same folder):
`
**SDR-Metrics.exe --subscription-id "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"**
`

**Custom output path:**
`
SDR-Metrics.exe --subscription-id "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" --output "C:\Users\YourName\Desktop\metrics.xlsx"
`

**Short form:**
`
SDR-Metrics.exe -s "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" -o "C:\Users\YourName\Desktop\metrics.xlsx"
`

### Step 4 — Wait for completion
The tool will show progress as it runs:
`
============================================
   SDR Metrics Automation Starting...
   Subscription: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
============================================

🔵 [1/6] Collecting AKS (Kubernetes) metrics...
   Found 3 AKS cluster(s)
   ⏳ Fetching metrics for cluster: my-aks-cluster
   ✅ AKS done — 3 row(s) collected

🔵 [2/6] Collecting Virtual Machine metrics...
   ...

⏳ Writing data to Excel file...
✅ Metrics exported successfully → azure_infra_metrics_latest.xlsx
`

### Step 5 — Open the Excel file
The Excel file will be in the same folder as the .exe (unless you specified a custom path).

---

## 🔄 Multiple Subscriptions

Run the tool once per subscription with a different output file each time:
`
SDR-Metrics.exe -s "subscription-id-1" -o "metrics_sub1.xlsx"
SDR-Metrics.exe -s "subscription-id-2" -o "metrics_sub2.xlsx"
SDR-Metrics.exe -s "subscription-id-3" -o "metrics_sub3.xlsx"
`

---

## ❓ Troubleshooting

| Error | Fix |
|-------|-----|
| z: command not found | Install Azure CLI from the link above |
| Please run 'az login' | Run z login in Command Prompt first |
| AuthenticationError | Your account may not have access to that subscription — check with your admin |
| No data in Excel sheet | No resources of that type exist in the subscription — this is normal |
| Windows Defender warning | Click **More info** → **Run anyway** (the exe is safe, built from our private repo) |

---

## 📅 Metrics Time Window

The tool always collects data for the **last full calendar month**.  
For example, if you run it in March 2026, it collects data from **February 1 – February 28, 2026**.

---

## 📬 Support

For issues or questions, contact the platform team.
