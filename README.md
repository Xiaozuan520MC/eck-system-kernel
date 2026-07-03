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

📜 License
ECK-System is open-source software, licensed under the GNU General Public License v2.0. See the LICENSE file for more details.

✍️ Author
Xiaozuan520MC

GitHub: @Xiaozuan520MC
