# A Git-Client written in Python.

## Using
__Initialize .git in a repo:__ `python script.py init repo_path`

__Adding to the staging area:__ `python script.py add file_name1 file_name2`

__Commiting:__ `python script.py commit -m "your message"`

__Status:__ `python script.py status`

(Will be adding function for reset: to undo changes in a Git repository by moving the current branch pointer to a previous commit) 

Git stores data using an "object model," meaning every piece of information within a repository, including files, directories, and commit history, is represented as a distinct "object" with a unique identifier (hash) stored in the .git/objects directory.

### Git Object Store
It contains your original data files and all the log messages, author information, dates, and other information required to rebuild any revision or branch of the project.

Every object consists of three things- a type, a size, and content. The size is simply the size of the contents, the content depends on what type of object is, and there are four different types of objects: “blob”, “tree”, “commit”, and “tag”. Git stores these different types of objects in .git/objects.

* A “blob” is used to store file data- it is generally a file.
* A “tree” is basically like a directory- it references a bunch of other trees and blobs (i.e. files and sub-directories).
* A “commit” object holds metadata for each change introduced in the repository, including the author, committer, commit-data, and log- messages.
* A “tag” object assigns an arbitrary human-readable name to a specific object usually a commit.

### Git Index

* The index, which is a single file at .git/index, is stored in a custom binary format. It’s not exactly complicated, but it does involve a bit of struct usage, plus a bit of a dance to get to the next index entry after the variable-length path field.

* The first 12 bytes are the header, the last 20 a SHA-1 hash of the index, and the bytes in between are index entries, each 62 bytes plus the length of the path and some padding.

![alt text](<public/Screenshot 2024-12-30 at 3.00.15 AM.png>)


#### Note: The `python script.py push url --username ___ --password (github-token)` does not work properly for now.
