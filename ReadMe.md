# Visual Studio Code Setup Guide

This guide helps you extract, transfer, and install Visual Studio Code (VS Code) extensions and settings on another machine.

---

## Extracting and Backing Up VS Code Extensions

To export your installed extensions:

1. Open a terminal or PowerShell.
2. Run the following command to list all installed extensions and save them to a file:
   ```bash
   code --list-extensions > extensions.txt
   ```
3. This creates a file named `extensions.txt` in the current directory, containing all your installed extensions.

---

## Backing Up VS Code Settings

To export your `settings.json`:

1. Locate the `settings.json` file:
   - Path on Windows:
     ```plaintext
     C:\Users\<YourUsername>\AppData\Roaming\Code\User\settings.json
     ```
2. Use the following PowerShell command to copy the `settings.json` to your current directory:
   ```powershell
   Copy-Item "$env:APPDATA\Code\User\settings.json" -Destination .\settings.json
   ```
3. This saves the `settings.json` file in the current directory.

---

## Transferring to a New Machine

### Prerequisites:
1. Install Visual Studio Code on the new machine from [code.visualstudio.com](https://code.visualstudio.com/).
2. Copy the `extensions.txt` and `settings.json` files to the new machine.

---

## Installing Extensions on the New Machine

To install extensions from the exported `extensions.txt`:

1. Open a terminal or PowerShell.
2. Navigate to the folder containing `extensions.txt` (e.g., `cd <path-to-file>`).
3. Run the following command to install all extensions listed in `extensions.txt`:
   ```powershell
   Get-Content extensions.txt | ForEach-Object { code --install-extension $_ }
   ```

---

## Importing Settings

To restore your `settings.json`:

1. Copy the `settings.json` file to the following directory:
   ```plaintext
   C:\Users\<YourUsername>\AppData\Roaming\Code\User\settings.json
   ```
2. Restart Visual Studio Code.

---

## Verification

1. Open VS Code.
2. Press `Ctrl+Shift+X` to open the Extensions view.
3. Verify that all extensions are installed.
4. Confirm that your settings have been applied.

---

## Notes
- Ensure the VS Code CLI (`code`) is added to your PATH. You can verify this by running `code --version` in the terminal.
- If any extensions fail to install, try running the command again or check for typos in the `extensions.txt` file.

---

With these steps, you can seamlessly set up VS Code with your preferred extensions and settings on any machine!

