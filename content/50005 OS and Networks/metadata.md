# File attributes
---
File attributes stored in inode in the kernel

These include:

-   **Name**:
    -   The symbolic file name is the only information kept in human readable form (stored in directory)
-   **Identifier**:
    -   This unique tag,usually a number, identifies the file within the file system; it is the non-human-readable name for the file (stored in inode, also known as inode id)
-   **Type/Format**:
    -   This information is needed for systems that support different types of files.
-   **Location**:
    -   This information is a pointer to a device and to the location of the file on that device.
-   **Size**:
    -   The current size of the file (in bytes, words, or blocks) and possibly the maximum allowed size are included in this attribute.
-   **Protection**:
-   Access-control information determines who can do reading, writing, executing, and so on.
-   **Time, date, and user identification**:
    -   This information may be kept for creation, last modification, and last use. These data can be useful for protection, security, and usage monitoring.


