To understand:
- Modularised processes helps to reduce the compromised surface area as compared to monolithic systems
- Linux can manage modularised processes but itself is a monolithic structure

## Permissions
- Check using `ls -l /path/to/file`
- To understand output:
	- First letter: file type
		- file/directory/etc
	- owner/group/other
		- rwxs
	- number of links to this file?
		- only for distributed systems?
	- Creator (e.g. root)
	- Group name of the Creator (e.g. root)

- Types of IDs
	- EUID
		- Effective User ID
	- RUID
	- SUID
		- This is a special permission that can be set on **executable** files. When a file with the SUID bit set is executed, it runs with the effective user ID set to the owner of the file rather than the user who executed it. This is commonly used for programs that need to perform certain actions with elevated privileges, such as changing passwords or managing system settings.
		- Represented as s, such as rws instead of rwx
		- There are ways to configure what `sudo` is allowed to do/not allowed to do in the the /etc/sudoers
		- There is also a syscall `setuid` that can be invoked inside process
	- FSID

- To see other processes and how they link to each other:
	- `pstree -U`

- ACL = access control list

- 666 = 110 110 110 = rw- rw- rw-
- umask = remove permission where there is 1
	- e.g. umask 200 = 010 000 000 remove the write access from the owner

File commands:
`chown` - change owner, **only root** can since need more permission than owner
`chgrp` - change group, only owner or root can
`chmod` - change access, only owner or root can
`setfacl` - set the access control list, only owner or root can

Vulnerabilities
- Chroot to create new user files/jails
	- Need to drop the root permission after creating the jails so that users in jail cannot access other files
- Reuse file descriptors to do stuff