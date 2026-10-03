# 📢 Banner Settings for Azure DevOps

<p align="center">
  <img src="static/screenshot.png" alt="Banner Settings Screenshot" width="850">
</p>

<p align="center">
  <strong>Site-wide banner management for Azure DevOps</strong>
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-how-it-works">How It Works</a> •
  <a href="#-banner-types">Banner Types</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-development">Development</a>
</p>

---

## 📌 Overview

**Banner Settings** is an Azure DevOps extension that provides a settings pane under **Organization Settings**.

It allows **Project Collection Administrators** to create and display site-wide banners across Azure DevOps.

Instead of sending mass emails, administrators can use banners to communicate:

* 📢 Important announcements
* ⚠️ Upcoming changes
* 🔧 Maintenance notifications
* 📅 Upcoming events
* ℹ️ General information

The extension is compatible with **Azure DevOps Services and Azure DevOps Server**.

---

## 📸 Preview

<p align="center">
  <img src="static/screenshot.png" alt="Banner Settings" width="850">
</p>

### Example Banner

> ⚠️ **Windows October Update released!**
> Please visit the [Windows Insider Blog](https://blogs.windows.com/windowsexperience/tag/windows-insider-program/) for more information.

---

# ✨ Features

<table>
<tr>
<td width="50%">

### 📢 Site-wide Banners

Display important messages across Azure DevOps pages.

</td>
<td width="50%">

### 🎨 Multiple Message Levels

Choose between Info, Warning, and Error banners.

</td>
</tr>

<tr>
<td>

### 📅 Expiration Dates

Set an expiration date for each banner.

</td>
<td>

### 🔗 Markdown Links

Include hyperlinks in banner messages using Markdown.

</td>
</tr>
</table>

---

# 🚦 Banner Types

The extension supports three levels of banner messages:

| Level          | Purpose               | Example                  |
| -------------- | --------------------- | ------------------------ |
| 🟦 **Info**    | General information   | New feature announcement |
| 🟨 **Warning** | Important notice      | Scheduled maintenance    |
| 🟥 **Error**   | Critical notification | Service disruption       |

---

# 🔄 How It Works

The basic workflow of the extension can be represented as:

```mermaid
flowchart TD
    A[Project Collection Administrator] --> B[Organization Settings]
    B --> C[Banner Settings]
    C --> D[Create / Configure Banner]
    D --> E{Select Banner Level}
    E -->|Info| F[Publish Banner]
    E -->|Warning| F
    E -->|Error| F
    F --> G[Azure DevOps Users]
    G --> H[View Banner]
    H --> I{Banner Closed?}
    I -->|Yes| J[Next Available Banner]
    I -->|No| K[Banner Remains Visible]
```

---

# 🏗️ Extension Workflow

```mermaid
flowchart LR
    A[Administrator] --> B[Banner Configuration]
    B --> C[Validation]
    C --> D[Banner Storage]
    D --> E[Azure DevOps Pages]
    E --> F[Users]

    B --> G[Expiration Date]
    G --> D

    B --> H[Message Level]
    H --> D
```

---

# 🧩 Core Components

| Component                    | Description                                         |
| ---------------------------- | --------------------------------------------------- |
| ⚙️ **Organization Settings** | Provides access to banner configuration             |
| 📝 **Banner Configuration**  | Allows administrators to create and modify messages |
| 🚦 **Message Level**         | Determines banner priority                          |
| 📅 **Expiration Date**       | Controls banner availability                        |
| 🔗 **Markdown Support**      | Allows hyperlinks inside messages                   |
| 🖥️ **Azure DevOps UI**      | Displays active banners to users                    |

---

# 🥇 Banner Priority

Only **one banner can be displayed at a time** to keep the interface clean.

When multiple banners exist, they are prioritized by their level.

```mermaid
flowchart TD
    A[Multiple Active Banners] --> B{Highest Priority}
    B --> C[Error]
    B --> D[Warning]
    B --> E[Info]

    C --> F[Display Error Banner]
    F --> G{Closed or Deleted?}

    G -->|Yes| H[Display Next Available Banner]
    G -->|No| I[Keep Error Banner Visible]

    H --> D
```
