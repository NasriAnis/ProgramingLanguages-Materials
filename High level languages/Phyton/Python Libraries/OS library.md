### 1. What does `os.path.exists(CONTACTS_FILE)` do?

- The **`os`** module lets Python interact with your operating system (Windows, Linux, etc.).
    
- `os.path.exists("contacts.txt")` checks if a file with that name already exists in the same folder as your script.
    
    - If yes → it returns `True`.
        
    - If no → it returns `False`.
        

So in `load_contacts()`, this line means:  
👉 _“If the file `contacts.txt` already exists, then open it and read its content. If not, just skip and return an empty list.”_

---

### 2. What does `with open(CONTACTS_FILE, "r") as f:` mean?

This is how you **open a file** in Python.

- `"r"` means **read mode** → you can only read from the file.
    
- `with ... as f:` is a special Python way of opening files safely.
    
    - It automatically closes the file when finished.
        
    - You don’t need to call `f.close()` manually.
        

Here `f` is a variable representing the open file. You can now loop through it line by line.

---

### 3. Reading from a file

Inside `load_contacts()`:

`for line in f:     name, phone, email = line.strip().split(",")`

- `for line in f:` → read the file line by line.
    
- Example of a line:
    
    `Alice,123456789,alice@gmail.com`
    
- `line.strip()` → removes the `\n` (new line at the end).
    
- `.split(",")` → cuts the line into 3 parts: `[name, phone, email]`.
    

So this line turns into:  
`"Alice,123456789,alice@gmail.com"` → `["Alice", "123456789", "alice@gmail.com"]`

---

### 4. Writing to a file

In `save_contacts(contacts)`:

`with open(CONTACTS_FILE, "w") as f:     for c in contacts:         f.write(f"{c['name']},{c['phone']},{c['email']}\n")`

- `"w"` means **write mode**. ⚠️ Important: it **erases the old content** before writing the new one.
    
- `f.write(...)` adds text to the file.
    
- `\n` means “go to next line”.
    

So if you have 2 contacts, the file `contacts.txt` will look like:

`Alice,123456789,alice@gmail.com Bob,987654321,bob@gmail.com`

---

### 5. Appending instead of rewriting

If instead of erasing the file each time you want to **add at the end**, you would use `"a"` (append mode):

`with open(CONTACTS_FILE, "a") as f:     f.write("New Contact,111222333,new@example.com\n")`

This adds a new line at the end, without deleting the old ones.

---

### 6. Summary of file modes

Here are the most useful modes for `open()`:

- `"r"` → read (error if file doesn’t exist).
    
- `"w"` → write (creates file if it doesn’t exist, but erases content if it does).
    
- `"a"` → append (creates file if it doesn’t exist, adds at end if it does).
    
- `"r+"` → read & write (file must exist, doesn’t erase content).
    
- `"w+"` → read & write (but erases old content).
    
- `"a+"` → read & append.
    