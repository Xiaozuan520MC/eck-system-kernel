# eck-system-kernel
A microkernel-based operating system for x86_64, with a built-in terminal interface.

📖 Overview
ECK-System is a microkernel operating system designed for the x86_64 architecture. It follows the principle of minimalism: the kernel itself provides only essential services — memory management, inter-process communication (IPC), and basic scheduling. Everything else, including device drivers and system services, runs in user space as separate processes.

The current implementation includes a fully functional terminal interface, providing direct interaction with the kernel and user-space services.

🧩 Architecture
ECK-System is built around a microkernel design:

Component	Location	Description
Microkernel	Kernel space	Manages memory, processes, and IPC. Handles interrupts and basic scheduling.
Terminal Server	User space	Provides a text-based interface for command input and output.
Device Drivers	User space (as servers)	Keyboard, framebuffer, and disk drivers run as separate processes.
System Services	User space	Filesystem, process manager, and other services are isolated from the kernel.
This design maximizes stability and modularity: a fault in one service does not crash the entire system.

🚀 Current Features
Microkernel Core: Minimal kernel with IPC, memory management, and scheduling.

Terminal Interface: Built-in text-based shell for direct system interaction.

Process Management: Creation, termination, and inter-process communication.

Memory Management: Physical and virtual memory management with page allocation.

Basic IPC: Message-passing between processes.

Interrupt Handling: IDT with support for keyboard interrupts.

x86_64 Support: Fully functional on x86_64 architecture, running in long mode.

BiliBili视频教程：
包括怎么安装WSL和视频展示的NO.1.sh,setup.sh和run.bat的文件内容
1.安装WSL：
  安装命令：wsl --install
2.视频展示的NO.1.sh,setup.sh和run.bat的文件内容：
  NO.1.sh内容：chmod +x setup.sh
  
  setup.sh的内容：
  #!/bin/bash
  echo "=== 开始为你一键配置 xv6-riscv 开发环境 ==="
  echo ">>> 正在更新软件源..."
  sudo apt update -y > /dev/null 2>&1    
  echo ">>> 正在安装 build-essential (make/gcc), RISC-V 交叉编译器, QEMU..."
  sudo apt install -y build-essential gcc-riscv64-linux-gnu qemu-system-misc > /dev/null 2>&1   
  echo "=== 安装完成，正在检查版本 ==="
  echo ">>> Make 版本:"
  make --version | head -n 1
  echo ">>> RISC-V 编译器版本:"
  riscv64-linux-gnu-gcc --version | head -n 1
  echo ">>> QEMU 版本:"
  qemu-system-riscv64 --version  
  echo "=========================================="
  echo "环境配置完美结束！"
  echo "接下来，进入你的代码目录，然后输入： make qemu"

  run.bat的内容：
    qemu-system-riscv64 -machine virt -bios none -kernel kernel/kernel -m 128M -smp 3 -nographic -global virtio-mmio.force-legacy=false -drive file=fs.img,if=none,format=raw,id=x0 -device virtio-blk-      device,drive=x0,bus=virtio-mmio-bus.0

📜 License
ECK-System is open-source software, licensed under the GNU General Public License v2.0. See the LICENSE file for more details.

✍️ Author
Xiaozuan520MC

GitHub: @Xiaozuan520MC
