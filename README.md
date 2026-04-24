# Project Infinity X - Non-ARB Flashing Guide

Flashing instructions for the **Non-ARB build** of **Project Infinity X** on the **OnePlus Nord CE 3 Lite 5G (`larry`)**.

> [!IMPORTANT]
> Read every step carefully before flashing.
>
> - Non-ARB build
> - This process will wipe all data
> - Follow the guide exactly

## Warning

> [!WARNING]
> **Do not flash this build if your device is on OOS firmware `1600` or `1301`.**
>
> - These firmware versions are known to trigger the **ARB (Anti Rollback) fuse**
> - Flashing this Non-ARB build on those firmwares can result in a **hard brick**
> - If your device is affected by ARB, use the ARB-safe build instead

If you need the **ARB-safe build**, use:

- [Project Infinity X ARB-Safe Releases](https://github.com/imCrest/Infinityx-Release)

## Downloads

- ROM: [Latest Release](https://github.com/imCrest/Infinityx-Release-NonArb/releases/latest)
- Mirror links: Available in official Telegram release posts

### Files You Need

Download these files before starting:

- ROM zip (`GApps` or `Vanilla`)
- `boot.img`
- `vendor_boot.img`
- `dtbo.img`

## Requirements

- Backup all important data
- Unlocked bootloader
- PC with ADB and Fastboot installed
- USB drivers for your device
- USB cable
- Make sure your device is **not** on OOS `1600` or `1301`

## Step 1: Enable Developer Options

1. Open **Settings** -> **About Phone**
2. Tap **Build Number** 7 times
3. Go to **Developer Options**
4. Enable:
   - **USB Debugging**
   - **OEM Unlocking**

## Step 2: Verify Device Connection

```bash
adb devices
```

## Step 3: Reboot to Bootloader

```bash
adb -d reboot bootloader
```

## Step 4: Unlock Bootloader

```bash
fastboot flashing unlock
```

- Confirm the unlock on your device
- Your device will wipe data and reboot automatically

## Step 5: Enter Fastboot Mode Again

After the device reboots:

- Power off the device
- Hold **Volume Down + Power** to enter fastboot mode again

## Step 6: Flash Required Partitions

```bash
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot flash dtbo dtbo.img
```

## Step 7: Reboot to Recovery

```bash
fastboot reboot recovery
```

## Step 8: Format Data

In recovery:

- Select **Factory Reset** or **Format Data**

## Step 9: Sideload the ROM

On your phone:

- Go to **Apply Update**
- Select **Apply from ADB**

Then run:

```bash
adb -d sideload <your-rom.zip>
```

## Step 10: Additional Packages If Prompted

- If recovery asks for additional packages, select **Yes**

## Step 11: Reboot to System

- Select **Reboot to System**

## Notes

- First boot can take several minutes
- Always confirm that your firmware is safe before flashing
- Double-check all files before starting
- Flash at your own risk

## Done

Your device should now boot into **Project Infinity X**.
