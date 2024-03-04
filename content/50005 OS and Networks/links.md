# Links
---
We can have different names for the same file by adding more than one entries pointing to the **same inode** 

## Purpose
---
Hard links are important to organize stuff without copying
Imagine having photos in your system, thousands of them. You want to **categorize** them for easier access.

-   You can categorize them as: photos of red things, photos of blue things, photos of green things.
-   You can also categorize them as: photos of vehicles, photos of trees, photos of flowers

Suppose you want to categorize them both ways. What you can do: **Method 1**: You could create a **copy** of the photos and categorize it multiple times in the way you want it.

-   This means you have two copies of the same file taking up two times the space.
-   It is not ideal to do this, especially with large amounts of data.

**Method 2**: Create hard links.

-   A hard link takes up almost no space at all. Y
-   ou could, therefore, store the same photo in various different categories (i.e. by color, by type, etc).

A symbolic link is much like a desktop **shortcut** within Windows. The symbolic link merely points to the location of a file. We have all been using it.

## Hard Links
---
Each hardlink is a pointer to the same file, but with different name. Everytime you create a hard link, reference count will increase by one. If you delete one file, must delete all of its corresponding files by changing the reference count to 0

Note that you **cannot** create hard links for directories, only can do that for files. This is a design choice to **prevent cycles**. We wanna have acyclic structures in directory tree so that 
- we wont end up looping in a loop de loop during graph traversal when searching for a file.
- Make it easier to delete files (files are deleted when reference count is set to 0)

Note that hard links is not copy! Copy will result in double entries in the inode table

## Soft Links
---
Also known as shortcuts, or symbolic links
It is another file that contains the path of actual file. The OS will  **automatically interprets** that content inside to open that actual file.
Now, you can link directories with symbolic links! Hooray, you still have only one path to a file

Example
`ln -s input input softlink`
You will get a different id as compared to the original file

**Broken Symlink**
its like a dangling pointer, when you delete the file that the symbolic link is pointing to

#os