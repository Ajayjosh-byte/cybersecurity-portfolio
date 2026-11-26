
# Python Automation: Updating an IP Address Allow List

## Project Overview

This project demonstrates how Python can automate the process of updating an IP address allow list by removing addresses that are no longer authorized to access restricted resources.

The exercise uses Python file-handling operations, conditional statements, loops, and list methods to automate access-list maintenance.

## Problem Statement

An organization uses an `allow_list.txt` file to identify IP addresses permitted to access restricted content.

A separate `remove_list` contains IP addresses that should no longer have access.

Manually checking and removing these addresses can be repetitive. The objective of this project is to develop a Python algorithm that automates the update process.

## Objectives

- Read an existing allow list from a text file.
- Convert file contents into a manageable Python list.
- Iterate through a list of IP addresses requiring removal.
- Check whether each address exists before removing it.
- Update the original file with the revised list.

## Tools and Technologies

- Python 3
- File handling (`open()`, `read()`, `write()`)
- Context managers (`with`)
- String methods (`split()` and `join()`)
- Lists and list methods (`remove()`)
- Conditional statements (`if`)
- Iteration (`for` loops)

## Implementation

### 1. Identify the file

```python
import_file = "allow_list.txt"
```

### 2. Read the file contents

```python
with open(import_file, "r") as file:
    ip_addresses = file.read()
```

### 3. Convert the string into a list

```python
ip_addresses = ip_addresses.split()
```

### 4. Remove unauthorized IP addresses

```python
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```

The conditional statement prevents Python from attempting to remove an address that does not exist in the allow list.

### 5. Convert the revised list into a string

```python
ip_addresses = "\n".join(ip_addresses)
```

### 6. Update the original file

```python
with open(import_file, "w") as file:
    file.write(ip_addresses)
```

## Complete Algorithm

```python
def update_file(import_file, remove_list):

    # Read the allow list
    with open(import_file, "r") as file:
        ip_addresses = file.read()

    # Convert the string into a list
    ip_addresses = ip_addresses.split()

    # Remove addresses that are no longer authorized
    for element in remove_list:
        if element in ip_addresses:
            ip_addresses.remove(element)

    # Convert the revised list back into a string
    ip_addresses = "\n".join(ip_addresses)

    # Rewrite the allow list
    with open(import_file, "w") as file:
        file.write(ip_addresses)
```

## Security Relevance

Maintaining an accurate allow list is an important access-control practice. Removing IP addresses that are no longer authorized helps reduce unnecessary access to restricted resources.

This exercise demonstrates how scripting can support repetitive security administration tasks and improve consistency.

## Key Learning Outcomes

Through this exercise, I strengthened my understanding of:

- Python file operations and resource management.
- Reading and writing text files.
- Converting strings into lists and lists into strings.
- Using loops to process multiple records.
- Applying conditional logic before modifying data.
- Automating a basic access-control maintenance task.

## Project Scope and Limitations

This is a guided Python learning exercise demonstrating allow-list maintenance. It does not represent a production network deployment or a live security incident investigation.

The algorithm assumes that the allow-list entries are separated by whitespace and that duplicate entries are not present.

Production implementations should include input validation, error handling, backups, logging, and appropriate authorization before modifying access-control records.

## Conclusion

This project strengthened my practical understanding of Python automation and its application to cybersecurity tasks, particularly access-control administration.

I continue to build my technical foundation through hands-on exercises and practical cybersecurity projects.
