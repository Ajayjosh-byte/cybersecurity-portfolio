# Linux File Permissions and Access Control Audit

## Project Overview

This project demonstrates practical Linux security skills through the inspection, analysis, and modification of file and directory permissions using Bash commands.

The objective was to ensure that files and directories in `/home/researcher2/projects` followed their intended access requirements, reduce unnecessary permissions, and restrict access to sensitive project resources.

The exercise simulates a routine system administration and cybersecurity task: reviewing existing permissions and correcting access that does not align with security requirements.

## Objectives

* Inspect file and directory permissions using Linux command-line utilities.
* Identify permission settings for the owner, group, and other users.
* Include hidden files in permission reviews.
* Remove unnecessary write permissions from project files.
* Protect archived files against unauthorized modification.
* Restrict access to the `drafts` directory according to the required access policy.
* Apply the principle of least privilege.

## Tools and Technologies

* **Operating System:** Linux
* **Shell:** Bash
* **Commands:** `cd`, `ls`, `chmod`
* **Security Concepts:** Linux file permissions, access control, least privilege, permission auditing

## Project Implementation

### 1. Inspecting file and directory permissions

I navigated to the projects directory and listed its contents, including hidden files, in long format to inspect permissions, ownership, and other file details.

```bash
cd /home/researcher2/projects
ls -la
```

The long-format listing displays the permission string, owner, group, file size, modification date, and filename.

### 2. Understanding Linux permission strings

Linux permissions are represented by ten characters.

Example:

```text
-rwxr-xr--
```

* **Character 1:** File type (`d` for directory and `-` for a regular file).
* **Characters 2–4:** Owner permissions.
* **Characters 5–7:** Group permissions.
* **Characters 8–10:** Permissions for other users.

The permission symbols are:

| Symbol | Meaning                                     |
| ------ | ------------------------------------------- |
| `r`    | Read                                        |
| `w`    | Write                                       |
| `x`    | Execute; for directories, permits traversal |
| `-`    | Permission not granted                      |

### 3. Removing unnecessary write access

I reviewed the permissions of `project_k.txt` and removed write permission for other users.

```bash
chmod o-w project_k.txt
```

This prevents users outside the file's owner and group from modifying the file through its permission settings.

### 4. Securing a hidden archived file

I used the `chmod` utility to adjust the permissions of a hidden project file, ensuring that the owner and group retained read access without write access.

```bash
chmod u+r-w,g+r-w .project_x.txt
```

This command adds read permission and removes write permission for the owner and group.

**Security consideration:** If the requirement is to prevent everyone from writing to the archived file, the more appropriate command is:

```bash
chmod a-w .project_x.txt
```

This removes write permission for the owner, group, and other users while preserving their existing read and execute permissions.

### 5. Restricting access to the drafts directory

I removed execute permission for the group from the `drafts` directory.

```bash
chmod g-x drafts
```

Directory execute permission controls traversal. Removing it from the group prevents group members from traversing the directory through that permission.

The initial permissions were:

```text
drwx--x---
```

After removing group execute permission, they become:

```text
drwx------
```

With these permissions, only the directory owner has read, write, and execute permissions. This meets the intended restriction when the owner is `researcher2` and the directory has no additional access-control-list entries granting access to other users.

### 6. Verifying permission changes

I used the following commands to verify the resulting permissions:

```bash
ls -l project_k.txt
ls -la
ls -ld drafts
```

Verification is an important part of access control administration because it confirms whether the intended permission changes have been applied.

## Security Concepts Demonstrated

* **Principle of Least Privilege:** Granting only the permissions needed for a user or group to perform its intended tasks.
* **Access Control:** Managing who can read, modify, or traverse files and directories.
* **Permission Hardening:** Removing unnecessary write and execute permissions to reduce opportunities for unauthorized actions.
* **Hidden-File Security:** Recognizing that hidden filenames do not provide security; actual protection depends on permissions and access controls.
* **Verification and Auditing:** Reviewing permissions before and after applying changes.

## Evidence

The Bash terminal screenshot included with this project documents the Linux commands used during the exercise and provides visual evidence of the permission-auditing workflow.

![Linux file permissions audit terminal screenshot](screenshots/file-permissions-audit.png)

*Replace the image path above with the actual path and filename of the screenshot uploaded to this repository.*

## Key Learning Outcomes

Through this exercise, I strengthened my ability to inspect Linux permissions, interpret permission strings, modify access settings with `chmod`, and verify the effects of security changes. I also gained practical experience applying least-privilege principles to file and directory access.

## Conclusion

This project demonstrates a foundational cybersecurity skill: managing Linux file permissions to reduce unnecessary access and protect system resources. These skills are relevant to Linux system administration, security operations, access control reviews, and entry-level cybersecurity analyst responsibilities.

**Author:** Ajay Josh

**Focus Areas:** Cybersecurity | Linux | Bash | Access Control | Security Hardening

## Evidence

![Linux File Permissions Audit](screenshots/linux-permissions-audit.png)
