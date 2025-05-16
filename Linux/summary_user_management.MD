# 👥 Linux User and Group Management

This guide provides step-by-step instructions for managing users and groups on a Linux system. It covers:

- Creating a user
- Setting a password
- Creating a group
- Adding a user to a group
- Changing the user's primary group
- Optional: Adding the original group as a secondary group

---

## 👤 Step 1: Create a New User

```
useradd -m newuser
```
- `-m` ensures a home directory is created at /home/newuser.
- Replace newuser with your desired username.

# 🔐 Step 2: Set a Password for the User
```
passwd newuser
```
You will be prompted to enter and confirm the password:
```
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

## 👨‍👩‍👧 Step 3: Create a New Group
```
groupadd devteam
```
- Replace devteam with the name of the group you want to create.

## ➕ Step 4: Add User to the Group (Supplementary)
```
usermod -aG devteam newuser
```
- `-aG` adds newuser to the supplementary group devteam without removing them from other groups.
To verify:
```
id newuser
```
You should see:
```
uid=1003(newuser) gid=1003(newuser) groups=1003(newuser),1004(devteam)
```

## 🔄 Step 5: Change the User’s Primary Group
To set devteam as the **primary group:**
```
usermod -g devteam newuser
```
To verify:
```
id newuser
```
Expected:
```
uid=1003(newuser) gid=1004(devteam) groups=1004(devteam)
```

## 🔁 Optional: Keep Original Group as Secondary
If the original group (e.g., newuser) should remain as a supplementary group:
```
usermod -aG newuser newuser
```
## 🛡️ Optional: Force Password Change on First Login
```
chage -d 0 newuser
```
- This will prompt the user to change their password on their first login.

## ✅ Final Checks
To confirm user details:
```
id newuser
ls -ld /home/newuser
```

## 📎 Notes
- Always use sudo if you’re not logged in as root.
- Make sure password policies are met (e.g., minimum length, complexity).
- Group IDs (gid) and user IDs (uid) may vary depending on your system.

## Remove user from a group
| **Action**                 | **Command**                                  |
|---------------------------|-----------------------------------------------|
| Check user groups         | `id username`                                 |
| Remove user from group    | `sudo gpasswd -d username groupname`          |
| Manually reassign groups  | `sudo usermod -G group1,group2 username`      |

- `group1`, `group2` are the names of groups which user want to be in, dont mention group name which user dont want to be in
- `gpasswd` is the best option to remove a user from group

