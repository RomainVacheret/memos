# Linux permissions

* All the information about users are stored in `/etc/passwd` 
  * Owned by `root`
  * Has permission `644`
  * Information's format:
    * username
    * password (usually set to `x`)
    * uid (user id)
    * gid (group id)
    * GECOS (comma-separated fields containing information about the user)
    * home directory
    * shell
* User's shell can be set to `/sbin/false` to unable the user to login
  * Similarly: `/sbin/nologin`

## Files permission
* Permission values:
  * Read: `r`
  * Write: `w`
  * Execute: `x`
  * Set as `-` if not attributed
* Octal notation
    ```
        Octal    Binary  File mode
        0        000     ---
        1        001     --x
        2        010     -w-
        3        011     -wx
        4        100     r--
        5        101     r-x
        6        110     rw-
        7        111     rwx
    ```
* 3 categories of entities:
  * The owner
    * Permissions will apply only to himself
  * The group
    * Permissions will apply to every user of the group
  * Others
    * Permissions will apply to anyone different from the user and not belonging to the group
   
### Display permissions with `ls -l`
* Example : 
    ```sh
        drwxr-xr-x    1 root     root           4096 Jan 01 00:00 aDirectory
        -rw-------    1 aUser aGroup            224  Jan 01 00:00 aFile
    ```
* Returns a list of lines composed of 7 fields:
  * File permission
    * First caracter specifies the type of the file:
      * `-`: normal
      * `d`: directory
      * `s`: socket
      * `l`: link
    * Then follow 9 caracteres:
      * Each group of 3 specifies the values listed above (in the same order)
      * In order, each group represents the entities listed above (in the same order)
  * Number of links
  * Owner
  * Group
  * Size
    * In bytes
  * Last modified date and time
  * File name
  
### Change permissions with `chmod`
* Allows you to change permissions of a file 
* Syntax:
  * `chmod <entity><modifier><permission> <file_name>`
  * `chmod <octal_notation> <file_name>`
* Modifiers are:
  * add: `+`
  * remove: `-`
  * assign: `=`
* Entities are represented by their first letter:
  * User: `u`
  * Group: `g`
  * Others: `o`
* Entities can be combined, example:
    ```sh 
        chmod ugo+rwx file.txt
        chmod u=rwx,g=rw,o=x
        chmod ug+rw,o-x file.txt
    ```
  
### Change owner with `chown`
* Allows you to change the ownership of a file
  * `chown <user_name> <file_name>`
* But also the group
  * `chown <user_name>:<group_name <file_name>`
* To set the group to default, put nothing after the `:`
* To only change the gorup, put nothing before the `:`
* To change the ownership of a folder recursively, use `-R`