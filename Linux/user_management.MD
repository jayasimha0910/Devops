## **User Management**
-----
## **1. Creating and Deleting Users in Linux**

In Linux, creating and deleting users can be done using commands such as `useradd`, `userdel`, and checking user details with the `id` or `cat /etc/passwd` command.


### **Creating a User**

To create a new user on your system, you can use either of the following commands:

#### **1. `useradd` Command:**
```sh
useradd username
```

#### **2. `adduser` Command:**
In some Linux distributions (like Debian-based systems), `adduser` is a more user-friendly script for creating users.
```sh
adduser username
```

#### **Explanation:**
- **`username`** → This is the name of the user you want to create.

Both commands create a new user, but `adduser` is typically more interactive and sets up additional configuration like password and home directory automatically.


### **Check If the User is Created**

To verify if the user has been created successfully, you can use the following commands:

#### **1. `id` Command:**
```sh
id username
```
This command will display the user ID (UID), group ID (GID), and the groups the user belongs to.

#### **2. `/etc/passwd` File:**
```sh
cat /etc/passwd | grep username
```
This command checks the `/etc/passwd` file, which stores information about all users on the system. If the user exists, you will see an entry for them.

### **Deleting a User**

To remove a user, you can use the `userdel` command.

#### **1. `userdel` Command:**
```sh
userdel username
```

This deletes the user but **does not** remove their home directory.

#### **2. `userdel -r` Command:**
```sh
userdel -r username
```

#### **Explanation:**
- **`-r`** → Removes the user's home directory and mail spool along with the user. This is useful to clean up all user-specific files.

### **Example Usage:**

#### **Create a User:**
```sh
useradd john
```

#### **Verify User Creation:**
```sh
id john
```

#### **Delete a User:**
```sh
userdel -r john
```

### **Note:**
- The `userdel` command will not remove files or directories owned by the user if they are elsewhere on the system. Use with caution, and always double-check before removing user accounts.
- **`-r`** is crucial if you want to remove all files associated with the user, including their home directory and mail spool.

### **Summary:**

| Command | Action |
|---------|--------|
| `useradd username` | Creates a user without additional options. |
| `adduser username` | Creates a user with additional prompts (interactive). |
| `id username` | Verifies user creation and shows UID, GID, and groups. |
| `cat /etc/passwd | grep username` | Checks the `/etc/passwd` file for the user entry. |
| `userdel username` | Deletes the user (but keeps the home directory). |
| `userdel -r username` | Deletes the user and removes their home directory and mail spool. |

----

## **Creating, Deleting Groups, and Managing User Group Memberships in Linux**

In Linux, managing user groups is essential for organizing users and controlling access to resources. This is done using the `groupadd`, `groupdel`, and `usermod` commands. Let's break them down in detail.

### **1. Creating a Group**

To create a new group in Linux, use the `groupadd` command.

#### **Syntax:**
```sh
groupadd group_name
```

#### **Example:**
```sh
groupadd developers
```
This command creates a new group named `developers`.

### **2. Checking if a Group Exists**

To verify that a group has been created, you can check the `/etc/group` file, which contains all group information on the system.

#### **Command:**
```sh
cat /etc/group
```

This will display a list of all groups on the system, including their names, group IDs (GID), and associated users.

### **3. Deleting a Group**

If you need to delete a group, use the `groupdel` command.

#### **Syntax:**
```sh
groupdel group_name
```

#### **Example:**
```sh
groupdel developers
```

This will remove the `developers` group from the system.

**Note:** You cannot delete a group if it is the primary group of any existing users. You will need to change their group first before deleting the group.

### **4. Adding Users to a Group**

You can add existing users to a group using the `usermod` command. To avoid removing the user from other groups, use the `-a` flag (append) with the `-G` flag.
`-aG` means: append `-a` the user to the supplementary group `-G` without removing them from existing groups.

#### **Syntax:**
```sh
usermod -a -G group_name user_name
```

#### **Example:**
```sh
usermod -a -G developers john
```
This command adds the user `john` to the `developers` group, while preserving any other group memberships `john` might have.

### **Summary of Commands:**

| Command                       | Action                                       |
|-------------------------------|----------------------------------------------|
| `groupadd group_name`          | Creates a new group.                         |
| `cat /etc/group`               | Lists all groups and their members.          |
| `groupdel group_name`          | Deletes a group.                             |
| `usermod -a -G group_name user_name` | Adds a user to an existing group without removing them from other groups. |

### **Example Use Case:**

1. **Create a group:**
   ```sh
   groupadd admins
   ```

2. **Verify group creation:**
   ```sh
   cat /etc/group
   ```

3. **Add a user to the group:**
   ```sh
   usermod -a -G admins alice
   ```

4. **Delete a group:**
   ```sh
   groupdel admins
   ```

### **Important Notes:**
- **`usermod -a -G`** is essential when adding users to groups because using **`-G`** without **`-a`** will **replace** the current group membership instead of **appending** to it.
- You cannot delete a group if there are users whose primary group is that group. You would need to reassign their primary group to another one before deleting the group.


### **Changing user primary group**

1. **Create the Group (if not already created)**
```
groupadd devteam
```
