### **Summary: Syncing Between Local and Google Drive Using Rclone**

#### **1. Sync Local to Google Drive**

To sync `D:\Books` to Google Drive’s `Ebook` folder (making them identical):

```bash
rclone sync D:\Books gdrive:Ebook --progress
```

⚠ **Warning**: Files **not in `D:\Books`** will be **deleted** from `gdrive:Ebook`.

#### **2. Reverse Sync (Google Drive to Local)**

To sync `gdrive:Ebook` back to `D:\Books`:

```bash
rclone sync gdrive:Ebook D:\Books --progress
```

⚠ **Warning**: This deletes files in `D:\Books` that **aren’t in** `gdrive:Ebook`.

#### **3. Safe Mode (Test First)**

Before making actual changes, preview them using:

```bash
rclone sync gdrive:Ebook D:\Books --dry-run --progress
```

#### **4. Copy Instead of Sync (No Deletion)**

To **only update** files without deleting anything:

```bash
rclone copy D:\Books gdrive:Ebook --progress
```

For reverse copy (Google Drive to local):

```bash
rclone copy gdrive:Ebook D:\Books --progress
```

#### **5. Check Google Drive Contents Before Syncing**

```bash
rclone ls gdrive:Ebook
```

Would you like help automating this process with scheduled syncs? 🚀