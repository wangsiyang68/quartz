## Directory
---
Directories are **special files** that are interpreted/executed by the [[Operating Systems]]. It contains the names of other files or other directories, and their IDs 1 level inside (so like it wont contain the entire universe)
- Thats why you can read but cannot edit the files that are managed by another file system, because the directories are written differently as they are supposed to work with different OS

Closely related to the Path, which is a logical namespace

Step by step process of what happens when double click on the file:
the id of the file is requested
os will look into inode which entry has the id
that entry will contain the address

#os