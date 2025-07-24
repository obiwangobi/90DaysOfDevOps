# Task 2: File and Directory Permissions

## Objective

1. Create a directory `/devops_workspace` and a file `project_notes.txt` inside it.
2. Set permissions so that:
   - The **owner** can read and write (edit).
   - The **group** can only read.
   - **Others** have no access.
3. Verify the permissions using `ls -l`.

---

## 1. Creating a a directory `/devops_workspace` and a file `project_nots.txt` inside it.

### Creating a directory

To create the directory use the following command

```bash
mkdir devops_workspace
```
### creating a file

To create the file use can use one of the follwing command

```bash 
touch project_notes.txt
```

```bash
vim projec_notes.txt
```

- using vim will directly open an editor with a file name "project_notes.txt"

---

## 2 setting permission to the file

Use the following command to set:

The **owner** can read and write (edit).
   - The **group** can only read.
   - **Others** have no access.

``` bash 
chmod 640 project_notes.txt
```
## verifying the permission

use the command 

```bash
ls -l
```

output will be 

```bash
-rw-r----- 1 devops_user devops_team 0 Jul 24 12:22 devops_workspace/project_notes.txt
```


