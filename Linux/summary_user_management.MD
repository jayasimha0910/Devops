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
- -m ensures a home directory is created at /home/newuser.
- Replace newuser with your desired username.
