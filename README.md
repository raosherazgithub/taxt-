## Found the Issue!

Your VDI virtual capacity is already **82015 MB (~80 GB)** but only **24 GB is actually used** on disk. So Kali already has 80 GB allocated virtually!

---

## The Real Problem is Inside Kali

The VDI is big enough, but **Kali's partition hasn't been extended** to use all that space. You need to fix this inside Kali.

---

## ⚠️ Also — VM is Still Running!

The output shows:
```
In use by VMs: kali-linux-2026.1-virtualbox-amd64
```
**Shut down Kali completely first** before doing anything!

---

## Fix: Extend Partition Inside Kali

Boot into Kali, open terminal and run:

```bash
# Check current disk layout
lsblk

# Install GParted
sudo apt install gparted -y

# Open GParted GUI
sudo gparted
```

In GParted:
1. You'll see your main partition with **lots of unallocated space** next to it
2. Right-click main partition → **Resize/Move**
3. Drag the arrow to the **far right** to use all space
4. Click **Apply**

---

## Quick Check Inside Kali Terminal

Run this to confirm how much space Kali sees:

```bash
df -h
lsblk
```

**Boot into Kali and share the output of `lsblk`** — that will show exactly what needs to be extended! 🎯
