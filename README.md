# active-directory-complete-guid

* In a **small network (5 computers, 5 employees)**, management is easy:

  * You manually create accounts on each PC.
  * Example: If *Rahul* joins, you log into his computer and create his user.
  * If his PC breaks, you go physically and fix it.

* In a **large network (157 computers, 320 users, multiple offices)**, this becomes impossible:

  * Example: If Rahul needs access to a shared folder, you’d have to configure it on many systems manually.
  * If a password policy changes, you must update it on every computer one by one.
  * Supporting users across different offices becomes time-consuming.

👉 **Solution: Windows Domain**

* A domain **centralizes everything** using **Active Directory (AD)**.
* Managed by a **Domain Controller (DC)**.

✅ **With Domain (Example):**

* Create Rahul’s account **once in AD**, and he can log into any company PC.
* Apply a password policy → automatically enforced on all users.
* Give folder access → managed centrally, not per computer.

👉 **Result:** Easy management, less manual work, scalable for growth.


### 🔹 Active Directory Domain Services (AD DS)

* **AD DS** is the **core service of Active Directory**.
* It works like a **central catalogue/database** that stores all network objects.
* These objects include: **users, computers, groups, printers, shares, etc.**

---

## 🔹 1. Users

* Users are **security principals** → they can **log in (authenticate)** and get **permissions (authorization)**.

No problem—this concept confuses a lot of people at first. Let’s make it **very simple** 👇

---

## 🔹 What is a Security Principal?

👉 A **security principal** is **anything that can be identified (login) and given permissions in a network**.

In simple words:
➡️ **“Jo login ho sakta hai aur access le sakta hai = security principal”**

---

## 🔹 Easy Analogy 🏢

Think of a company office with ID cards:

* If you have an **ID card**, you can:

  * Enter the building ✅
  * Access certain rooms ✅

👉 That ID holder = **Security Principal**

---

## 🔹 In Active Directory

Security principals are objects that:

1. Can **authenticate (login / prove identity)**
2. Can be **given permissions (access control)**

---

## 🔹 Examples

### ✅ Security Principals:

* **User accounts** → Rahul, Priya
* **Machine accounts** → `PC01$`, `DC01$`
* **Security Groups** → Domain Admins, HR Group

👉 All of these can:

* Be identified
* Be given access (files, folders, systems)

---

### ❌ Not Security Principals:

* Printers
* Shared folders
* Files

👉 Because:

* They **don’t log in**
* They are just **resources**, not identities

---

## 🔹 One-Line Definition

👉 **Security Principal = Identity + Permissions**

---

## 🔹 Real Example

* Rahul logs in → **User (security principal)**
* His PC connects → **Machine (security principal)**
* He is in HR Group → **Group (security principal)**
* He opens a file → file is **resource**, not security principal

---



### 👉 Types of Users:

* **People (Normal Users):**

  * Example: *Rahul, Priya* → employees who log into systems.
* **Service Accounts:**

  * Used by services like IIS, MSSQL.
  * Have **limited permissions** only for running that service.

---

## 🔹 2. Machines (Computers)

* Every computer joined to a domain gets a **machine account in AD**.
* Also a **security principal** (can authenticate).

### 👉 Key Points:

* Machine account name = **ComputerName + $**

  * Example: `DC01$`
* Has **limited permissions** in domain.
* Acts as **local admin on its own system**.
* Password is **auto-generated & changes regularly (very long & secure)**.

---

## 🔹 3. Security Groups

* Used to **manage permissions easily** by grouping users/machines.
* Instead of assigning rights individually → assign to group.

### 👉 Example:

* Add Rahul to “HR Group” → he automatically gets all HR access.

### 👉 Important Default Groups:

* **Domain Admins** → Full control of entire domain
* **Server Operators** → Manage Domain Controllers
* **Backup Operators** → Access all files (for backups)
* **Account Operators** → Create/modify user accounts
* **Domain Users** → All users
* **Domain Computers** → All machines
* **Domain Controllers** → All DC servers

Here’s a **clear but slightly detailed explanation** of each important default group in Active Directory:

---

## 🔹 1. Domain Admins

* **Most powerful group in the domain**
* Members have **full control over everything**

### 👉 What they can do:

* Manage all users, groups, and computers
* Access any file or system
* Control Domain Controllers (DCs)
* Install software, change policies, etc.

### 👉 Example:

If *Rahul* is in Domain Admins → he can control all 157 computers and all users.

---

## 🔹 2. Server Operators

* Can **manage Domain Controllers**, but with **limited admin rights**

### 👉 What they can do:

* Start/stop services on DC
* Manage server operations (like backups, shares)

### ❌ Limit:

* Cannot change **admin group memberships** (like Domain Admins)

### 👉 Example:

Used for IT staff who manage servers but shouldn’t get full control.

---

## 🔹 3. Backup Operators

* Special group for **backup purposes**

### 👉 What they can do:

* Access **any file**, even if permissions deny it
* Perform backup and restore operations

### ❗ Important:

* They **bypass file permissions**

### 👉 Example:

Even if Rahul denies access to a folder, Backup Operators can still read it for backup.

---

## 🔹 4. Account Operators

* Focused on **user and account management**

### 👉 What they can do:

* Create, modify, delete users and groups

### ❌ Limit:

* Cannot manage **high-privilege accounts** (like Domain Admins)

### 👉 Example:

HR IT staff can create employee accounts without full admin rights.

---

## 🔹 5. Domain Users

* **Default group for all users**

### 👉 What it means:

* Every new user is automatically added
* Has **basic access** to domain resources

### 👉 Example:

Rahul joins company → automatically part of Domain Users.

---

## 🔹 6. Domain Computers

* Contains **all computers joined to the domain**

### 👉 What it means:

* Every machine automatically becomes a member

### 👉 Example:

When a new PC joins domain → it is added here.

---

## 🔹 7. Domain Controllers

* Contains **all Domain Controller servers**

### 👉 What it means:

* Only DC machines are part of this group
* Used for applying specific policies to DCs

### 👉 Example:

DC01, DC02 → both are in this group.

---



