# Android Virtual Machine Setup & Network Connectivity Testing

## 📌 Project Overview

This project documents the installation and configuration of an Android virtual machine using **Android-x86 9.0 (64-bit)** on Oracle VirtualBox.

The lab was created to explore Android virtualization, configure static IP addressing, and establish network communication between an Android virtual machine and a Kali Linux virtual machine.

The project also involved testing internet connectivity and verifying communication between both virtual machines using ICMP (ping).

## 🎯 Objectives

- Download and install Android-x86 9.0 (64-bit) on VirtualBox.
- Configure the virtual machine's hardware and network settings.
- Install Android-x86 onto a virtual hard disk.
- Configure a static IP address on the Android virtual machine.
- Test internet connectivity using Google's public DNS IP address.
- Establish communication between Android and Kali Linux.
- Verify connectivity using ICMP ping tests.

## 🛠️ Tools & Technologies

| Tool | Description |
|---|---|
| Ubuntu | Host operating system |
| Oracle VirtualBox | Virtualization platform |
| Android-x86 9.0 (64-bit) | Android operating system ISO |
| Kali Linux | Second virtual machine used for connectivity testing |
| ICMP / Ping | Network connectivity testing |
| NetworkManager | Network configuration on Kali Linux |

## 💻 Virtual Machine Configuration

The Android virtual machine was configured with the following specifications:

| Component | Configuration |
|---|---|
| Operating System | Android-x86 9.0 (64-bit) |
| RAM | 4096 MB (4 GB) |
| Processors | 2 CPUs |
| Virtual Disk | 10 GB |
| Disk Format | VDI |
| Storage Allocation | Dynamically allocated |
| Graphics Controller | VMSVGA |
| Video Memory | 128 MB |
| 3D Acceleration | Disabled |
| Network Adapter | NAT Network |

## ⚙️ Lab Implementation

### 1. Download Android-x86 ISO

Downloaded the Android-x86 9.0 (64-bit) ISO image to use as the installation media for the virtual machine.

### 2. Create the Virtual Machine

Created a new virtual machine in Oracle VirtualBox and configured the following:

- Allocated 4096 MB of RAM.
- Assigned 2 virtual CPUs.
- Created a 10 GB VDI virtual hard disk.
- Selected dynamically allocated storage.

### 3. Configure VirtualBox Settings

Before starting the virtual machine, the following settings were adjusted:

**Display Settings**
- Graphics Controller: VMSVGA
- Video Memory: 128 MB
- 3D Acceleration: Disabled

**Network Settings**
- Attached the network adapter to NAT Network.

**Storage Settings**
- Mounted the Android-x86 9.0 ISO image to the virtual optical drive.

### 4. Install Android-x86

Booted the virtual machine and selected:

`Installation - Install Android-x86 to harddisk`

The following installation procedure was performed:

1. Selected **Create/Modify partitions**.
2. Selected **No** when prompted to use GPT.
3. Created a new primary partition.
4. Marked the partition as bootable.
5. Selected Write and confirmed by typing `yes`.
6. Selected Quit to return to the installation menu.
7. Selected the newly created `sda1` partition.
8. Formatted the partition using the **ext4** filesystem.
9. Confirmed installation of the GRUB bootloader.
10. Allowed the `/system` directory to be mounted as read-write.
11. Selected Reboot after installation.
12. Removed the mounted ISO image before booting into the installed Android system.

### 5. Configure Android Static IP Address

After successfully installing Android-x86, I configured a static IP address on the Android virtual machine.

This was necessary to establish predictable network communication between Android and Kali Linux.

The static IP configuration was performed using the Android network settings.

<sub>Screenshot: Android static IP configuration</sub>

![Android Static IP Configuration](images/android-static-ip.png)

### 6. Test Internet Connectivity

After configuring the Android network settings, I tested connectivity to Google's public DNS IP address using:

```bash
ping 8.8.8.8
```

This test was performed to verify whether the Android virtual machine could reach an external IP address.

<sub>Screenshot: Android internet connectivity test</sub>

![Android Internet Connectivity Test](images/android-ping-8.8.8.8.png)

### 7. Test Connectivity Between Android and Kali Linux

The next stage involved verifying communication between the two virtual machines.

**Test 1: Android to Kali Linux**

From the Android virtual machine, I pinged the Kali Linux IP address:

```bash
ping 10.0.0.2
```

This was used to verify connectivity from Android to Kali Linux.

**Test 2: Kali Linux to Android**

From the Kali Linux terminal, I pinged the static IP address configured on Android:

```bash
ping <ANDROID_STATIC_IP>
```

Successful replies confirmed that the two virtual machines could communicate over the configured virtual network.

<sub>Screenshot: Android-to-Kali connectivity test</sub>

![Android to Kali Connectivity](images/android-to-kali-ping.png)

<sub>Screenshot: Kali-to-Android connectivity test</sub>

![Kali to Android Connectivity](images/kali-to-android-ping.png)

## 📊 Results & Observations

The lab demonstrated the successful installation and configuration of an Android virtual machine within Oracle VirtualBox.

The following activities were completed:

- Successfully installed Android-x86 9.0 (64-bit).
- Configured the virtual machine's hardware resources.
- Configured a static IP address on Android.
- Tested external IP connectivity using `8.8.8.8`.
- Tested network communication between Android and Kali Linux.
- Performed bidirectional ICMP connectivity tests.

## 📚 Skills Acquired

Through this practical exercise, I gained experience in:

- Virtual machine creation and configuration.
- Android operating system installation.
- Virtual networking using VirtualBox NAT Network.
- Static IP addressing.
- Network connectivity troubleshooting.
- ICMP and ping-based network diagnostics.
- Communication testing between different operating systems.




This repository documents my practical learning journey in virtualization, networking, cybersecurity lab environments, and security operations.

---

*Hands-on learning. Practical experience. Continuous improvement.*
