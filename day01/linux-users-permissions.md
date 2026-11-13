# Linux Users, Groups and Permissions

## What I learned
- /etc/passwd: it contains the list of users, their UID, GID, home directory and shell to name a few
- /etc/group: contains list of group and info about the group including but not limited to GID and members of the group
- /etc/shadow: holds the password hashes and aging info, root-only. The x in /etc/passwd means ‘look in shadow’

## Commands I used
| Command | What it does |
|---|---|
| useradd -m user | Creates a new user and a home directory |
| usermod -aG group user | Adds user to existing group |
| gpasswd -d user group | removes user from group |
| visudo -f /etc/sudoers.d/name | Opens a drop-in file in a text editor, checks syntax by default before saving to flag errors and avoid locking the user's access |

## Permissions
- rwx = 4/2/1, owner/group/others
- 4th digit(leading): setuid - the file runs with owner’s privilege (root only if root owns it). Compiled binaries only, ignored on scripts, setgid - new file inherits directory's group, sticky - applies in a in a directory like /tmp, only a file’s owner (or root) can delete or rename files.. 
- umask: decides/controls what the initial permission a file gets after creation

## Things that confused me
- I need `x` permission on every directory on the path of the file or the file's own permissions are never checked.

## Still unsure
- regex pattern in file manipulation

## My experiments
- chmod 4664 on an empty file: `ls -l` showed capital `S`, not `s`.
  Why: setuid needs the owner's `x` underneath it to show lowercase.
- bob got "Permission denied" on /home/alice/alice-file even though the
  file was 664 with group devs. Why: /home/alice was 750 and bob had
  no `x` on the directory. Nano opened a blank buffer, which looked
  like success but wasn't.
- `sudo su - alice` worked without alice's password. Why: root is never
  asked for the target user's password.
