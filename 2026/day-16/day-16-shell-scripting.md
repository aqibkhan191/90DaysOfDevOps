# Day 16 
## Challenge Tasks

### Task 1: Your First Script
1. Create a file `hello.sh`
2. Add the shebang line `#!/bin/bash` at the top
3. Print `Hello, DevOps!` using `echo`
4. Make it executable and run it

<img width="1920" height="774" alt="image" src="https://github.com/user-attachments/assets/771c22e0-f32c-4196-9241-3cbe3efd82be" />

What Happens When You Remove the Shebang Line

The shebang (#!/bin/bash, #!/bin/sh, etc.) tells the OS which interpreter to use. Removing it has different effects depending on how you run the script:
Running with ./script.sh (direct execution)
Without a shebang, the OS has no interpreter specified. Most systems fall back to running it with /bin/sh (the system's default shell). This can cause problems if:

Your script uses bash-specific syntax ([[ ]], arrays, $BASHPID, etc.) but /bin/sh is dash or another POSIX shell
You get cryptic errors like syntax error: unexpected "(" or [[: not found

---

### Task 2: Variables
1. Create `variables.sh` with:
   - A variable for your `NAME`
   - A variable for your `ROLE` (e.g., "DevOps Engineer")
   - Print: `Hello, I am <NAME> and I am a <ROLE>`
2. Try using single quotes vs double quotes — what's the difference?




