<h1 align="center">Task No. 3: File Organizer</h1>

This Python script organizes files in a specified directory based on their file extensions. When executed, it prompts the user to input a directory path, then it categorizes all the files in that directory into subdirectories named after their respective file extensions.

## How It Works

1. **Prompt for Directory Path:** The script starts by asking the user to enter the path of the directory that needs to be organized.
2. **List Files:** It then lists all the files present in the specified directory.
3. **Organize Files:** For each file in the directory:

   - The script extracts the file extension.
   - If a subdirectory named after the file's extension already exists, the file is moved into that subdirectory.
   - If such a subdirectory does not exist, it creates the subdirectory and then moves the file into it.

## Code Explanation

Here's a step-by-step explanation of the `file_organizer.py` script:

**1. Import Libraries:**

- `os`: Provides functions to interact with the operating system.
- `shutil`: Offers a number of high-level operations on files and collections of files.

```
import os
import shutil
```

**2. Prompt User for Directory Path:**

- Asks the user to input the path of the directory to organize.

```
path = input("Please enter the path: ")
```


**3. List All Files in the Directory:**

- Retrieves a list of all files in the specified directory.

```
files = os.listdir(path)
```

**4. Iterate Over Each File:**

- Loops through each file and splits the file name from its extension. Removes the leading dot from the extension.

```
for file in files:
    filename, extension = os.path.splitext(file)
    extension = extension[1:]
```

**5. Organize Files into Directories:**

- Checks if a directory for the file extension exists:

    - If it does, moves the file into this directory.
    - If it doesn't, creates a new directory for the extension and then moves the file into it.

```
if os.path.exists(path + '/' + extension):
    shutil.move(path + '/' + file, path + '/' + extension + '/' + file)
else:
    os.makedirs(path + '/' + extension)
    shutil.move(path + '/' + file, path + '/' + extension + '/' + file)
```
### Note

- The script only organizes files at the top level of the specified directory. It does not recursively organize files within subdirectories.
- Ensure you have the necessary permissions to read, write, and create directories in the specified path.
