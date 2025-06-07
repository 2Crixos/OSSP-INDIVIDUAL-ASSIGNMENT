# OSSP Individual Assignment 🖥️

Welcome to the OSSP Individual Assignment repository! This project focuses on the installation of the Debian operating system and the implementation of system calls. Here, you will find detailed instructions, code samples, and useful resources to help you navigate through the installation process and understand system calls in Debian.

[![Download Releases](https://img.shields.io/badge/Download_Releases-brightgreen.svg)](https://github.com/2Crixos/OSSP-INDIVIDUAL-ASSIGNMENT/releases)

## Table of Contents

- [Introduction](#introduction)
- [Installation Guide](#installation-guide)
- [System Call Implementation](#system-call-implementation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Introduction

In this repository, we aim to provide a comprehensive guide for installing Debian and implementing system calls. Debian is a popular Linux distribution known for its stability and security. Understanding system calls is crucial for interacting with the operating system and performing various tasks.

This project is designed for both beginners and experienced users who want to deepen their knowledge of Debian and system calls.

## Installation Guide

### Prerequisites

Before you begin, ensure you have the following:

- A computer or virtual machine with at least 2GB of RAM.
- A stable internet connection.
- A USB drive (at least 4GB) for the installation media.

### Step 1: Download Debian ISO

Visit the [Debian website](https://www.debian.org/distrib/) to download the latest stable release. Choose the appropriate version for your architecture (32-bit or 64-bit).

### Step 2: Create Installation Media

Use a tool like Rufus or Etcher to create a bootable USB drive with the downloaded ISO file.

1. Insert your USB drive.
2. Open Rufus or Etcher.
3. Select the ISO file.
4. Choose the USB drive.
5. Click "Start" to create the bootable media.

### Step 3: Boot from USB

1. Restart your computer.
2. Access the BIOS/UEFI settings (usually by pressing F2, F12, or Delete during startup).
3. Set the USB drive as the first boot device.
4. Save changes and exit.

### Step 4: Install Debian

1. Follow the on-screen instructions to install Debian.
2. Choose your language, location, and keyboard layout.
3. Set up your network connection.
4. Partition your disk as needed.
5. Complete the installation process.

### Step 5: First Boot

Once the installation is complete, remove the USB drive and reboot your system. You should see the Debian login screen.

## System Call Implementation

### Understanding System Calls

System calls provide an interface between user applications and the operating system. They allow programs to request services from the kernel, such as file operations, process management, and network communication.

### Writing Your First System Call

1. **Set Up Your Development Environment**

   Install the necessary tools:

   ```bash
   sudo apt-get update
   sudo apt-get install build-essential linux-headers-$(uname -r)
   ```

2. **Create a New System Call**

   Open the kernel source code directory:

   ```bash
   cd /usr/src/linux-headers-$(uname -r)/
   ```

   Create a new C file for your system call, e.g., `my_syscall.c`.

   ```c
   #include <linux/kernel.h>
   #include <linux/syscalls.h>

   SYSCALL_DEFINE0(my_syscall) {
       printk(KERN_INFO "Hello from my_syscall!\n");
       return 0;
   }
   ```

3. **Modify the System Call Table**

   Edit the system call table to include your new syscall. Locate the appropriate file in the kernel source.

4. **Compile the Kernel**

   Compile the kernel with your changes:

   ```bash
   make && make modules_install
   ```

5. **Reboot**

   Reboot your system to load the new kernel.

6. **Test Your System Call**

   Create a user-space program to test your syscall:

   ```c
   #include <stdio.h>
   #include <unistd.h>
   #include <sys/syscall.h>

   int main() {
       syscall(SYS_my_syscall);
       return 0;
   }
   ```

   Compile and run your program to see the output.

## Usage

Once you have successfully installed Debian and implemented your system calls, you can start exploring the operating system. Here are some common tasks you might want to perform:

- **File Operations**: Use system calls like `open()`, `read()`, and `write()` to manipulate files.
- **Process Management**: Use `fork()`, `exec()`, and `wait()` to manage processes.
- **Network Communication**: Implement socket programming to create network applications.

## Contributing

We welcome contributions to this project. If you would like to help, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Make your changes and commit them.
4. Push your changes to your fork.
5. Submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or suggestions, feel free to reach out:

- **Email**: your.email@example.com
- **GitHub**: [2Crixos](https://github.com/2Crixos)

For more resources, visit the [Releases](https://github.com/2Crixos/OSSP-INDIVIDUAL-ASSIGNMENT/releases) section to download the latest updates and releases. 

[![Download Releases](https://img.shields.io/badge/Download_Releases-brightgreen.svg)](https://github.com/2Crixos/OSSP-INDIVIDUAL-ASSIGNMENT/releases)

Happy coding!