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
