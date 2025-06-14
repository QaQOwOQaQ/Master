# 一、Linux 目录树结构

``` cpp
/
├── bin -> usr/bin
├── boot
├── dev
├── etc
├── home
├── lib -> usr/lib
├── lib32 -> usr/lib32
├── lib64 -> usr/lib64
├── libx32 -> usr/libx32
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin -> usr/sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

以下是一些 `/` 目录下常见的文件夹及其含义：

- **`/bin` (binaries)**: 包含所有用户都可用的基本命令行程序（二进制文件）。这些命令在系统启动、修复或单用户模式下都必须可用，例如 `ls`、`cp`、`cat` 等。
- **`/boot`**: 存储引导加载器文件，包括 Linux 内核（`vmlinuz`）、初始 RAM 磁盘（`initrd`）以及引导加载器的配置文件（如 `grub`）。这些文件是系统启动所必需的。
- **`/dev` (devices)**: 包含设备文件。在 Linux 中，硬件设备（如硬盘、USB 驱动器、终端等）都被表示为文件。通过这些特殊文件，应用程序可以像读写普通文件一样与硬件设备进行交互。
- **`/etc` (et cetera)**: 包含系统范围的配置文件。这些文件通常是纯文本文件，用于配置系统服务、应用程序和系统行为。例如，网络配置、用户密码文件（虽然加密密码在 `/etc/shadow` 中）、系统启动脚本等。
- **`/home`**: 包含普通用户的个人主目录。每个用户都有一个单独的子目录，通常以其用户名命名。用户可以在其主目录中存储自己的文档、图片、音乐、配置文件等。
- **`/lib` (libraries)**: 包含 `/bin` 和 `/sbin` 中二进制文件所需的共享库文件。这些库文件类似于 Windows 中的 DLL 文件，它们是程序运行时需要的额外代码。
- **`/media`**: 用于挂载可移动媒体设备（如 CD/DVD-ROM、USB 驱动器等）的临时挂载点。当你插入一个 USB 驱动器时，它通常会被自动挂载到 `/media` 下的一个子目录。
- **`/mnt` (mount)**: 传统的临时文件系统挂载点。系统管理员通常在这里手动挂载临时的文件系统。
- **`/opt` (optional)**: 用于安装可选的或第三方应用程序软件包。这些应用程序通常不是系统核心部分，它们的安装目录通常独立于系统其他部分，并且自包含。
- **`/proc` (processes)**: 一个虚拟文件系统，提供关于系统和正在运行的进程的实时信息。它不存储实际的文件，而是动态生成数据，作为内核与用户空间之间通信的接口。例如，你可以通过读取 `/proc/cpuinfo` 来获取 CPU 信息。
- **`/root`**: 这是 **root 用户**（超级用户，系统管理员）的主目录。与普通用户的 `/home` 目录不同，`/root` 目录独立存在，以确保即使 `/home` 目录所在的存储出现问题，root 用户也能正常登录和进行系统维护。
- **`/run`**: 存储系统启动后运行时的数据，例如进程 ID 文件（`.pid`）和套接字文件。这些文件通常在系统重启后被清除。
- **`/sbin` (system binaries)**: 包含系统管理员专用的基本系统管理二进制文件。这些命令通常用于系统维护、启动和关闭，并且需要 root 权限才能执行，例如 `fdisk`、`mkfs`、`reboot` 等。
- **`/srv` (service data)**: 包含特定服务的数据。例如，Web 服务器（如 Apache）的数据可能存储在 `/srv/www` 中。
- **`/sys` (system)**: 另一个虚拟文件系统，提供对 Linux 内核设备驱动程序的访问。它以文件形式呈现硬件设备的信息和配置。
- **`/tmp` (temporary)**: 存储临时文件。这些文件通常由应用程序或系统创建，并且在系统重启后或经过一段时间后会被自动删除。
- **`/usr` (Unix System Resources)**: 包含用户程序和文件。这是 Linux 文件系统中最大的目录之一，包含大量的共享数据、只读文件、应用程序、文档等。它的子目录包括：
  - `/usr/bin`: 大多数用户命令的二进制文件。
  - `/usr/lib`: 应用程序和系统程序所需的共享库。
  - `/usr/local`: 用于本地安装的软件，通常由系统管理员手动安装的软件会放在这里。
  - `/usr/share`: 包含所有架构通用的共享数据，如文档、图标、字体等。
  - `/usr/src`: 包含内核源代码和其他程序的源代码。
- **`/var` (variable data)**: 包含内容经常变化的文件，例如日志文件、邮件队列、打印队列、数据库文件、缓存文件等。它是 `/usr` 的可写对应物，因为 `/usr` 在正常操作下通常是只读的。
  - `/var/log`: 系统和应用程序的日志文件。
  - `/var/cache`: 应用程序的缓存数据。
  - `/var/lib`: 应用程序运行过程中修改的持久性数据（如数据库、包管理系统元数据）。
  - `/var/tmp`: 另一个用于存储临时文件的地方，但通常比 `/tmp` 中的文件保留时间更长，即使系统重启也可能保留。

## 1. WSL2 中 /boot 目录为空

如果在 WSL2 (Windows Subsystem for Linux 2) 中发现 `/boot` 目录为空，这是**正常且预期**的行为，而不是系统有问题。

原因如下：

1. **WSL2 的架构:**
   - WSL2 不是一个传统的虚拟机。它运行在一个轻量级的 Hyper-V 虚拟机中，但这个虚拟机是由 Windows 本身管理的，并且它**不使用你 WSL2 发行版（例如 Ubuntu 或 Debian）自带的内核**。
   - 相反，WSL2 使用一个由 **Microsoft 专门定制和优化过的 Linux 内核**。这个内核文件存储在 Windows 文件系统中的特定位置（通常在 `%LOCALAPPDATA%\Packages\<distro_package_id>\LocalState` 或 `%PROGRAMFILES%\WindowsApps` 目录下），而不是在你的 WSL2 虚拟硬盘（`ext4.vhdx`）内部。
2. **引导过程的差异:**
   - 在传统的 Linux 系统中，`/boot` 目录包含内核映像（`vmlinuz`）、initramfs 文件以及引导加载器（如 GRUB）的配置文件。这些文件负责引导 Linux 系统。
   - 但在 WSL2 中，**Windows 负责启动这个轻量级虚拟机**，并将 Microsoft 定制的 Linux 内核加载到其中。你的 WSL2 发行版只是在这个已经启动的内核之上运行其用户空间（user-space）。
   - 因此，你的 WSL2 实例**不需要**自己的 `/boot` 目录来存储内核或引导加载器文件，因为这些都被 Windows 的底层机制所管理。

**这意味着什么？**

- 你无法像在真实 Linux 环境中那样，通过修改 `/boot` 目录下的文件来更换或升级 WSL2 的内核。如果你想使用自定义内核，你需要通过在 Windows 的 `.wslconfig` 文件中指定自定义内核路径来实现。
- 你也不需要担心 `/boot` 目录的空间问题，因为它本身就不包含这些文件。

## 2. 常见设备文件

**`console`**: 系统控制台设备。它通常指向当前正在使用的物理控制台（例如，你直接连接到服务器的键盘和显示器）。

**`core`**: 核心转储文件。当程序崩溃时，操作系统可能会将程序内存的副本写入一个核心文件，用于调试。`core` 文件可以重定向到 `/dev/null`。

**`fd` (file descriptors)**: 这是一个特殊的目录，包含当前进程打开的文件描述符的链接。例如，`fd/0` 是标准输入，`fd/1` 是标准输出，`fd/2` 是标准错误。

**`full`**: 模拟一个永远是满的设备。向它写入数据总是会返回“设备上没有空间”的错误。有时用于测试程序处理磁盘满错误的情况。

**`mqueue` (message queue)**: POSIX 消息队列文件系统。用于进程间通信。

**`null`**: **空设备**。写入到 `/dev/null` 的任何数据都会被丢弃，读取 `/dev/null` 会立即返回文件结束符（EOF）。它常用于丢弃不需要的输出。

**`ptmx` (pseudo-terminal master)**: 伪终端主设备。它是创建伪终端对（master 和 slave）的接口。例如，当你通过 SSH 连接到 Linux 服务器时，会话就会通过伪终端进行。

**`pts` (pseudo-terminal slaves)**: 伪终端从设备。当 `ptmx` 被打开时，就会在 `pts` 目录下创建一个相应的从设备，用于程序的输入/输出。

**`random`**: **随机数生成器**。从这个设备读取数据会提供高质量的伪随机数。它会从系统环境中的噪声（例如鼠标移动、键盘输入、磁盘 I/O）收集熵来生成随机数。

**`shm` (shared memory)**: POSIX 共享内存文件系统。用于不同进程之间共享内存区域，提高通信效率。

**`stderr` (standard error)**: 标准错误输出。它是 `fd/2` 的符号链接，通常会将错误信息输出到终端。

**`stdin` (standard input)**: 标准输入。它是 `fd/0` 的符号链接，通常从键盘或重定向的文件接收输入。

**`stdout` (standard output)**: 标准输出。它是 `fd/1` 的符号链接，通常会将程序的正常输出显示在终端。

**`tty` (teletypewriter)**: 当前终端设备。通常指向你当前正在使用的终端。

**`urandom`**: **非阻塞随机数生成器**。与 `random` 类似，但当熵池不足时，`urandom` 不会阻塞，而是使用密码学安全的算法生成伪随机数，这可能导致随机性略逊于 `random`，但保证了非阻塞性。适用于大多数需要随机数的场景。

**`zero`**: **零设备**。从这个设备读取数据会不断返回空字节（null bytes，即 `\0`）。向它写入数据会被丢弃。它常用于创建指定大小的空文件或填充文件。

简而言之，`/dev` 目录是 Linux 实现“一切皆文件”理念的核心体现。通过这些特殊文件，系统管理和应用程序能够以统一的方式与各种硬件和内核服务进行交互。

## 3. lib、lib32、lib64、libx32

这些目录的存在是为了支持**多架构（multi-architecture）**系统。在同一台机器上运行不同 CPU 架构的程序时，就需要有不同架构的库文件。

- **`/lib32` 或 `/usr/lib32`**:
  - 用于存放 **32 位应用程序**所需的共享库。
  - 在一个 64 位系统上，为了运行 32 位程序，就需要这些 32 位的库。例如，如果你在 64 位的 Ubuntu 上安装了 32 位的 Steam 游戏，它会依赖这些 32 位库。
- **`/lib64` 或 `/usr/lib64`**:
  - 用于存放 **64 位应用程序**所需的共享库。
  - 这是当前主流 64 位 Linux 系统上最常用的库目录。
- **`/libx32` 或 `/usr/libx32`**:
  - 这个目录比较特殊，用于存放 **x32 ABI（Application Binary Interface）**的共享库。
  - x32 ABI 是一种在 **64 位内核上运行的 32 位用户空间**。它允许程序使用 32 位指针和数据类型，但利用 64 位处理器的寄存器和指令集，从而在某些情况下提供比纯 32 位或纯 64 位更好的性能和内存效率。
  - 它的应用场景相对小众，主要用于一些对性能和内存使用有极高要求的特定应用。
- **`lib` (或 `usr/lib`)** 通常指默认架构（在 64 位系统上通常就是 64 位库，或者在 32 位系统上就是 32 位库），而 `lib32`、`lib64`、`libx32` 则明确指定了特定位宽和 ABI 的库，以支持多架构环境。

## 4. bin 和 usr/bin

理解 `/usr/bin` 和 `/bin` 的区别，是理解 Linux 文件系统层次结构演变的关键。

**传统上的区别：**

在 FHS (Filesystem Hierarchy Standard) 的早期版本中，`/bin` 和 `/usr/bin` 之间存在明确的界限：

1. **`/bin` (essential user binaries)**
   - **含义：** 存储**基本（essential）的用户命令**。
   - **用途：** 这些命令是系统**启动、维护和修复**所必需的。它们必须在 `/usr` 文件系统被挂载之前就可用。这意味着，即使 `/usr` 所在的磁盘分区发生故障或未被挂载，`/bin` 下的命令也应该能正常工作。
   - **示例：** `ls`, `cp`, `mv`, `rm`, `cat`, `echo`, `bash` (shell) 等。这些是系统正常运行和最基本的命令行操作所必须的。
2. **`/usr/bin` (non-essential user binaries)**
   - **含义：** 存储**非基本（non-essential）的用户命令**。
   - **用途：** 这些命令是系统运行和用户日常使用所必需的，但它们**不是系统启动或基本维护所必需的**。它们通常在 `/usr` 文件系统挂载之后才可用。
   - **示例：** `gcc`, `g++`, `find`, `grep`, `awk`, `less`, `vim`, `python`, `git` 等。这些是功能更丰富的应用程序和工具。

**这种区别的原因：**

历史原因在于，早期的 Unix 系统磁盘空间有限，操作系统和用户程序可能分别安装在不同的物理磁盘上。`/usr` 通常是挂载的第二个文件系统。为了保证系统即使在 `/usr` 不可用时也能进行基本操作，就需要将最关键的命令放在根文件系统下的 `/bin`。

**现代 Linux 发行版中的变化：`/usr` 合并**

现在，许多现代 Linux 发行版（例如 Debian、Ubuntu、Fedora、Arch Linux、RHEL/CentOS 7+ 等）已经实施了所谓的 **`/usr` 合并（`/usr` merge）**。

**在 `/usr` 合并后的系统中：**

- `/bin` 不再是一个独立的目录，而是一个指向 `/usr/bin` 的

  符号链接（软链接）。

  - 你会看到类似 `bin -> usr/bin` 的条目当你 `ls -l /` 时。

- 所有的用户二进制文件，无论是基本还是非基本，都**实际存储在 `/usr/bin` 中**。

**为什么要进行 `/usr` 合并？**

1. **简化文件系统结构：** 所有的可执行程序都集中在 `/usr/bin` 和 `/usr/sbin` 下，这使得文件系统结构更清晰，管理更简单。
2. **提高管理效率：** 统一的目录结构便于软件包管理器更好地管理文件，也更容易实现只读的 `/usr` 分区，从而提高系统的安全性和稳定性。
3. **消除不必要的区别：** 随着技术发展，磁盘空间不再是主要限制，并且 `/usr` 分区通常在系统启动早期就会被挂载，传统上 `/bin` 和 `/usr/bin` 之间的区别变得不再那么必要和有意义。
4. **方便快照和版本控制：** 将所有大部分只读的系统组件放在一个统一的位置（`/usr`）更便于进行系统快照、版本控制和部署。

**总结区别（现代系统视角）：**

- **`/bin`:** 在现代 Linux 系统中，`/bin` 是一个指向 `/usr/bin` 的**符号链接**。它本身不再包含任何实际文件。
- **`/usr/bin`:** 包含了**绝大多数用户可执行的命令**，无论是传统上认为的“基本”命令还是“非基本”命令。所有这些命令的实际文件都存放在这里。

所以，虽然在你的 `/` 目录下仍然会看到 `/bin` 这个条目，但它仅仅是一个“入口”，当你 `cd /bin` 时，你实际上是在操作 `/usr/bin` 里的文件。

**如何查看你的系统是否进行了 `/usr` 合并？**

你可以在根目录下执行 `ls -l /` 命令。如果 `/bin` 显示为 `bin -> usr/bin`，那么你的系统就采用了 `/usr` 合并。

Bash

```
ls -l /
```

输出中如果包含类似这样的一行，就说明已经合并了：

```
lrwxrwxrwx   1 root root    7 May  8 10:00 bin -> usr/bin
```

## 5. usr  和 home

| 特性         | `/usr`                                         | `/home`                                          |
| :----------- | :--------------------------------------------- | :----------------------------------------------- |
| **用途**     | 存放系统级程序、库、文档和共享资源             | 存放用户个人数据、文件和应用程序配置             |
| **所有者**   | 属于系统（通常是 `root`）                      | 属于特定的普通用户                               |
| **权限**     | 通常是**只读**的（用户不能随意写入和修改）     | 用户对其主目录具有完全的读写权限                 |
| **内容**     | 操作系统组件、安装的应用程序、库文件、系统文档 | 用户的文档、图片、音乐、视频、下载、个人配置文件 |
| **可删除性** | 谨慎，删除可能破坏系统或应用程序               | 可以自由删除个人文件，但要小心配置文件           |
| **重要性**   | 系统正常运行的基础                             | 用户数据和个性化环境的基础                       |

# 二、**快捷键**

``` bash
(1) ctrl c: 取消命令，并且换行
(2) ctrl u: 清空本行命令
(3) tab键：可以补全命令和文件名，如果补全不了快速按两下tab键，可以显示备选选项
```

# 三、系统资源监控

## 1. cpuinfo: CPU

`/proc/cpuinfo` 是 Linux 系统中一个非常重要的虚拟文件，它不存储在硬盘上，而是由内核动态生成，每次读取时都会反映出当前系统的实时 CPU 状态。通过查看这个文件，你可以获取关于系统 CPU 的详细信息，这对于系统性能优化、硬件兼容性检查和故障排查都非常有帮助。

`/proc/cpuinfo` 文件中通常包含以下关键信息：

- **`processor`**: 逻辑处理器的编号。在多核、多线程（如 Intel 的超线程技术）的 CPU 系统中，每个逻辑处理器都会有一个独立的编号。
- **`vendor_id`**: CPU 制造商的 ID，例如 "GenuineIntel" (Intel CPU) 或 "AuthenticAMD" (AMD CPU)。
- **`cpu family`**: CPU 的家族代号，通常以数字表示。
- **`model`**: CPU 家族中的模型代号，也以数字表示。
- **`model name`**: CPU 的完整名称，包含其型号、系列、主频等信息，例如 "Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz"。
- **`stepping`**: CPU 的步进编号，表示处理器的设计或制作版本，用于跟踪处理器的更改。
- **`cpu MHz`**: CPU 的实际运行主频（兆赫兹）。这个值可能会根据 CPU 的负载动态调整（CPU 频率缩放）。
- **`cache size`**: CPU 的二级（或更高级别）缓存大小，例如 "6144 KB"。
- **`physical id`**: 物理 CPU 的 ID。如果系统有多个物理 CPU 插槽，每个物理 CPU 会有唯一的 ID。通过不重复的 `physical id` 数量，可以知道主板上实际插入的物理 CPU 数量。
- **`siblings`**: 当前逻辑处理器所在的物理 CPU 上的逻辑核数。这个值等于 `cpu cores`（物理核数）乘以超线程数（如果开启）。
- **`core id`**: 当前逻辑处理器所在的物理核心的 ID。在一个物理 CPU 内部，每个核心有唯一的 `core id`。
- **`cpu cores`**: 当前物理 CPU 的物理核心数量。例如，一个四核 CPU 会显示 `cpu cores : 4`。
- **`apicid`**: 高级可编程中断控制器 ID，用于区分不同的逻辑核。每个逻辑核的此编号都是唯一的。
- **`fpu`**: 表示 CPU 是否具有浮点运算单元（Floating Point Unit）。
- **`fpu_exception`**: 表示 CPU 是否支持浮点计算异常。
- **`cpuid level`**: 执行 `cpuid` 指令前，EAX 寄存器中的值。根据不同的值，`cpuid` 指令会返回不同的内容。
- **`wp`**: 表示当前 CPU 是否在内核态支持对用户空间的写保护（Write Protection）。
- **`flags`**: 一系列标志，表示 CPU 支持的特性和指令集，如 `lm` (Long Mode，支持 64 位), `vmx` (Intel 虚拟化技术), `svm` (AMD 虚拟化技术), `sse`, `avx` 等。
- **`bogomips`**: 在系统内核启动时粗略测算的 CPU 速度，单位是 MIPS (Million Instructions Per Second)。它并不是一个精确的性能指标，主要用于一些内部测试。
- **`clflush size`**: 每次刷新缓存的大小单位。
- **`cache_alignment`**: 缓存地址对齐单位。
- **`address sizes`**: 可访问地址空间位数。
- **`power management`**: 对能源管理的支持情况。

下面是在我的 Docker Ubuntu22.04 虚拟机上的 `cpuinfo` 文件：

``` shell
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 183
model name	: Intel(R) Core(TM) i7-14650HX
stepping	: 1
microcode	: 0xffffffff
cpu MHz		: 2419.201
cache size	: 30720 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 28
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
vmx flags	: vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
bugs		: spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
bogomips	: 4838.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 183
model name	: Intel(R) Core(TM) i7-14650HX
stepping	: 1
microcode	: 0xffffffff
cpu MHz		: 2419.201
cache size	: 30720 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 28
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
vmx flags	: vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
bugs		: spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
bogomips	: 4838.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 183
model name	: Intel(R) Core(TM) i7-14650HX
stepping	: 1
microcode	: 0xffffffff
cpu MHz		: 2419.201
cache size	: 30720 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 28
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
vmx flags	: vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
bugs		: spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
bogomips	: 4838.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 183
model name	: Intel(R) Core(TM) i7-14650HX
stepping	: 1
microcode	: 0xffffffff
cpu MHz		: 2419.201
cache size	: 30720 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 28
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves avx_vnni umip waitpkg gfni vaes vpclmulqdq rdpid movdiri movdir64b fsrm md_clear serialize flush_l1d arch_capabilities
vmx flags	: vnmi invvpid ept_x_only ept_ad ept_1gb tsc_offset vtpr ept vpid unrestricted_guest ept_mode_based_exec tsc_scaling usr_wait_pause
bugs		: spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi
bogomips	: 4838.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:
```

**重要的计算关系：**

- **物理 CPU 数量**: `cat /proc/cpuinfo | grep "physical id" | sort | uniq | wc -l`
- **每个物理 CPU 的核心数**: `cat /proc/cpuinfo | grep "cpu cores" | uniq`
- **总逻辑 CPU 数量**: `cat /proc/cpuinfo | grep "processor" | wc -l`
- **是否支持 64 位**: `cat /proc/cpuinfo | grep flags | grep ' lm '` (如果返回结果，则支持)

## 2. free: Memory

`free` 命令是 Linux 系统中一个非常常用且重要的工具，用于显示系统当前的**物理内存（RAM）**和 **交换空间（Swap）**的使用情况。它能够帮助你快速了解系统的内存健康状况，判断是否存在内存瓶颈。

默认情况下，`free` 以 **字节（Bytes）** 为单位显示内存信息。为了方便阅读，我们通常会用一些选项来改变输出单位：

``` bash
Usage:
 free [options]

Options:
 -b, --bytes         show output in bytes
     --kilo          show output in kilobytes
     --mega          show output in megabytes
     --giga          show output in gigabytes
     --tera          show output in terabytes
     --peta          show output in petabytes
 -k, --kibi          show output in kibibytes
 -m, --mebi          show output in mebibytes
 -g, --gibi          show output in gibibytes
     --tebi          show output in tebibytes
     --pebi          show output in pebibytes
 -h, --human         show human-readable output
     --si            use powers of 1000 not 1024
 -l, --lohi          show detailed low and high memory statistics
 -t, --total         show total for RAM + swap
 -s N, --seconds N   repeat printing every N seconds
 -c N, --count N     repeat printing N times, then exit
 -w, --wide          wide output

     --help     display this help and exit
 -V, --version  output version information and exit
```

接下来让我们以 `free -h` 的输出为例来详细解释每一列的含义：

```bash
               total        used        free      shared  buff/cache   available
Mem:            7.7G        6.3G        301M        893M        1.1G        309M
Swap:           2.0G        600M        1.4G
```

**第一行：`Mem:` (物理内存)**

- `total`:
  - 表示系统**安装的总物理内存量**。
  - 在上面的例子中是 `7.7G`。
- `used`:
  - 表示当前**已经被使用的物理内存量**。
  - 这个值是 `total` 减去 `free`、`buff/cache` 的值，以及部分 `shared` 内存。
  - **注意：`used` 并不完全代表“应用程序正在使用的内存”**。它包含了内核自身、用户进程以及 **作为文件缓存的内存**。Linux 系统会尽可能地使用内存来缓存文件，以提高性能。
  - 在上面的例子中是 `6.3G`。
- `free`:
  - 表示当前**完全空闲、未被任何程序或缓存使用的物理内存量**。
  - 在上面的例子中是 `301M`。
  - **一个常见的误解是：`free` 内存太少就意味着系统内存不足。这通常是错误的！** Linux 系统会积极地使用空闲内存作为文件缓存 (`buff/cache`)，这部分内存可以随时被应用程序回收使用。所以，`free` 内存小通常是好事，说明系统充分利用了内存。
- `shared`:
  - 表示被**多个进程共享的内存量**。这通常是 System V 共享内存（SysV IPC Shared Memory）或者 `tmpfs` 文件系统使用的内存。
  - 在上面的例子中是 `893M`。
- `buff/cache`:
  - 表示被内核用于文件系统缓存（`buffers` 和 `caches`）的内存量。
    - **`buffers`** 主要用于块设备 I/O 缓存，例如磁盘块。
    - **`caches`** 主要用于文件系统页缓存，即磁盘上的文件内容被加载到内存中以加速访问。
  - 在上面的例子中是 `1.1G`。
  - **这部分内存非常重要！** 它是 Linux 内存管理的一个核心优化。当应用程序需要更多内存时，内核会优先回收这部分内存供应用程序使用，而无需进行耗时的磁盘 I/O。所以，`buff/cache` 越大，系统性能通常越好。
- `available`:
  - 这是 **最重要的指标**，表示当前**应用程序可以立即使用的内存量估算值**。
  - 这个值包含了 `free` 内存，以及可以被快速回收（reclaimable）的 `buff/cache` 内存。
  - 在上面的例子中是 `309M`。
  - **当你判断系统是否面临内存压力时，主要看 `available` 字段。** 如果 `available` 持续很低，系统可能会开始使用交换空间，导致性能下降。

**第二行：`Swap:` (交换空间)**

- `total`:
  - 系统配置的总交换空间大小。交换空间是硬盘上的一块区域，当物理内存不足时，操作系统会将不常用的内存页写入到交换空间中，以释放物理内存供活跃进程使用。
  - 在上面的例子中是 `2.0G`。
- `used`:
  - 当前已使用的交换空间量。
  - 在上面的例子中是 `600M`。
- `free`:
  - 当前空闲的交换空间量。
  - 在上面的例子中是 `1.4G`。
  - 如果 `used` 交换空间很高，并且 `available` 内存很低，这通常是一个警告信号，表明系统物理内存不足，正在频繁地进行内存交换（swapping），这会导致系统性能显著下降，因为硬盘的速度远低于内存。

> 为什么说物理内存的 used 使用了部分 shared 的内存？
>
> 首先，`shared` 内存是指可以被多个进程共享的物理内存区域。最常见的形式是：
>
> - **`tmpfs` 文件系统**：挂载在 `/dev/shm` 等位置的基于内存的文件系统。
> - **System V IPC 共享内存**：用于进程间通信。
> - **共享库（Shared Libraries）**：例如 C 库 `glibc`，当多个程序都加载同一个共享库时，该库的代码段在内存中只有一份副本，但会被所有使用它的进程共享。
> - **写时复制（Copy-on-Write, CoW）页面**：当一个进程 `fork` 出子进程时，初始阶段它们共享父进程的内存页面。只有当其中一个进程尝试写入这些页面时，才会复制一份新的副本。
>
> **`shared` 内存本身是“已用”的内存。** 既然它被一个或多个进程使用了，那么它肯定不能算是 `free` 内存。
>
> 然而，**`used` 字段的计算方式是 `total - free - buff/cache`。**
>
> 这里的问题是，`shared` 内存中的一部分（特别是 `tmpfs` 和一些 IPC 共享内存）**可能会同时被计入 `buff/cache` 中**，因为它们本质上也是基于内存的文件系统或内存映射。
>
> 因此，当 `used` 计算公式是 `total - free - buff/cache` 时，如果 `shared` 内存的一部分已经被 `buff/cache` 包含了，那么在计算 `used` 的时候，这部分内存**不会再被重复计算**。

## 3. top: Processes

`top` （table of processes）命令是 Linux 系统中一个非常常用的性能监控工具，它提供了一个动态、实时、交互式的系统运行状态视图，类似于 Windows 上的“任务管理器”。通过 `top` 命令，你可以快速了解系统的整体运行状况，以及各个进程的资源占用情况。

### `top` 命令的输出结构

`top` 命令的输出通常分为两大部分：

1. **概要信息区 (Summary Area / Dashboard)**：位于上半部分，显示了系统整体的统计信息。
2. **任务列表区 (Task Area / Process List)**：位于下半部分，列出了当前运行的进程或线程的详细信息。

例如：

``` bash
❯ top
top - 06:46:03 up  4:31,  0 users,  load average: 0.17, 0.06, 0.03
Tasks:  28 total,   1 running,  27 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  0.9 sy,  0.0 ni, 97.5 id,  0.2 wa,  0.0 hi,  0.2 si,  0.0 st
MiB Mem :   7946.9 total,   6002.7 free,   1231.9 used,    712.2 buff/cache
MiB Swap:   4096.0 total,   4096.0 free,      0.0 used.   6417.8 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                             324 root      20   0   22.5g 225804  52092 S   1.3   2.8   3:43.02 node
  172 root      20   0 1326712 103908  44156 S   1.0   1.3   0:26.59 node                            
  238 root      20   0 1003908  63144  38452 S   0.3   0.8   0:04.89 node                            
    1 root      20   0    4628   3696   3144 S   0.0   0.0   0:00.00 bash                             	 27 root      20   0    2892   1852   1732 S   0.0   0.0   0:00.07 sh                                 144 root      20   0    2892   1052    964 S   0.0   0.0   0:00.00 sh                                 156 root      20   0  993140  43516  35124 S   0.0   0.5   0:00.18 node                               163 root      20   0    2892    984    892 S   0.0   0.0   0:00.00 sh                                 266 root      20   0  993980  50424  38780 S   0.0   0.6   0:04.18 node                               305 root      20   0 1242740  80316  40888 S   0.0   1.0   0:14.91 node                               425 root      20   0 1054752  81432  41804 S   0.0   1.0   0:19.81 node                               436 root      20   0   16700  10780   5892 S   0.0   0.1   0:15.51 zsh                                 442 root      20   0   11148   4788   2212 S   0.0   0.1   0:00.00 zsh                                 480 root      20   0   12280   4836   1396 S   0.0   0.1   0:00.00 zsh                                 481 root      20   0   12264   3436      0 S   0.0   0.0   0:00.14 zsh                                 483 root      20   0    3452   1100    980 S   0.0   0.0   0:00.45 gitstatusd-linu                     495 root      20   0 1408124 247196  54568 S   0.0   3.0   0:01.99 clangd.main                         543 root      20   0 1003120  62508  39596 S   0.0   0.8   0:00.66 node 
```

#### 概要信息区详解

- **第一行：系统时间、运行时间、登录用户数和平均负载**

  - ```
    top - hh:mm:ss up days, hh:mm, users, load average: 0.00, 0.00, 0.00
    ```

    - `hh:mm:ss`: 当前系统时间。
    - `up days, hh:mm`: 系统自上次启动以来的运行时间（例如：`up 2 days, 4:36` 表示系统已运行 2 天 4 小时 36 分钟）。
    - `users`: 当前登录系统的用户数量。
    - `load average: 0.00, 0.00, 0.00`: 系统平均负载。这三个数字分别表示过去 1 分钟、5 分钟和 15 分钟的平均负载。平均负载表示系统在给定时间段内处于可运行或不可中断睡眠状态的进程数量。对于单核 CPU，理想的负载值是接近 1 或更低。对于多核CPU，理想的负载值是接近 CPU 核心数或更低。

- **第二行：任务（进程）状态总结**

  - ```
    Tasks: total, running, sleeping, stopped, zombie
    ```

    - `total`: 总进程数。
    - `running`: 正在运行的进程数。
    - `sleeping`: 睡眠状态的进程数（等待某个事件发生）。
    - `stopped`: 已停止的进程数。
    - `zombie`: 僵尸进程数（已终止但其父进程尚未回收资源的进程）。

- **第三行：CPU 使用率**

  - ```
    %Cpu(s): us, sy, ni, id, wa, hi, si, st
    ```

    - `us` (user): 用户空间进程使用 CPU 的百分比。
    - `sy` (system): 内核空间进程使用 CPU 的百分比。
    - `ni` (nice): 低优先级用户进程使用 CPU 的百分比。
    - `id` (idle): CPU 空闲时间的百分比。
    - `wa` (iowait): CPU 等待 I/O 完成的百分比。如果这个值很高，可能表示磁盘或网络I/O是瓶颈。
    - `hi` (hardware interrupt): 硬中断使用 CPU 的百分比。
    - `si` (software interrupt): 软中断使用 CPU 的百分比。
    - `st` (steal time): 当系统在虚拟机中运行时，被虚拟机管理器“偷走”的 CPU 时间百分比。

- **第四行：内存使用情况**

  - ```
    MiB Mem : total total, free free, used used, buff/cache buff/cache
    ```

    - `total`: 总物理内存量。
    - `free`: 空闲物理内存量。
    - `used`: 已使用物理内存量。
    - `buff/cache`: 用于文件缓存和缓冲区使用的内存量。

- **第五行：交换空间（Swap）使用情况**

  - ```
    MiB Swap: total total, free free, used used, avail Mem
    ```

    - `total`: 总交换空间量。
    - `free`: 空闲交换空间量。
    - `used`: 已使用交换空间量。
    - `avail Mem`: 可用于新进程的内存量（包括部分缓存内存）。

#### 任务列表区详解

任务列表区默认按 **CPU 使用率**从高到低排序，显示了每个进程的详细信息。常见的列包括：

- **PID**: 进程ID，每个进程的唯一标识符。
- **USER**: 进程所有者的用户名。
- **PR（Priority）**: 进程的调度优先级。值越小优先级越高。对于普通（非实时）进程，`PR` 的计算公式通常是 `PR = 20 + NI`。
- **NI**: `nice` 值。`nice` 值是用来调整进程优先级的，范围从 -20（最高优先级）到 19（最低优先级）。
- **VIRT**: 进程使用的虚拟内存总量（单位：KiB）。
- **RES（Resident Set Size）**: 进程使用的常驻内存（物理内存，不包括 swap out 的量）总量（单位：KiB）。
- **SHR（Shared Memory）**: 进程使用的共享内存总量（单位：KiB）。
- **S:** 进程状态。常见状态包括：
  - `D`: 不可中断睡眠 (Uninterruptible sleep)
  - `R`: 正在运行 (Running)
  - `S`: 睡眠 (Sleeping)
  - `T`: 停止或被追踪 (Stopped or Traced)
  - `Z`: 僵尸 (Zombie)
- **%CPU**: 进程使用的 CPU 百分比。
- **%MEM**: 进程使用的物理内存百分比。
- **TIME+**: 进程自启动以来占用的总 CPU 时间（精确到百分之一秒）。
- **COMMAND**: 启动进程的命令或程序名。

## 4. iostat: IO

`iostat` (Input/Output Statistics) 是 Linux 系统中一个非常重要的性能监控工具，它属于 `sysstat` 软件包。`iostat` 主要用于监控系统设备的 I/O 负载，包括物理磁盘、逻辑卷和网络文件系统（NFS），以及 CPU 的使用情况。通过 `iostat`，你可以识别 I/O 瓶颈，评估存储系统的性能，并为系统优化提供数据支持。

最简单的用法是直接运行 `iostat`：

```bash
iostat
```

这将显示自系统启动以来的平均 CPU 统计信息和所有设备的 I/O 统计信息。

通常，我们会结合 `interval`（间隔时间）和 `count`（次数）参数来实时监控：

```basj
iostat [options] [interval [count]]
```

- `interval`: 指定两次报告之间的时间间隔，单位为秒。
- `count`: 指定报告的次数。如果省略 `count`，`iostat` 会持续报告，直到你按 `Ctrl+C` 停止。

**示例：**

```bash
iostat 2 5  # 每2秒报告一次，共报告5次
```

另外我们也可以使用 `-x` 参数来查看一些拓展指标，这在下文有详细说明。

### `iostat` 输出的结构

`iostat` 的输出通常分为两大部分：

1. **CPU 使用率报告 (CPU Utilization Report)**：显示 CPU 的整体使用情况。
2. **设备使用率报告 (Device Utilization Report)**：显示各个存储设备的 I/O 统计信息。

#### 1. CPU 使用率报告详解

这部分通常出现在第一个报告的顶部，或者当你使用 `-c` 选项时。它与 `top` 命令中的 CPU 统计类似。

- `%user`: 用户空间（非内核）程序使用的 CPU 时间百分比。
- `%nice`: 带有非默认 `nice` 值的用户进程使用的 CPU 时间百分比。
- `%system`: 内核空间（系统调用和内核任务）使用的 CPU 时间百分比。
- `%iowait`: CPU 等待 I/O 操作完成的空闲时间百分比。如果这个值持续很高（例如超过 20-30%），可能表明 I/O 是系统瓶颈。
- `%steal`: (在虚拟机环境下) CPU 被虚拟机管理程序“窃取”的时间百分比。
- `%idle`: CPU 处于完全空闲状态的时间百分比，没有任何任务需要处理，也没有等待 I/O。

#### 2. 设备使用率报告详解

这部分显示了每个存储设备的详细 I/O 统计信息。默认情况下，`iostat` 会显示一些基本指标。使用 `-x` 选项可以显示更详细的扩展统计信息，这在分析 I/O 性能时非常有用。

**基本指标 (默认输出):**

当你运行不带 `-x` 参数的 `iostat` 命令时，你会看到每个存储设备的基本性能概览。这些指标提供了高层次的 I/O 活动信息：

- **`Device`**:
  - **含义**: 显示存储设备的名称。
  - **例子**: `sda` (第一个 SCSI 磁盘), `sdb` (第二个 SCSI 磁盘), `dm-0` (一个逻辑卷或多路径设备), `nvme0n1` (NVMe 固态硬盘)。
  - **作用**: 帮助你识别当前正在报告的物理或逻辑存储单元。
- **`tps` (transactions per second)**:
  - **含义**: 每秒发送到设备的传输请求次数。一个“传输”可以理解为一次独立的 I/O 操作（读或写）。
  - 解读: 这个值反映了设备每秒处理的 I/O 操作数量，类似于 IOPS (Input/Output Operations Per Second)。
    - **高 `tps`**: 通常表示设备正在处理大量的独立 I/O 请求，这对于数据库、虚拟机等需要频繁小文件读写的应用场景非常关键。
    - **低 `tps`**: 可能表示 I/O 活动较少，或者正在进行大块的顺序 I/O（此时 `kB_read/s` 或 `kB_wrtn/s` 可能很高，但 `tps` 不一定高）。
  - **提示**: 不同的存储介质有不同的 `tps` 处理上限。例如，SSD 的 `tps` 通常远高于 HDD。
- **`kB_read/s` (或 `MB_read/s`)**:
  - **含义**: 每秒从设备读取的数据量。
  - **单位**: 默认为千字节/秒 (KiB/s)，若使用 `-m` 选项则为兆字节/秒 (MiB/s)。
  - 解读: 这个指标衡量了设备的读吞吐量（Read Throughput）。
    - **高值**: 表明设备正在以高速率传输数据，常见于文件服务器、备份还原、视频编辑等场景。
- **`kB_wrtn/s` (或 `MB_wrtn/s`)**:
  - **含义**: 每秒写入设备的数据量。
  - **单位**: 默认为千字节/秒 (KiB/s)，若使用 `-m` 选项则为兆字节/秒 (MiB/s)。
  - 解读: 这个指标衡量了设备的写吞吐量（Write Throughput）。
    - **高值**: 表明设备正在以高速率写入数据，同样常见于文件服务器、数据库日志写入等场景。
- **`kB_dscd/s` (或 `MB_dscd/s`)**:
  - **含义**: 每秒从设备丢弃（Discarded）的数据量。
  - **单位**: 默认为千字节/秒 (KiB/s)，若使用 `-m` 选项则为兆字节/秒 (MiB/s)。
  - 解读: 这个指标主要与 TRIM/UNMAP 操作有关，尤其在固态硬盘（SSD）和某些虚拟化存储（如精简配置的 LVM 或 SAN 卷）中。
    - 当系统删除文件或释放数据块时，会向支持 TRIM/UNMAP 的存储设备发送指令，告诉设备这些块不再使用，可以被内部回收。
    - **高值**: 通常表示系统正在进行大量的删除操作、文件系统在后台执行 TRIM，或在虚拟化环境中虚拟机内部正在释放存储空间。这对于 SSD 的性能维护和寿命延长很重要。
- **`kB_read` (或 `MB_read`)**:
  - **含义**: 自系统启动以来，从设备读取的**总数据量**。
  - **单位**: 默认为千字节 (KiB)，若使用 `-m` 选项则为兆字节 (MiB)。
  - **解读**: 这是一个累积值，可以帮助你了解设备在长时间内的总读取负载。
- **`kB_wrtn` (或 `MB_wrtn`)**:
  - **含义**: 自系统启动以来，写入设备**的总数据量**。
  - **单位**: 默认为千字节 (KiB)，若使用 `-m` 选项则为兆字节 (MiB)。
  - **解读**: 同样是累积值，显示了设备在长时间内的总写入负载。
- **`kB_dscd` (或 `MB_dscd`)**:
  - **含义**: 自系统启动以来，从设备丢弃（Discarded）的**总数据量**。
  - **单位**: 默认为千字节 (KiB)，若使用 `-m` 选项则为兆字节 (MiB)。
  - **解读**: 这是一个累积值，与 `kB_dscd/s` 对应，表示自系统启动以来，通过 TRIM/UNMAP 操作通知存储设备可以回收的总数据量。它反映了长期以来存储空间的回收活动。

**扩展指标 (使用 `iostat -x`):**

使用 `-x` 选项后，除了上述基本指标，还会增加以下更详细的列：

- `rrqm/s`: 每秒合并到队列的读请求数（即，块层将相邻的读请求合并为一个较大的请求）。
- `wrqm/s`: 每秒合并到队列的写请求数。
- `r/s`: 每秒发出的读请求数。
- `w/s`: 每秒发出的写请求数。
- `rkB/s` (或 `rMB/s`): 每秒从设备读取的千字节数（读吞吐量）。
- `wkB/s` (或 `wMB/s`): 每秒写入设备的千字节数（写吞吐量）。
- `avgrq-sz`: 平均每个 I/O 请求的数据大小（单位：扇区，通常一个扇区是 512 字节）。较大的值通常意味着更高效的 I/O。
- `avgqu-sz`: 平均 I/O 队列长度。表示在给定时间段内，有多少个 I/O 请求在等待设备处理。高值可能表明设备是瓶颈。
- `await`: **Average wait time for I/O requests**，平均每个 I/O 请求的等待和处理时间（单位：毫秒）。这个时间包括请求在队列中等待的时间和设备实际处理请求的时间。**这是评估磁盘性能非常重要的指标。高 `await` 值（例如，HDD 超过 20-30ms，SSD 超过 1-2ms）通常表明 I/O 延迟较高。**
- `r_await`: 平均每个读请求的等待和处理时间（毫秒）。
- `w_await`: 平均每个写请求的等待和处理时间（毫秒）。
- `%util`: Percentage of CPU time during which I/O requests were issued to the device，设备利用率，表示设备在处理 I/O 请求的时间百分比。
  - **对于单个设备：** `%util` 接近 100% 通常意味着设备已达到饱和，或者正在成为性能瓶颈。即使队列不长，一个慢速设备也可能达到 100% 利用率。
  - **对于 RAID 或多路径设备：** `%util` 可能会超过 100%，因为它是所有底层物理磁盘利用率的总和。
  - 高 `%util` 但低 `await` 可能意味着设备吞吐量很高，但没有延迟；高 `%util` 且高 `await` 则很可能存在 I/O 瓶颈。

### `iostat` 常用选项

- `-c`: 只显示 CPU 统计信息。
- `-d`: 只显示设备 I/O 统计信息。
- `-h`: 以人类可读的格式显示（例如，KB、MB、GB）。
- `-k`: 以千字节（kilobytes）为单位显示统计信息（默认可能为扇区或块）。
- `-m`: 以兆字节（megabytes）为单位显示统计信息。
- `-N`: 显示 LVM2 逻辑卷的统计信息。
- `-p [device|ALL]`: 显示指定设备及其所有分区的统计信息。例如：`iostat -p sda`。
- `-t`: 在每个报告前显示时间戳。
- `-x`: 显示扩展统计信息（详细的 I/O 指标，如 `await`, `%util` 等）。
- `-y`: 跳过第一次（自启动以来）的统计报告，直接从第一个间隔开始报告。
- `--dec={0|1|2}`: 设置小数位数。

### 如何解读 `iostat` 输出以诊断问题

1. **检查 `%iowait` (CPU 报告)**：
   - 如果 `%iowait` 持续较高（例如超过 20-30%），表明 CPU 正在等待 I/O 完成，这通常是 I/O 瓶颈的明显信号。
2. **检查 `await` (设备报告，尤其配合 `-x`)**：
   - `await` 值是衡量 I/O 延迟的关键指标。
   - 对于 HDD，`await` 超过 20-30ms 可能表明性能不佳。
   - 对于 SSD，`await` 超过 1-2ms 可能就需要关注。
   - 如果 `await` 很高，但 `avgqu-sz` 较低，可能意味着单个 I/O 请求本身就很慢（例如，存储设备本身性能不足）。
   - 如果 `await` 和 `avgqu-sz` 都很高，表明有大量的 I/O 请求在排队，并且设备处理不过来。
3. **检查 `%util` (设备报告，尤其配合 `-x`)**：
   - `%util` 接近 100% 表示设备非常繁忙，可能是瓶颈。
   - 如果 `%util` 很高但 `tps` 和 `kB_read/s`/`kB_wrtn/s`（吞吐量）较低，这可能意味着设备正在处理大量的小文件随机 I/O，效率低下。
   - 如果 `%util` 很高且吞吐量也很高，说明设备正在高效地处理大量数据。
4. **检查 `tps` 和 `kB_read/s`/`kB_wrtn/s` (吞吐量)**：
   - `tps` (I/O Operations Per Second) 显示每秒的 I/O 请求数量。这对于评估硬盘的 IOPS 性能很有用。
   - `kB_read/s` 和 `kB_wrtn/s` 显示数据传输的带宽。
   - 根据你的应用场景，可能更关注 IOPS（例如数据库、虚拟化）或带宽（例如文件服务器、视频编辑）。
5. **检查 `avgqu-sz` (设备报告，尤其配合 `-x`)**：
   - 高队列长度表明设备无法及时处理所有传入的 I/O 请求。这可能是因为设备本身速度不够，或者系统发送给它的请求过多。

## 5. iotop: IO

## 6. df: Disk

`df` (disk free) 是一个在类 Unix 系统（包括 Linux）中广泛使用的命令行工具，用于**报告文件系统的磁盘空间使用情况**。它显示的是整个文件系统的总容量、已用空间、可用空间以及使用率百分比，而不是像 `du` 那样计算特定文件或目录的大小。

### `df` 命令的基本用途

`df` 命令的主要目的是让用户快速了解当前系统上各个**已挂载文件系统**的整体磁盘空间状况。这对于监控服务器磁盘空间、预警空间不足、规划存储容量等方面都非常有用。

### `df` 命令的基本语法

```bash
df [选项] [文件或目录]
```

- **不带任何参数**：默认情况下，`df` 会列出所有已挂载的文件系统的信息。

  ```bash
  df
  ```

  输出示例（可能因系统而异）：

  ```bash
  Filesystem      1K-blocks     Used Available Use% Mounted on
  overlay        1055762868 20264836 981794560   3% /
  tmpfs               65536        0     65536   0% /dev
  tmpfs             4068792        0   4068792   0% /sys/fs/cgroup
  shm                 65536        0     65536   0% /dev/shm
  /dev/sdd       1055762868 20264836 981794560   3% /etc/hosts
  tmpfs             4068792        0   4068792   0% /proc/acpi
  tmpfs             4068792        0   4068792   0% /sys/firmware
  ```

  每一列的含义：

  - **Filesystem**：文件系统名称（通常是设备名称，如 `/dev/sda1`）。
  - **1K-blocks**：文件系统总大小（以 1KB 块为单位）。
  - **Used**：已使用的空间（以 1KB 块为单位）。
  - **Available**：可用空间（以 1KB 块为单位）。
  - **Use%**：已用空间的百分比。
  - **Mounted on**：文件系统的挂载点。

- **指定文件或目录**：如果你指定一个文件或目录，`df` 会显示该文件或目录所在的**文件系统**的信息。

  Bash

  ```bash
  df /home/user
  df /var/log/syslog
  ```

  这会显示 `/home/user` 目录所在的那个文件系统（例如 `/dev/sda1`）的整体信息。

### `df` 命令的常用选项

`df` 命令提供了多种选项来定制输出，使其更易读或提供更多信息：

1. **`-h`, `--human-readable`：以人类可读的格式显示大小。** 这是最常用的选项，它会将大小显示为 K (KB), M (MB), G (GB), T (TB) 等，使得输出更易于理解。

   ```bash
   ❯ df -h
   Filesystem      Size  Used Avail Use% Mounted on
   overlay        1007G   20G  937G   3% /
   tmpfs            64M     0   64M   0% /dev
   tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
   shm              64M     0   64M   0% /dev/shm
   /dev/sdd       1007G   20G  937G   3% /etc/hosts
   tmpfs           3.9G     0  3.9G   0% /proc/acpi
   tmpfs           3.9G     0  3.9G   0% /sys/firmware
   ```

2. **`-a`, `--all`：显示所有文件系统的信息，包括伪文件系统。** 默认情况下，`df` 会忽略一些虚拟或伪文件系统（如 `proc`, `sysfs` 等）。使用 `-a` 会显示这些文件系统。

   ```bash
   ❯ df -ha
   Filesystem      Size  Used Avail Use% Mounted on
   overlay        1007G   20G  937G   3% /
   proc               0     0     0    - /proc
   tmpfs            64M     0   64M   0% /dev
   devpts             0     0     0    - /dev/pts
   sysfs              0     0     0    - /sys
   tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
   cgroup             0     0     0    - /sys/fs/cgroup/cpuset
   cgroup             0     0     0    - /sys/fs/cgroup/cpu
   cgroup             0     0     0    - /sys/fs/cgroup/cpuacct
   cgroup             0     0     0    - /sys/fs/cgroup/blkio
   cgroup             0     0     0    - /sys/fs/cgroup/memory
   cgroup             0     0     0    - /sys/fs/cgroup/devices
   cgroup             0     0     0    - /sys/fs/cgroup/freezer
   cgroup             0     0     0    - /sys/fs/cgroup/net_cls
   cgroup             0     0     0    - /sys/fs/cgroup/perf_event
   cgroup             0     0     0    - /sys/fs/cgroup/net_prio
   cgroup             0     0     0    - /sys/fs/cgroup/hugetlb
   cgroup             0     0     0    - /sys/fs/cgroup/pids
   cgroup             0     0     0    - /sys/fs/cgroup/rdma
   cgroup             0     0     0    - /sys/fs/cgroup/misc
   cgroup             0     0     0    - /sys/fs/cgroup/systemd
   mqueue             0     0     0    - /dev/mqueue
   shm              64M     0   64M   0% /dev/shm
   /dev/sdd       1007G   20G  937G   3% /etc/resolv.conf
   /dev/sdd       1007G   20G  937G   3% /etc/hostname
   /dev/sdd       1007G   20G  937G   3% /etc/hosts
   devpts             0     0     0    - /dev/console
   proc               0     0     0    - /proc/bus
   proc               0     0     0    - /proc/fs
   proc               0     0     0    - /proc/irq
   proc               0     0     0    - /proc/sys
   tmpfs           3.9G     0  3.9G   0% /proc/acpi
   tmpfs            64M     0   64M   0% /proc/interrupts
   tmpfs            64M     0   64M   0% /proc/kcore
   tmpfs            64M     0   64M   0% /proc/keys
   tmpfs            64M     0   64M   0% /proc/timer_list
   tmpfs           3.9G     0  3.9G   0% /sys/firmware
   ```

3. **`-T`, `--print-type`：显示文件系统类型。** 在输出中增加一列，显示文件系统的类型（如 `ext4`, `xfs`, `tmpfs` 等）。

   ```bash
   ❯ df -T
   Filesystem     Type     1K-blocks     Used Available Use% Mounted on
   overlay        overlay 1055762868 20264836 981794560   3% /
   tmpfs          tmpfs        65536        0     65536   0% /dev
   tmpfs          tmpfs      4068792        0   4068792   0% /sys/fs/cgroup
   shm            tmpfs        65536        0     65536   0% /dev/shm
   /dev/sdd       ext4    1055762868 20264836 981794560   3% /etc/hosts
   tmpfs          tmpfs      4068792        0   4068792   0% /proc/acpi
   tmpfs          tmpfs      4068792        0   4068792   0% /sys/firmware
   ```

4. **`-i`, `--inodes`：显示 inode 使用情况而不是磁盘块使用情况。** Inode（索引节点）是文件系统存储文件和目录元数据的数据结构。每个文件或目录都需要一个 inode。当文件系统上的文件数量非常多时，即使磁盘空间还有，也可能因为 inode 用尽而无法创建新文件。这个选项可以帮助检查 inode 的使用情况。

   ```bash
   ❯ df -ih
   Filesystem     Inodes IUsed IFree IUse% Mounted on
   overlay           64M  207K   64M    1% /
   tmpfs            994K    17  994K    1% /dev
   tmpfs            994K    16  994K    1% /sys/fs/cgroup
   shm              994K     1  994K    1% /dev/shm
   /dev/sdd          64M  207K   64M    1% /etc/hosts
   tmpfs            994K     1  994K    1% /proc/acpi
   tmpfs            994K     1  994K    1% /sys/firmware
   ```

5. **`-x <TYPE>`, `--exclude-type=<TYPE>`：排除指定类型的文件系统。** 例如，`df -h -x tmpfs` 会在输出中排除所有 `tmpfs` 类型的文件系统。

6. **`-t <TYPE>`, `--type=<TYPE>`：只显示指定类型的文件系统。** 例如，`df -h -t ext4` 只会显示 `ext4` 类型的文件系统。

7. **`-P`, `--portability`：使用 POSIX 输出格式。** 这会使得输出格式更符合 POSIX 标准，通常用于脚本中以确保解析的兼容性。

### `df` 的实际应用场景

- **日常监控**：快速查看所有挂载点的磁盘使用率，及时发现空间不足的风险。
- **空间规划**：在部署新服务或应用前，检查是否有足够的可用磁盘空间。
- **故障排查**：当应用程序报错“磁盘空间不足”时，`df` 是第一个要检查的命令。
- **自动化脚本**：在脚本中检查磁盘使用率，如果超过某个阈值就发送警告或执行清理操作。

### `df` 与 `du` 的区别

理解 `df` 和 `du` 的区别是 Linux 磁盘空间管理的关键：

- **`df` (Disk Free)**：**报告文件系统的整体可用空间和使用情况。** 它读取文件系统的元数据来获取这些信息。它的数据是基于**整个文件系统**的统计。
  - 关注点：**整个分区的剩余空间。**
  - 常见差异原因：文件删除后，如果进程仍然打开着该文件句柄，`du` 可能不再统计该文件，但 `df` 仍会认为该文件占用的空间没有被释放，因为文件系统直到所有句柄关闭后才会真正回收空间。
- **`du` (Disk Usage)**：**估算文件或目录所占用的磁盘空间。** 它通过遍历文件和目录来计算实际使用的块数。
  - 关注点：**特定文件或目录的占用空间。**

**简而言之：**

- `df` 告诉你**你的水箱里还有多少水，以及用了多少。**
- `du` 告诉你**你的某个水桶里装了多少水。**

两者结合使用，可以更全面地了解磁盘空间的使用状况。例如，如果你发现 `df` 报告某个分区空间不足，但用 `du` 却找不到占用空间大的目录，那么很可能是存在被删除但仍被进程占用的文件句柄。

### 补充：tmpfs

`tmpfs` (Temporary File System) 是 Linux 中一种特殊的**虚拟文件系统**，它将文件和目录存储在**虚拟内存**中，而不是持久性存储设备（如硬盘或 SSD）上。这意味着 `tmpfs` 中的所有数据在系统重启或卸载文件系统时会**丢失**。

#### `tmpfs` 的核心特性

1. **内存驻留**：`tmpfs` 中的文件数据主要存储在 RAM（随机存取存储器）中。这使得对 `tmpfs` 文件的读写操作非常快，通常比访问传统磁盘文件系统快几个数量级。
2. **按需分配与动态伸缩**：
   - `tmpfs` 不会预先分配所有指定的内存空间。它会根据实际需要动态地分配和释放内存。
   - 你可以为 `tmpfs` 设置一个最大大小（例如，`size=1G`），但它只会在实际使用到时才占用内存。如果没有数据写入，它几乎不占用任何 RAM。
   - 当文件被删除或文件系统被卸载时，`tmpfs` 占用的内存会自动释放回给系统。
3. **可交换性 (Swappable)**：
   - 这是 `tmpfs` 与早期的 `ramfs` 的一个主要区别。如果系统内存压力较大，`tmpfs` 中的不常用页面（pages）可以被**交换（swap）**到硬盘上的交换空间（swap partition或swap file）中。
   - 这种特性使得 `tmpfs` 比 `ramfs` 更健壮，因为它不会导致系统在内存耗尽时崩溃，而是会使用交换空间来缓解压力。当然，如果数据被交换到磁盘，其访问速度会显著下降。
4. **临时性**：如其名称“Temporary File System”所示，`tmpfs` 中的所有内容都是临时的。系统关机、重启或卸载 `tmpfs` 后，所有数据都会被清除。
5. **文件系统接口**：尽管数据存储在内存中，但 `tmpfs` 提供了标准的 POSIX 文件系统接口。这意味着你可以使用所有常规的文件系统命令（如 `ls`, `cd`, `cp`, `rm`, `mkdir`, `df`, `du` 等）来操作 `tmpfs` 上的文件和目录。

#### `tmpfs` 的常见用途和应用场景

`tmpfs` 由于其高速和临时性，在 Linux 系统中被广泛应用于以下场景：

1. **`/dev/shm` (POSIX 共享内存)**：
   - 这是 `tmpfs` 最常见的默认挂载点之一。它提供了 POSIX 共享内存机制（`shm_open()`, `shm_unlink()`），允许不同的进程通过这个基于内存的文件系统来共享数据。
   - 许多应用程序，尤其是数据库系统、Web 服务器（用于缓存）和一些高性能计算应用，会利用 `/dev/shm` 进行快速的进程间通信或存储临时数据。
2. **`/run` (或 `/var/run`)**：
   - 存储系统运行时数据，例如 PID 文件、锁文件、套接字文件等。这些文件通常只在系统运行时有意义，并在系统启动后创建，关闭时清除。
   - 在现代 Linux 系统中，`/run` 通常是一个 `tmpfs` 挂载点，取代了传统的 `/var/run` 和 `/var/lock`。
3. **`/tmp` 和 `/var/tmp`**：
   - `tmpfs` 经常被用于挂载 `/tmp` 目录。`/tmp` 目录用于存储各种应用程序的临时文件。
   - 将 `/tmp` 设置为 `tmpfs` 的优点是：
     - **速度快**：临时文件的读写速度更快。
     - **自动清理**：系统重启后，`/tmp` 中的所有内容会自动清除，避免了临时文件堆积占用硬盘空间。
     - **减少磁盘磨损**：对于频繁读写的临时文件，可以减少对 SSD 等存储设备的磨损。
   - **注意**：`/var/tmp` 通常用于需要跨重启保留的临时文件，所以它不应该被挂载为 `tmpfs`，否则重启后数据会丢失。然而，在一些系统（如某些 Docker 容器）中，出于性能考虑，`/var/tmp` 也可能被配置为 `tmpfs`。
4. **浏览器缓存**：一些用户会将浏览器缓存目录（如 Firefox 或 Chrome 的缓存）挂载到 `tmpfs` 上，以提高浏览速度和减少磁盘 I/O。
5. **构建过程中的临时文件**：在软件编译或打包过程中，可能会生成大量的临时文件。将这些临时文件存储在 `tmpfs` 上可以加快构建速度。
6. **Docker 容器中的临时卷**：Docker 提供了 `tmpfs` 挂载选项 (`--tmpfs`)，允许容器将某些目录挂载为 `tmpfs`，用于存储不需持久化的临时数据，提高性能和减少容器层写入。

#### 如何挂载 `tmpfs`

你可以手动挂载一个 `tmpfs` 文件系统：

```bash
sudo mount -t tmpfs -o size=1G,mode=1777 tmpfs /mnt/mytmpfs
```

- `-t tmpfs`：指定文件系统类型为 `tmpfs`。
- `size=1G`：设置 `tmpfs` 的最大大小为 1GB。如果不指定，默认通常是系统总 RAM 的一半。
- `mode=1777`：设置挂载点的权限（`rwxrwxrwt`，即所有用户可读写，但只能删除自己创建的文件）。
- `tmpfs`：这是文件系统的“设备”名称，对于 `tmpfs` 来说，它只是一个占位符。
- `/mnt/mytmpfs`：你想要挂载 `tmpfs` 的目录，这个目录需要提前创建。

为了让 `tmpfs` 在系统启动时自动挂载，你可以将条目添加到 `/etc/fstab` 文件中：

```
tmpfs   /mnt/mytmpfs    tmpfs   defaults,size=1G,mode=1777 0 0
```

#### `tmpfs` 与 `ramdisk` 的区别

尽管两者都涉及内存，但它们在实现和行为上有所不同：

- **`ramdisk` (RAM Disk)**：
  - 是一个**模拟的块设备**，类似于一个硬盘分区，但它存在于内存中。
  - 你需要在这个 `ramdisk` 上**创建并格式化**一个传统的文件系统（如 `ext4`, `xfs`）才能使用它。
  - 一旦创建，`ramdisk` 的大小是**固定**的，即使没有数据，也会占用预设的内存量。
  - 通常**不支持交换**到磁盘。
  - 在现代 Linux 中较少直接使用，因为 `tmpfs` 更灵活高效。
- **`tmpfs`**：
  - 是一个**虚拟文件系统**本身，不需要底层块设备。
  - 它是**动态分配**内存的，只占用实际使用的空间。
  - **支持交换**（swapping）到磁盘。
  - 是现代 Linux 系统中更推荐和更常用的内存文件系统解决方案。

简而言之，`tmpfs` 是一种更智能、更灵活、更节省内存的内存文件系统解决方案。

#### 补充2：虚拟或伪文件系统

在 Linux（以及其他类 Unix 系统）中，“虚拟文件系统”或“伪文件系统”是指**不直接存储在物理磁盘上的文件系统**。它们是由内核在运行时动态创建和维护的，通常用于向用户空间程序提供系统信息、配置选项或进程间通信机制。

这些文件系统之所以被称为“虚拟”或“伪”，是因为：

1. **没有底层物理存储**：它们不占用传统的硬盘空间。其数据通常存在于内存（RAM）中，或者是在被访问时由内核即时生成。
2. **动态内容**：文件和目录的内容不是静态的，而是反映了系统当前的实时状态、硬件配置、运行进程等。当你读取它们时，内核会根据请求动态地生成数据。
3. **接口一致性**：尽管它们不是真正的磁盘文件，但它们提供了一致的文件系统接口。这意味着你可以使用标准的 Linux 命令（如 `ls`、`cat`、`cd`、`echo`、`mount`、`df` 等）来访问、查看和（在某些情况下）修改它们，就像操作普通文件一样。

### 常见的虚拟/伪文件系统

Linux 中有几个非常重要的虚拟文件系统：

1. **`/proc` (procfs)**：

   - **作用**：提供关于**进程信息**和**内核状态**的接口。
   - 特点：
     - 对于每个正在运行的进程，`/proc` 下都有一个以其 PID（进程 ID）命名的目录，例如 `/proc/1234`。这些目录中包含了该进程的各种信息，如命令行参数、环境变量、打开的文件描述符、内存映射等。
     - 此外，`/proc`  还包含许多描述系统整体状态的文件，例如：
       - `/proc/cpuinfo`：CPU 信息。
       - `/proc/meminfo`：内存使用情况。
       - `/proc/mounts`：当前挂载的文件系统列表。
       - `/proc/sys/`：用于查看和修改内核参数的接口（通过 `sysctl` 命令也可以操作）。
   - **例子**：`cat /proc/cpuinfo` 可以查看 CPU 详细信息；`ls /proc/self/fd` 可以查看当前进程打开的文件描述符。
   - **数据来源**：当用户读取这些文件时，内核会实时收集相关数据并将其格式化为文本形式。

2. **`/sys` (sysfs)**：

   - **作用**：提供关于**设备模型**、**内核对象**和**硬件信息**的接口。
   - 特点：
     - `/sys` 是一个更结构化的虚拟文件系统，设计用于表示 Linux 内核设备模型中的对象层次结构。它暴露了内核中各种设备（如 CPU、内存、PCI 设备、USB 设备、块设备等）及其驱动程序的信息。
     - 用户可以通过读取 `/sys` 中的文件来获取硬件状态，甚至通过写入某些文件来配置硬件（如果内核允许）。
   - **例子**：`cat /sys/class/net/eth0/address` 可以查看网卡 MAC 地址；`ls /sys/block/sda/` 可以查看 `sda` 块设备的详细信息。
   - **数据来源**：数据也是由内核动态生成，反映设备和驱动的当前状态。

3. **`/dev/shm` (tmpfs)**：

   - **作用**：提供一个基于 RAM 的**共享内存文件系统**。

   - 特点

     ：

     - `/dev/shm` 是一个 `tmpfs` 文件系统，它将文件存储在内存中（实际上是文件系统缓存，如果内存不足可以交换到 SWAP ）。
     - 它的主要目的是用于进程间通信（IPC），允许多个进程通过读写共享的内存文件来交换数据，这比传统的磁盘 I/O 快得多。
     - 存储在 `/dev/shm` 中的数据在系统重启后会丢失，因为它存储在易失性内存中。

   - **例子**：许多数据库系统（如 Oracle）和 Web 服务器（如 Nginx 缓存）会利用 `/dev/shm` 来提高性能。

   - **数据来源**：内存。

4. **`/run` (tmpfs)**：

   - **作用**：存储运行时数据，这些数据通常在系统启动后创建，并在系统关闭时删除。

   - 特点

     ：

     - 类似于 `/dev/shm`，`/run` 也是一个 `tmpfs` 文件系统，数据存在于内存中。
     - 它用于存储各种运行时信息，例如进程 ID 文件（PID 文件）、锁文件、套接字文件等，这些文件对于正在运行的服务和程序的正确操作至关重要。

   - **例子**：`sshd.pid` 文件通常存在于 `/run/sshd.pid`，记录了 SSH 守护进程的 PID。

5. **`/dev` (devtmpfs 或 udev)**：

   - **作用**：包含设备文件，这些文件代表系统上的硬件设备。

   - 特点

     ：

     - 传统上，`/dev` 目录中的设备文件是静态创建的。但现代 Linux 系统（使用 `udev` 或 `devtmpfs`）会**动态**地创建和删除这些设备文件，以反映当前连接到系统的硬件。
     - 例如，当你插入一个 USB 驱动器时，`/dev` 下会动态出现一个新的设备文件（如 `/dev/sdd`）。

   - **数据来源**：由 `udev`（用户空间守护进程）或 `devtmpfs`（内核实现）根据内核检测到的硬件事件动态管理。

#### 为什么需要虚拟/伪文件系统？

- **统一接口**：将系统信息和硬件控制以文件和目录的形式呈现，使得用户和程序可以使用熟悉的工具和 API 来访问和管理这些复杂的内部数据，而无需特殊的系统调用或内核编程。
- **实时性**：提供对系统实时状态的动态访问，数据是最新且精确的。
- **安全性与抽象**：通过文件系统权限来控制对特定系统信息的访问，并抽象化了底层复杂的内核数据结构。
- **易用性**：简化了对系统参数的查询和修改，使得自动化脚本编写更为方便。

总而言之，虚拟或伪文件系统是 Linux 内核提供的一种巧妙机制，它们将复杂的、动态的系统信息和硬件接口“映射”到我们熟悉的、统一的文件系统结构中，极大地提高了系统的可管理性和可编程性。

## 7. du: Disk

`du` (disk usage) 是一个在类 Unix 系统（包括 Linux）中广泛使用的命令行工具，用于**估算文件和目录的磁盘空间使用量**。它会递归地遍历指定目录及其子目录中的所有文件，并计算它们所占用的磁盘空间。

### `du` 命令的基本用途

`du` 命令的主要目的是帮助用户了解文件系统上哪些文件或目录占用了大量的空间，从而进行磁盘空间管理、找出占用空间大的文件或目录，以便进行清理或迁移。

### `du` 命令的基本语法

```bash
du [选项] [文件或目录]
```

- **不带任何参数和文件/目录**：默认情况下，`du` 会显示当前目录及其所有子目录的磁盘使用量，包括文件。输出的单位通常是**块（block）**，每个块的大小通常是 1KB（1024 字节），但具体大小可能因文件系统和系统配置而异。

  例如：

  ```bash
  ❯ du
  40      ./test_inline_function
  24      ./bin
  84      .
  ```

  上面的 `.` 表示当前目录的总大小。注意当前目录总大小不一定等于子目录大小之和，这是因为当前目录下还可能有一些文件。

- **指定文件或目录**：

  ```
  du /path/to/directory
  du /path/to/file.txt
  ```

### `du` 命令的常用选项

`du` 命令有很多有用的选项，可以帮助你更清晰地查看磁盘使用情况：

1. **`-h`, `--human-readable`：以人类可读的格式显示大小。** 这是最常用的选项，它会将大小显示为 K (KB), M (MB), G (GB) 等，使得输出更易于理解。

   ```bash
   ❯ du -h
   40K     ./test_inline_function
   24K     ./bin
   84K     .
   ```

2. **`-s`, `--summarize`：只显示总计大小。** 这个选项不会列出每个子目录的大小，只会显示指定目录或文件的总大小。当你想快速知道某个目录的总大小而不关心其内部细节时非常有用。

   ```bash
   ❯ du ./ -s
   84      ./
   ```

3. **`-a`, `--all`：显示所有文件（包括目录和文件）的磁盘使用量。** 默认情况下，`du` 只显示目录的合计大小。使用此选项会列出每个文件的独立大小。

   ```bash
   ❯ du -ah
   8.0K    ./test.cpp
   4.0K    ./main.cpp
   4.0K    ./test_inline_function/main.cpp
   20K     ./test_inline_function/app
   4.0K    ./test_inline_function/imp1.cpp
   4.0K    ./test_inline_function/header.h
   4.0K    ./test_inline_function/imp2.cpp
   40K     ./test_inline_function
   20K     ./bin/app
   24K     ./bin
   4.0K    ./makefile
   84K     .
   ```

   我们注意到，`./bin` 目录下只有一个 `app` 文件，大小为 20k，但是 `./bin` 的总大小却为 24k，这可能是因为当前目录 `.` 自身在文件系统中占用的一个块（因为它需要存储其包含的文件和子目录的元数据）。

4. **`-c`, `--total`：在末尾显示所有参数的总计。** 如果你指定了多个文件或目录，这个选项会在最后一行显示它们的总和。

   ```bash
   > du -ch dir1 dir2
   8.0K    dir1
   12K     dir2
   20K     total
   ```

5. **`-x`, `--one-file-system`：跳过不同文件系统上的目录。** 当你在一个挂载了其他文件系统的目录下运行 `du` 时，这个选项可以防止 `du` 跨越文件系统边界进行统计，确保只统计当前文件系统上的使用量。

   ```bash
   du -shx /
   ```

   这会显示根目录 `/` 所在的**文件系统**的总使用量，而不包括挂载到 `/` 下的其他分区。

6. **`--max-depth=<N>`**：限制 **显示** 深度。 

   ``` bash
   print the total for a directory (or file, with --all) only if it is N or fewer levels below the command line argument;  --max-depth=0 is the same as --summarize
   ```

7. **`-B <SIZE>`, `--block-size=<SIZE>`：指定输出的块大小。** 可以强制 `du` 以特定的单位显示大小。例如，`-BM` 表示以 MB 为单位，`-BG` 表示以 GB 为单位。

### `du` 的常见应场景

- **查找占用空间最大的目录或文件**：

  Bash

  ```bash
  du -sh * | sort -rh | head -n 10
  ```

  这条命令会显示当前目录下（包括文件和子目录）最大的 10 个项目。

  - `du -sh *`：显示当前目录下每个文件/目录的汇总大小，并以人类可读格式显示。
  - `sort -rh`：对输出进行排序，`-r` 表示逆序（从大到小），`-h` 表示按照人类可读的数字进行排序。
  - `head -n 10`：只显示前 10 行。

- **清理磁盘空间**： 通过 `du` 找出大文件或不再需要的目录，然后使用 `rm` 命令删除它们。

- **监控磁盘使用情况**： 定期运行 `du` 报告，可以帮助你了解磁盘空间使用量的变化趋势。

- **脚本自动化**： 在自动化脚本中使用 `du` 来检查某个目录的空间是否超出阈值，然后触发警告或清理操作。

### `du` 与 `df` 的区别

常常有人会将 `du` 和 `df` 命令混淆，它们都与磁盘空间有关，但用途不同：

- **`du` (disk usage)**：**估算文件或目录所占用的磁盘空间。** 它是通过遍历文件和目录来计算的，统计的是**实际使用**的块数。
- **`df` (disk free)**：**报告文件系统的总容量、已用空间、可用空间和挂载点。** 它统计的是整个文件系统的“块”级信息，通常与文件系统的元数据有关。

**简而言之：**

- `du` 告诉你**某个文件或目录**占了多少空间。
- `df` 告诉你**某个分区（文件系统）**还有多少空间可用。

## 8. lsblk: Device

`lsblk` (list block devices) 是一个在 Linux 系统中非常有用的命令，用于列出关于块设备（如硬盘、SSD、USB 驱动器以及它们的各个分区）的详细信息。它通常以树状结构显示这些信息，使得设备及其分区的关系一目了然。

### `lsblk` 命令的作用

- **显示所有块设备:** 列出系统中所有可用的块设备，包括物理硬盘、固态硬盘、USB 存储设备、逻辑卷（LVM）、RAID 设备等。
- **查看分区信息:** 显示每个磁盘上的分区情况，包括分区名称、大小、类型等。
- **识别挂载点:** 显示设备或分区当前被挂载到文件系统中的哪个位置。
- **获取文件系统信息:** 可以显示文件系统类型、标签和 UUID。
- **故障排除:** 在磁盘空间不足、分区错误或设备未被识别时，`lsblk` 是一个重要的诊断工具。

### `lsblk` 命令的语法

```
lsblk [选项] [设备...]
```

- **`[选项]`**: 用于修改命令行为和输出格式的标志。
- **`[设备...]`**: 可选参数，指定要列出的特定块设备。如果不指定设备，`lsblk` 会列出所有检测到的块设备。

### `lsblk` 命令的默认输出列解释

当不带任何选项运行 `lsblk` 时，它会输出以下默认列：

- **`NAME`**: 设备名称。例如，`sda` 代表第一块 SCSI/SATA 硬盘，`sda1` 是它的第一个分区，`nvme0n1` 代表第一块 NVMe 硬盘，`nvme0n1p1` 是它的第一个分区。
- **`MAJ:MIN`**: 设备的主设备号和次设备号。这两个数字唯一标识系统中的设备。主设备号表示设备类型（例如，磁盘驱动器），次设备号表示特定设备的实例或分区。
- **`RM`**: 可移动设备标志。如果设备是可移动的（例如 USB 驱动器），则显示 `1`，否则显示 `0`。
- **`SIZE`**: 设备或分区的大小。通常以人类可读的格式（如 `G` 代表 GB，`M` 代表 MB）显示。
- **`RO`**: 只读标志。如果设备或分区是只读的，则显示 `1`，否则显示 `0`。
- `TYPE`: 设备类型。常见的类型有：
  - `disk`: 整个磁盘设备。
  - `part`: 磁盘分区。
  - `lvm`: LVM 逻辑卷。
  - `rom`: 只读光盘设备（如 CD/DVD 驱动器）。
  - `loop`: 循环设备（通常用于挂载 ISO 镜像或 Snap 包）。
- **`MOUNTPOINT`**: 设备或分区的挂载点。如果设备或分区已挂载到文件系统中的某个目录，则显示该目录的路径。如果未挂载，则为空。

### `lsblk` 命令常用选项

`lsblk` 提供了许多选项，用于定制输出或过滤信息：

- **`-a`, `--all`**: 显示所有块设备，包括空设备和 RAM 磁盘。默认情况下，`lsblk` 会过滤掉一些不常用的设备。

- `-b`, `--bytes`: 以字节为单位显示 `SIZE` 列，而不是人类可读的格式。这对于精确的脚本处理非常有用。

- `-d`, `--nodeps`: 不显示设备的从属（slave）设备。例如，只显示磁盘本身，不显示其分区。

  - **示例**: `lsblk -d /dev/sda`

- `-f`, `--fs`: 显示文件系统信息，包括 `FSTYPE` (文件系统类型)、`LABELs` (文件系统标签) 和 `UUID` (通用唯一标识符)。

  - **示例**: `lsblk -f`

  - 输出示例:

    ```
    NAME        FSTYPE      LABEL UUID                                 MOUNTPOINT
    sda
    ├─sda1      ext4        boot  a1b2c3d4-e5f6-7890-1234-567890abcdef /boot
    └─sda2      LVM2_member       fedcba98-7654-3210-fedc-ba9876543210
      ├─vg-root ext4              09876543-2109-8765-4321-098765432109 /
      └─vg-swap swap              12345678-90ab-cdef-1234-567890abcdef [SWAP]
    sdb         ext4        data  abcdef12-3456-7890-abcd-ef1234567890 /data
    ```

- **`-i`, `--ascii`**: 使用 ASCII 字符进行树状输出，而不是默认的 Unicode 字符。这在一些旧终端或需要纯文本输出的场景下很有用。

- `-l`, `--list`: 以列表格式显示输出，而不是树状格式。`

- `-m`, `--perms`: 显示设备所有者、组和权限模式信息。

- `-o`, `--output <列名列表>`: 指定要显示的列。可以使用逗号分隔多个列名。要查看所有可用的列，可以使用 `--help` 选项，或者直接使用 `-O`。

  - **常用列名**: `NAME`, `SIZE`, `FSTYPE`, `MOUNTPOINT`, `UUID`, `LABEL`, `RO`, `RM`, `TYPE`, `MAJ:MIN`, `PHY-SEC`, `LOG-SEC` (物理/逻辑扇区大小), `VENDOR`, `MODEL`, `SERIAL` 等。
  - **示例**: `lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINT`

- **`-O`, `--output-all`**: 显示所有可用的列。

- `-p`, `--paths`: 显示设备的完整路径。

  - **示例**: `lsblk -p`

- **`-S`, `--scsi`**: 仅显示 SCSI 设备。

- **`-t`, `--topology`**: 显示拓扑信息，包括设备驱动器、逻辑/物理扇区大小、可写缓存等。

- **`-h`, `--help`**: 显示帮助信息并退出。

- **`-V`, `--version`**: 显示版本信息并退出。

### 注意事项

- `lsblk` 命令通常不需要 `sudo` 权限即可运行，因为它从 `/sys` 虚拟文件系统和 `udev` 数据库中获取信息。但某些特定选项（例如需要读取设备上的文件系统标签或 UUID 时，如果 `udev` 数据库不可用）可能需要 root 权限。
- `lsblk` 主要用于显示块设备的静态信息和它们之间的关系，而不是实时的磁盘使用情况。要查看文件系统的磁盘空间使用情况，应使用 `df` 命令。要查看目录或文件的大小，可以使用 `du` 命令。

## 9. lsof: File

`lsof` 是一个在 Unix-like 系统中非常强大的命令行工具，其名称是 **"list open files"（列出打开的文件）**的缩写。在 Linux 中，“一切皆文件” 的哲学使得 `lsof` 不仅仅能列出普通文件，还能列出 **目录、设备、管道 (pipe)、网络套接字 (socket)** 等各种**被进程打开的资源**。

### `lsof` 命令的作用

`lsof` 的主要作用是显示系统上所有被进程打开的文件和网络连接的详细信息。它在以下场景中非常有用：

1. **查找文件被哪个进程占用**：当你想卸载一个文件系统或删除一个文件，但系统提示“设备忙”或“文件被占用”时，`lsof` 可以帮助你找出是哪个进程在使用它。
2. **监控网络连接和端口**：可以查看哪些进程正在监听哪些端口，或者哪些进程正在进行网络通信。这对于网络故障排查和安全审计非常有用。
3. **发现异常进程或文件**：通过列出所有打开的文件，可以帮助发现一些不正常的进程或可疑的文件访问行为。
4. **管理系统资源**：找出哪些进程占用了大量文件描述符，或者哪些被删除但仍被进程持有的文件正在占用磁盘空间。
5. **调试应用程序**：帮助开发者了解应用程序打开了哪些文件、使用了哪些库，或者是否存在文件泄漏。

### `lsof` 命令的基本语法

```
lsof [选项]
```

不带任何选项直接运行 `lsof` 会列出系统上所有打开的文件，这通常会产生大量输出。因此，通常需要结合各种选项来过滤结果。

### `lsof` 命令输出的字段解释

`lsof` 的输出通常包含以下列：

- **COMMAND**：打开文件的进程的命令名称。
- **PID**：进程的进程ID (Process ID)。
- **TID**：线程ID (Task ID)。如果为空，表示是进程而不是线程。
- **USER**：进程的所有者用户名或用户ID。
- **FD：**文件描述符 (File Descriptor)。这表示进程如何使用文件。常见的描述符类型包括：
  - **cwd**：当前工作目录 (Current Working Directory)。
  - **txt**：程序的可执行文本 (Text) 文件。
  - **mem**：内存映射 (Memory-mapped) 文件。
  - **数字 (n)：**实际的文件描述符数字。
    - `n u`：文件描述符 *n*，以读写模式打开 (read and write)。
    - `n r`：文件描述符 *n*，以只读模式打开 (read only)。
    - `n w`：文件描述符 *n*，以只写模式打开 (write only)。
    - `n W`：文件描述符 *n*，以写模式打开并锁定整个文件 (write and with write lock on entire file)。
  - **0**：标准输入 (stdin)。
  - **1**：标准输出 (stdout)。
  - **2**：标准错误 (stderr)。
- **TYPE：**文件类型。常见的类型包括：
  - **REG**：普通文件 (Regular file)。
  - **DIR**：目录 (Directory)。
  - **CHR**：字符设备 (Character special file)。
  - **BLK**：块设备 (Block special file)。
  - **FIFO**：命名管道 (First In First Out)。
  - **SOCK**：套接字 (Socket)。
  - **UNIX**：Unix 域套接字 (UNIX domain socket)。
  - **IPv4**：IPv4 网络文件。
  - **IPv6**：IPv6 网络文件。
- **DEVICE**：设备号。对于文件，表示文件系统所在的设备的设备号（主设备号，次设备号）。
- **SIZE/OFF**：文件大小（字节）或文件偏移量。对于网络文件，通常显示为 `0t0`。
- **NODE**：文件的 inode 号（索引节点号）。对于网络文件，显示为网络协议相关的信息。
- **NAME**：文件的名称，或者网络连接的本地和远程地址。

### `lsof` 命令的常用选项和示例

以下是一些 `lsof` 的常用选项和实用示例：

1. **列出所有打开的文件（不带任何选项）**：

   ```bash
   lsof
   ```

   输出会非常多，通常会结合 `less` 或 `grep` 使用。

   ```bash
   lsof | less
   ```

2. **列出某个用户打开的文件**：

   ```bash
   lsof -u username
   # 示例：列出用户 'john' 打开的文件
   lsof -u john
   ```

   要排除某个用户，可以使用 `^`：

   ```bash
   lsof -u ^root # 列出所有非 root 用户打开的文件
   ```

3. **列出某个进程打开的文件**：

   - 按进程ID (PID)

     ```bash
     lsof -p PID
     # 示例：列出 PID 为 1234 的进程打开的文件
     lsof -p 1234
     ```

   - 按进程名称 (COMMAND)

     ```bash
     lsof -c command_name
     # 示例：列出 'sshd' 进程打开的文件
     lsof -c sshd
     ```

     可以使用多个 `-c` 选项来匹配多个命令：

     ```bash
     lsof -c sshd -c systemd
     ```

4. **列出某个文件被哪个进程占用**：

   ```bash
   lsof /path/to/file
   # 示例：查看 /var/log/syslog 被哪个进程占用
   lsof /var/log/syslog
   ```

   对于目录，它会显示将该目录作为其工作目录的进程：

   ```bash
   lsof /var/log/
   ```

5. **列出网络连接**：

   * 列出网络连接

     ``` bash
     lsof -i     # 列出所有网络链接
     lsof -i TCP # 列出所有 TCP 连接
     lsof -i UDP # 列出所有 UDP 连接
     ```

   - 列出监听特定端口的进程

     ```bash
     lsof -i :port_number
     # 示例：查看哪个进程监听 80 端口
     lsof -i :80
     ```

   - 列出与特定 IP 地址和端口相关的连接

     ```bash
     lsof -i @IP_address:port_number
     # 示例：查看与 192.168.1.100 的 22 端口相关的连接
     lsof -i @192.168.1.100:22
     ```

   - 列出所有处于 LISTEN 状态的 TCP 连接

     ```bash
     lsof -i TCP -s TCP:LISTEN
     ```

6. **列出已删除但仍被进程打开的文件**： 有时文件被删除后，如果仍有进程持有其文件描述符，那么磁盘空间不会被立即释放。

   ```bash
   lsof | grep deleted
   ```

7. **结合多个选项**： 可以使用 `-a` (AND) 选项来组合多个条件，表示所有条件都必须满足。默认情况下，多个条件是 OR 关系。

   ```bash
   # 示例：列出用户 'john' 并且 PID 为 1234 的进程打开的文件 (AND 关系)
   lsof -u john -p 1234 -a
   ```

   注意：没有 `-a` 时，`lsof -u john -p 1234` 会列出用户 john 打开的所有文件 **或** PID 为 1234 的进程打开的所有文件。

8. **列出指定文件描述符类型的文件**：

   ```bash
   lsof -d FD_type
   # 示例：列出所有内存映射文件
   lsof -d mem
   # 示例：列出所有标准输入、输出、错误文件
   lsof -d 0,1,2
   ```

9. **输出格式控制**：

   - `-F fmt`：生成适合程序解析的输出格式。
   - `-l`：显示用户ID而不是用户名。
   - `-n`：不将网络号转换为主机名。
   - `-P`：不将端口号转换为服务名。

### 常见的实际应用场景

- **解决磁盘空间问题**：

  ```bash
  lsof | grep "deleted"
  ```

  如果发现大量被删除的文件仍然被占用，可以考虑重启相关进程或杀死它们以释放磁盘空间。

- **查找占用端口的进程**： 当一个服务无法启动，提示端口已被占用时：

  ```bash
  lsof -i :8080
  ```

  找到 PID 后，可以使用 `kill PID` 来终止该进程。

- **检查可疑的网络活动**：

  ```bash
  lsof -i TCP
  ```

  可以查看是否有不认识的进程在进行网络通信。

- **查看进程的当前工作目录**：

  ```bash
  lsof -p PID | grep cwd
  ```

`lsof` 是一个非常灵活和强大的工具，通过查阅其 `man` 手册页 (`man lsof`) 可以了解更多高级用法和所有可用的选项。

# 四、网络工具

## 1. ethtool

**`ethtool`（Ethernet tool）** 是一个功能强大的 Linux 命令行工具，主要用于**查询和配置以太网设备的各种参数**。它允许系统管理员对网卡的工作模式、链路状态、驱动程序信息、硬件卸载功能、统计数据等进行详细的查看和调整。

### `ethtool` 的主要作用：

- **查询网卡信息：** 获取网卡驱动程序版本、固件版本、总线信息等。
- **查看链路状态：** 检查网卡是否已连接，链路速度（例如 100Mbps、1Gbps）、双工模式（半双工或全双工）。
- **配置链路参数：** 手动设置网卡的链路速度和双工模式（例如，强制设置为 100Mbps 全双工）。
- **管理硬件卸载（Offload）功能：** 开启或关闭网卡的各种硬件卸载功能，如 TCP Segmentation Offload (TSO)、Generic Receive Offload (GRO)、checksum offload 等。这些功能可以将一些网络处理任务从 CPU 卸载到网卡硬件，从而提高网络性能和降低 CPU 负载。
- **查看和清除统计信息：** 获取网卡接收和发送数据包的统计信息，如错误包数量、丢弃包数量等，并可以重置这些计数器。
- **控制网卡指示灯：** 让网卡指示灯闪烁，以便在物理上识别特定的网卡。
- **执行自检：** 对网卡硬件进行自检以诊断潜在问题。

### `ethtool` 的常用选项和用法：

`ethtool` 命令的基本语法是 `ethtool [选项] <网络接口名称>`。

以下是一些常用的 `ethtool` 选项及其用途：

- **`ethtool <interface>`：** 显示指定网络接口的当前设置。
  - 例如：`ethtool eth0` 会显示 `eth0` 网卡的链路速度、双工模式、自动协商状态、端口类型等。
- **`ethtool -i <interface>`：** 显示指定网络接口的驱动程序信息。
  - 例如：`ethtool -i eth0` 会显示网卡的驱动名称、版本、固件版本、总线信息等。
- **`ethtool -s <interface> [speed <speed>] [duplex <half|full>] [autoneg <on|off>]`：** 设置指定网络接口的参数。
  - 例如：`ethtool -s eth0 speed 1000 duplex full autoneg off` 会将 `eth0` 网卡的速度强制设置为 1Gbps，全双工，并关闭自动协商。
  - **注意：** 并非所有网卡和驱动都支持所有这些设置，有些设置可能需要网卡或驱动程序支持。强制设置可能导致网络不稳定或无法连接。
- **`ethtool -K <interface> [feature <on|off>]`：** 开启或关闭指定网络接口的硬件卸载功能。
  - 例如：
    - `ethtool -K eth0 gro off` 关闭 `eth0` 的 GRO 功能。
    - `ethtool -K eth0 tso on` 开启 `eth0` 的 TSO 功能。
  - 常用的卸载功能包括：
    - `rx-checksum` / `tx-checksum` (接收/发送校验和卸载)
    - `sg` (Scatter-gather 卸载)
    - `tso` (TCP Segmentation Offload)
    - `gso` (Generic Segmentation Offload)
    - `gro` (Generic Receive Offload)
    - `lro` (Large Receive Offload) - 通常被 GRO 取代
    - `rxvlan` / `txvlan` (VLAN 卸载)
- **`ethtool -S <interface>`：** 显示指定网络接口的详细统计信息。
  - 例如：`ethtool -S eth0` 会显示接收/发送的字节数、数据包数、错误数、丢弃数等，这些统计信息可以帮助诊断网络问题。
- **`ethtool -t <interface>`：** 对指定网络接口进行自检。
  - 例如：`ethtool -t eth0`。这会运行一系列测试来检查网卡硬件是否正常工作。
- **`ethtool -p <interface> [time]`：** 触发指定网络接口的指示灯闪烁。
  - 例如：`ethtool -p eth0 10` 会让 `eth0` 的指示灯闪烁 10 秒，方便在物理机架中定位网卡。
- **`ethtool -L <interface> [combined <N>]`：** 配置网卡的 RX/TX 队列数量。
  - 例如：`ethtool -L eth0 combined 4` 设置 `eth0` 的接收/发送队列合并为 4 个。这对于高性能网络和多核 CPU 系统很有用。

### 总结：

`ethtool` 是 Linux 系统中网络管理不可或缺的工具。通过它，管理员可以深入了解网卡的硬件和驱动状态，优化网络性能，诊断网络故障，并进行精细化的网络配置。熟练掌握 `ethtool` 的使用对于任何 Linux 系统管理员都是非常有益的。

## 2. netstat

`netstat`（network statistics）是一个用于显示各种网络相关数据结构内容的命令行工具。它是一个强大的网络管理和故障排除工具，可以提供关于网络连接、路由表、接口统计以及协议统计的详细信息。

### `netstat` 命令的主要作用

1. **显示活动网络连接：** 查看当前系统上所有活动的 TCP、UDP 连接，以及它们的状态（如建立连接、监听中、等待关闭等）。
2. **显示监听端口：** 哪些端口正在被应用程序监听，等待传入连接。
3. **显示路由表信息：** 查看系统的路由表，了解数据包如何从本地主机发送到目标地址。
4. **显示网络接口统计：** 查看网络接口的收发字节数、数据包数、错误数等统计信息。
5. **显示协议统计信息：** 查看 TCP、UDP、ICMP、IP 等协议的统计数据，例如发送和接收的数据包数量、错误数量等。
6. **进程ID (PID) 和程序名称：** 在某些操作系统（如Windows、Linux）上，可以显示与特定连接或监听端口关联的进程ID和程序名称，这对于识别是哪个应用程序在使用网络资源非常有帮助。

### `netstat` 命令的基本语法

```bash
netstat [选项]
```

### `netstat` 常用选项详解

以下是一些常用的 `netstat` 选项及其解释：

- `-a` 或 `--all`：

  显示所有连接和监听端口。如果没有此选项，通常只显示已建立的连接。

- `-n` 或 `--numeric`：

  以数字形式显示地址和端口号，而不是尝试解析主机名、服务名。这可以加快输出速度，尤其是在 DNS 解析速度慢的环境中。

- `-p <协议>` 或 `--protocol=<协议>`：

  显示指定协议的连接或统计信息。常用的协议有 tcp、udp、icmp、ip、tcpv6、udpv6 等

  - **示例：** `netstat -p tcp` (只显示TCP连接)
  - **示例：** `netstat -s -p tcp udp` (只显示TCP和UDP的统计信息)

- `-o` (仅限Windows) / `-P` (Linux/Unix)：

  显示与每个连接关联的进程 ID (PID)。在Windows上，可以通过任务管理器根据 PID 找到相应的应用程序。在Linux/Unix 上，通常需要 root 权限才能看到 PID 和程序名称。

  - **示例 (Windows)：** `netstat -o`
  - **示例 (Linux)：** `sudo netstat -p`

- `-b` (仅限Windows)：

  显示创建每个连接或监听端口涉及的可执行文件。此选项可能很耗时，且需要足够的权限。

  - **示例：** `netstat -b`

- `-e` 或 `--extend`：

  显示以太网统计信息，例如发送和接收的字节数和数据包数。此参数通常与 `-s` 一起使用。

  - **示例：** `netstat -e` 或 `netstat -e -s`

- `-s` 或 `--statistics`：

  按协议显示统计信息。默认情况下，会显示 TCP、UDP、ICMP 和 IP 协议的统计信息。如果安装了 IPv6 协议，则会显示基于 IPv6 的协议统计信息。

- `-r` 或 `--route`：显示路由表信息。

- `-i` 或 `--interfaces`：

  显示网络接口的统计信息（如接口名称、MTU、接收/发送的错误和丢包数量）。

- `-c` 或 `--continuous`：

  持续显示网络状态，每隔一段时间刷新一次。可以通过指定一个时间间隔（秒）来控制刷新频率。

  - **示例：** `netstat -c 5` (每5秒刷新一次)

- `-l` 或 `--listening`：仅显示处于监听（Listening）状态的套接字。

- `-t`：仅显示TCP连接。

- `-u`：仅显示UDP连接。

### 常见使用场景和示例

- **查看所有活动的 TCP 连接和监听端口（不解析名称）：** `netstat -an`
- **查看所有监听中的 TCP 端口：** `netstat -lntp` (Linux) `netstat -ano | findstr "LISTENING"` (Windows)
- **查看哪个进程正在使用某个端口（例如端口 80）：** `netstat -anop | grep :80` (Linux) `netstat -ano | findstr ":80"` (Windows，然后根据PID查看任务管理器)
- **查看TCP协议的统计信息：** `netstat -s -p tcp`
- **查看路由表：** `netstat -r`
- **持续监控网络连接（每2秒刷新一次）：** `netstat -c 2` (Linux) `netstat -ano 2` (Windows)

### 输出列的含义

`netstat` 命令的输出通常包含以下列（具体取决于操作系统和选项）：

- **Proto (协议)：** 连接使用的协议（如 TCP、UDP）。
- **Local Address (本地地址)：** 本地计算机的 IP 地址和端口号。
- **Foreign Address (外部地址)：** 远程计算机的 IP 地址和端口号。
- **State (状态)：**TCP 连接的状态，如：
  - `LISTENING`：正在监听传入连接。
  - `ESTABLISHED`：连接已建立。
  - `TIME_WAIT`：连接已终止，但仍在等待，以确保远程端收到连接终止的确认。
  - `CLOSE_WAIT`：远程端已关闭连接，本地端正在等待关闭。
  - `SYN_SENT`：已发送连接请求，等待对方确认。
  - `SYN_RECV`：已收到连接请求，已发送确认，等待对方确认。
  - `FIN_WAIT1` / `FIN_WAIT2`：连接正在关闭。
  - `CLOSED`：连接已关闭。
- **PID (进程ID)：** 占用该连接或端口的进程ID。
- **Program Name (程序名称)：** 占用该连接或端口的程序名称（仅限某些操作系统和选项）。
- **Recv-Q (接收队列)：** 接收队列中的字节数（已接收但尚未被应用程序读取的数据）。
- **Send-Q (发送队列)：** 发送队列中的字节数（已发送但尚未被远程主机确认的数据）。

`netstat` 是一个非常实用的网络工具，掌握它的使用对于网络故障排查、系统安全审计以及了解系统网络活动至关重要。

## 3. host

`host` 命令是一个简单而强大的命令行工具，用于执行 DNS (Domain Name System) 查询。它主要用于将域名解析为 IP 地址，以及将 IP 地址解析为域名（反向查询）。对于网络管理员、开发人员和 IT 专业人员来说，它是一个非常有用的工具，可以帮助他们进行网络故障排除和调试依赖于 DNS 的应用程序。

### 主要功能

- **域名到 IP 地址的解析 (A/AAAA 记录查询):** 这是 `host` 命令最基本的功能。当你提供一个域名时，它会返回该域名对应的 IPv4 (A 记录) 或 IPv6 (AAAA 记录) 地址。
- **IP 地址到域名的反向解析 (PTR 记录查询):** 当你提供一个 IP 地址时，`host` 命令会查询对应的 PTR (Pointer) 记录，返回与该 IP 地址关联的域名。这通常用于反向 DNS 查找。
- 查询各种 DNS 记录类型: `host` 命令不仅仅限于 A/AAAA 和 PTR 记录。它还可以查询多种其他类型的 DNS 记录，例如：
  - **NS (Name Server) 记录:** 查询指定域名的权威 DNS 服务器。
  - **MX (Mail Exchange) 记录:** 查询指定域名的邮件交换服务器，用于电子邮件路由。
  - **SOA (Start of Authority) 记录:** 查询域名的起始授权记录，包含域名的基本属性、主名字服务器、管理员邮箱等信息。
  - **TXT (Text) 记录:** 查询文本记录，通常用于存储任意文本信息，如 SPF (Sender Policy Framework) 记录（用于电子邮件验证）或域所有权验证。
  - **CNAME (Canonical Name) 记录:** 查询域名的规范名称（别名）。
  - **HINFO (Host Information) 记录:** 查询主机 CPU 和操作系统类型。
  - **ANY 记录:** 查询所有可用的记录类型。
- **指定查询的 DNS 服务器:** 默认情况下，`host` 命令会使用系统配置的 DNS 服务器（通常在 `/etc/resolv.conf` 中）。但你可以指定一个特定的 DNS 服务器来进行查询。

### 命令语法

```
host [选项] 主机名或IP地址 [DNS服务器]
```

- **主机名或 IP 地址:** 你要查询的域名或 IP 地址。
- **DNS服务器 (可选):** 指定一个要查询的 DNS 服务器的名称或 IP 地址。

### 常用选项

- `-a` 或 `-v`: 显示所有可用的信息（等同于 `-v`，开启详细模式）。
- `-c <class>`: 指定 DNS 查询的类别。默认是 `IN` (Internet)。其他常见的有 `CHAOS`、`HESIOD`。
- `-d`: 开启调试模式，显示更详细的调试信息。
- `-l`: 列表模式，对指定的区域执行区域传输 (zone transfer)，并打印出 NS、PTR 和地址记录 (A/AAAA)。结合 `-a` 可以打印区域中的所有记录。**注意：** 区域传输通常只在授权的 DNS 服务器上被允许。
- `-n`: 等同于 `hostnew` 命令（在某些系统上）。
- `-r`: 禁用递归查询。它会模拟 DNS 服务器的行为，进行非递归查询，并期望接收到对其他名称服务器的引用（referrals）。
- `-t <type>`: 指定要查询的记录类型。常用的类型包括：`A`, `AAAA`, `MX`, `NS`, `SOA`, `TXT`, `CNAME`, `PTR`, `ANY` 等。
- `-T`: 强制使用 TCP 连接进行查询。默认情况下，`host` 命令使用 UDP 进行查询。当查询需要时（例如区域传输 AXFR 请求），TCP 会自动选择。
- `-w`: 永远等待 DNS 服务器的响应，直到收到回复。
- `-W <time>`: 设置等待响应的超时时间（秒）。如果 `time` 小于 1，则超时设置为 1 秒。默认情况下，`host` 等待 UDP 响应 5 秒，TCP 连接 10 秒。
- `-4`: 强制使用 IPv4。
- `-6`: 强制使用 IPv6。

### 示例

1. **查询域名的 IP 地址:**

   ```bash
   host google.com
   ```

   输出示例：

   ```bash
   google.com has address 142.250.187.14
   google.com has IPv6 address 2a00:1450:4009:80b::200e
   google.com mail is handled by 10 aspmx.l.google.com.
   google.com mail is handled by 20 alt1.aspmx.l.google.com.
   google.com mail is handled by 30 alt2.aspmx.l.google.com.
   google.com mail is handled by 40 alt3.aspmx.l.google.com.
   google.com mail is handled by 50 alt4.aspmx.l.google.com.
   ```

2. **查询 IP 地址对应的域名 (反向解析):**

   ```bash
   host 142.250.187.14
   ```

   输出示例：

   ```bash
   14.187.250.142.in-addr.arpa domain name pointer ord30s09-in-f14.1e100.net.
   ```

3. **查询域名的邮件交换 (MX) 记录:**

   ```bash
   host -t mx google.com
   ```

   输出示例：

   ```bash
   google.com mail is handled by 10 aspmx.l.google.com.
   google.com mail is handled by 20 alt1.aspmx.l.google.com.
   google.com mail is handled by 30 alt2.aspmx.l.google.com.
   google.com mail is handled by 40 alt3.aspmx.l.google.com.
   google.com mail is handled by 50 alt4.aspmx.l.google.com.
   ```

4. **查询域名的名称服务器 (NS) 记录:**

   ```bash
   host -t ns google.com
   ```

   输出示例：

   ```bash
   google.com name server ns1.google.com.
   google.com name server ns2.google.com.
   google.com name server ns3.google.com.
   google.com name server ns4.google.com.
   ```

5. **查询域名的文本 (TXT) 记录:**

   ```bash
   host -t txt google.com
   ```

   输出示例（可能包含 SPF 记录等）：

   ```bash
   google.com descriptive text "v=spf1 include:_spf.google.com ~all"
   google.com descriptive text "docusign=05C55A94-F8E3-404B-871B-A70A70F66BC9"
   ...
   ```

6. **查询域名的 SOA 记录:**

   ```bash
   host -t soa google.com
   ```

   输出示例：

   ```
   google.com has SOA record ns1.google.com. dns-admin.google.com. 156142728 900 900 1800 60
   ```

7. **指定 DNS 服务器进行查询:**

   ```bash
   host google.com 8.8.8.8
   ```

   这将使用 Google 的公共 DNS 服务器 (8.8.8.8) 来查询 `google.com`。

8. **显示所有可用的 DNS 信息:**

   ```bash
   host -a google.com
   ```

   这会显示非常详细的 DNS 信息，包括 A, AAAA, MX, NS, SOA 等记录。

### 与 `dig` 和 `nslookup` 的比较

`host`、`dig` 和 `nslookup` 都是用于 DNS 查询的工具，但它们各有侧重：

- **`host`:** 简洁易用，输出清晰，适用于快速查询和简单的 DNS 故障排除。
- **`dig`:** 功能最强大，输出最详细，可以进行复杂的 DNS 查询和调试。它通常是网络专业人员的首选。
- **`nslookup`:** 较老的工具，有两个模式（交互式和非交互式）。在某些情况下，`dig` 和 `host` 被认为是更现代和推荐的选择，但 `nslookup` 在许多系统上仍然可用并被广泛使用。

总的来说，`host` 命令是一个非常实用的 DNS 查询工具，以其简洁明了的输出和易用性而受到欢迎。

## 4. nslookup

`nslookup`（全称：**Name Server Lookup**）是一个命令行工具，用于查询域名系统（DNS）服务器以获取域名或 IP 地址的映射信息，以及其他各种 DNS 记录。它是网络管理员和用户诊断 DNS 相关问题、验证 DNS 配置和收集域信息的重要工具。

### `nslookup` 的工作原理

`nslookup` 通过向 DNS 服务器发送 DNS 查询请求来获取信息。当您输入一个 `nslookup` 命令时，该工具会向您指定或系统默认的 DNS 服务器发送一个 DNS 查询。服务器处理查询并响应所请求的信息，例如与域名关联的 IP 地址，或与 IP 地址关联的域名。`nslookup` 使用 DNS 协议与 DNS 服务器进行通信，根据查询类型和大小，它可以使用 UDP 和 TCP 协议。

### `nslookup` 的主要用途

- **查找域名的 IP 地址**：这是 `nslookup` 最常用也最基本的功能，用于将域名解析为 IPv4 或 IPv6 地址。
- **反向 DNS 查询**：根据 IP 地址查找对应的域名。
- **故障排除 DNS 问题**：当网站无法访问或电子邮件无法发送时，`nslookup` 可以帮助诊断是否是 DNS 解析问题。
- **检查 DNS 记录**：查看特定域名的各种 DNS 记录，例如邮件服务器（MX 记录）、名称服务器（NS 记录）等。
- **识别可疑域名**：发现与现有域名相似的恶意域名，以防范网络钓鱼等安全威胁。
- **验证 DNS 服务器配置**：确认 DNS 服务器是否正确配置并响应查询。

### `nslookup` 的两种模式

`nslookup` 命令工具可以在两种模式下运行：

1. **交互模式 (Interactive Mode)**：

   - 进入方式

     - 直接输入 `nslookup` 命令，不带任何参数。
     - 输入 `nslookup -`，然后可选地输入要使用的 DNS 服务器的名称或 IP 地址。

   - **特点**：进入交互模式后，命令提示符会变为 `>`。您可以在此提示符下输入多个查询、设置不同的选项，直到输入 `exit` 退出。这对于需要查找多个数据片段或进行复杂配置时非常有用。

   - 示例

     ```bash
     nslookup
     > example.com
     > set type=mx
     > example.com
     > server 8.8.8.8
     > example.com
     > exit
     ```

2. **非交互模式 (Non-interactive Mode)**：

   - **进入方式**：将要查找的主机名或 IP 地址作为第一个命令行参数。可选的第二个参数是 DNS 服务器的名称或 IP 地址。

   - **特点**：适用于只需要查找单个数据片段或在脚本、命令行或 PowerShell 中使用 `nslookup` 的情况。

   - 示例

     ```bash
     nslookup www.google.com 8.8.8.8
     nslookup 192.168.1.1
     ```

### `nslookup` 常用选项和子命令

在 `nslookup` 的交互模式中，您可以输入 `set` 命令来设置不同的查询选项，或者在非交互模式中作为命令行参数。

#### 常用选项 (在非交互模式中，通常以 `-` 开头)

- **`-query=<type>` 或 `-type=<type>`**：指定要查询的 DNS 记录类型。常用的类型包括：

  - `A`：地址记录，用于将域名映射到 IPv4 地址（默认类型）。

  - `AAAA`：IPv6 地址记录，用于将域名映射到 IPv6 地址。😀

  - `MX`：邮件交换记录，指定负责接收域电子邮件的邮件服务器。

  - `NS`：名称服务器记录，列出域的权威 DNS 服务器。

  - `CNAME`：规范名称记录，为域名创建别名。

  - `PTR`：指针记录，用于反向 DNS 查询，将 IP 地址映射到域名。

  - `SOA`：起始授权记录，提供有关 DNS 区域的基本信息，如主名称服务器、管理员邮箱等。

  - `TXT`：文本记录，存储任意文本信息，常用于 SPF、DKIM 等邮件验证和域验证。

  - `ANY`：查询所有可用的记录类型。

  - 示例

    ```bash
    nslookup -type=mx example.com
    nslookup -type=ns example.com
    nslookup -type=any example.com
    ```

- **`server <DNS服务器地址>`**：指定用于查询的 DNS 服务器。如果未指定，`nslookup` 会使用系统默认配置的 DNS 服务器。

  ```bash
  nslookup example.com 8.8.8.8  (非交互模式，使用 Google Public DNS)
  # 或在交互模式下：
  nslookup
  > server 1.1.1.1
  > example.com
  ```

- **`[no]debug`**：开启或关闭调试模式，显示更多详细的查询和响应信息。

  ```bash
  nslookup -debug example.com
  # 或在交互模式下：
  nslookup
  > set debug
  > example.com
  ```

- **`[no]recurse`**：开启或关闭递归查询。默认情况下是开启的，表示如果当前 DNS 服务器没有所需的信息，它会向其他 DNS 服务器请求。

  ```bash
  nslookup -norecurse example.com
  ```

- **`timeout=<seconds>`**：设置等待 DNS 服务器响应的初始超时时间（秒）。

  ```bash
  nslookup -timeout=5 example.com
  ```

- **`port=<port_number>`**：指定 DNS 查询的端口号，默认为 53。

  ```
  nslookup -port=5353 example.com
  ```

- **`domain=<domain_name>`**：更改默认的域名后缀。当您查询不带点号的主机名时，会自动追加此域名后缀。

  ```bash
  # 假设当前域是 "example.com"
  nslookup
  > set domain=example.com
  > host1  (会查询 host1.example.com)
  ```

- **`[no]search`**：开启或关闭使用域名搜索列表。如果查询请求包含至少一个句点（但不以尾随句点结束），`nslookup` 会将域名搜索列表中的域名追加到请求中，直到收到应答。

#### 交互模式下的其他子命令

- **`exit`**：退出 `nslookup` 交互模式。
- **`help` 或 `?`**：显示 `nslookup` 子命令的简短摘要。
- **`lserver <DNS服务器地址>`**：使用初始服务器查找指定域的信息。
- **`root`**：将默认服务器设置为根名称服务器。
- **`view <file>`**：对指定文件的内容进行排序并分页。

### `nslookup` 示例

1. **查询域名的 IPv4 地址 (A 记录)**：

   ```bash
   nslookup www.google.com
   ```

   输出示例：

   ```
   Server:         192.168.65.7         
   Address:        192.168.65.7#53       
   
   Non-authoritative answer:
   Name:   www.google.com
   Address: 31.13.94.41
   Name:   www.google.com
   Address: 2001::1
   ```

   * **`Server: 192.168.65.7`**: 这行指示了 `nslookup` 命令向哪台 **DNS 服务器** 发送了查询请求。在这种情况下，你的系统默认的 DNS 服务器是 `192.168.65.7`。这通常是你的路由器、本地网络中的一个 DNS 服务器，或者是由虚拟机软件（比如 Docker Desktop、WSL 2 或 VMware）创建的虚拟网络适配器所提供的 DNS 服务。

   * **`Address: 192.168.65.7#53`**: 这行进一步确认了用于查询的 DNS 服务器的 IP 地址，并指定了用于 DNS 查询的端口号——**53**。端口 53 是 DNS 协议的默认端口，用于发送和接收 DNS 查询请求。

   * **`Non-authoritative answer:`**: 这是非常重要的一行。它表示这个 DNS 响应不是直接来自 `www.google.com` 的**权威 DNS 服务器**。这意味着 `192.168.65.7` 这台 DNS 服务器是从它的**缓存**中，或者通过**递归查询**（向其他权威 DNS 服务器发起查询并获得答案）后，将结果返回给你的。如果你能直接从 `www.google.com` 的权威 DNS 服务器获得答案，这里会显示 `Authoritative answer:`。对于大多数日常的 DNS 查询来说，看到 `Non-authoritative answer` 是正常的。

     **`Name: www.google.com`**: 这表示你查询的域名是 `www.google.com`。

     **`Address: 31.13.94.41`**: 这是 `www.google.com` 对应的 **IPv4 地址**。当你的设备需要访问 `www.google.com` 时，它会尝试连接这个 IP 地址。

     **`Name: www.google.com`**

     **`Address: 2001::1`**: 这是 `www.google.com` 对应的 **IPv6 地址**。如果你的系统支持 IPv6 并且网络环境也支持，它可能会优先使用 IPv6 地址来访问服务。

     

2. **查询域名的 IPv6 地址 (AAAA 记录)**：

   ```bash
   nslookup -type=aaaa example.com
   ```

3. **查询域名的邮件交换记录 (MX 记录)**：

   ```bash
   nslookup -type=mx google.com
   ```

   输出示例：

   ```
   Server:         192.168.65.7
   Address:        192.168.65.7#53
   
   Non-authoritative answer:
   google.com      mail exchanger = 10 smtp.google.com.
   
   Authoritative answers can be found from:
   ```

4. **反向查询 IP 地址对应的域名 (PTR 记录)**：

   ```bash
   nslookup 8.8.8.8 8.8.4.4
   ```

   输出示例：

   ```
   8.8.8.8.in-addr.arpa    name = dns.google.
   
   Authoritative answers can be found from:
   ```

5. **指定 DNS 服务器进行查询**：

   ```bash
   nslookup example.com 8.8.8.8  (使用 Google 的 DNS 服务器)
   ```

6. **在交互模式下查询多个记录类型**：

   ```bash
   nslookup
   > set type=a
   > example.com
   > set type=ns
   > example.com
   > exit
   ```

### 注意事项

- `nslookup` 在某些系统上可能已被更现代的工具（如 `dig` 或 `host`）取代，因为 `nslookup` 有时被认为功能有限或输出格式不够灵活。然而，它仍然是一个广泛使用且易于理解的工具。
- `nslookup` 的输出可能包含“非权威应答”（Non-authoritative answer），这表示信息是从缓存中获取的，而不是直接从域的权威 DNS 服务器获取的。

总的来说，`nslookup` 是一个强大而实用的网络工具，对于日常的 DNS 查询和故障排除非常有帮助。

## 5. dig

`dig`**（Domain Information Groper）**命令是一个功能强大的命令行工具，用于查询域名系统（DNS）名称服务器。它执行 DNS 查找并显示从查询的名称服务器返回的答案。DNS 管理员通常使用 `dig` 来诊断 DNS 问题，因为它非常灵活、易用且输出清晰。

### `dig` 命令的基本用法

最简单的 `dig` 命令形式是：

```bash
# dig 域名
dig google.com
```

### `dig` 命令的常用选项和参数

`dig` 命令提供了许多选项，可以影响查询的执行方式和结果的显示。这些选项通常以加号 `+` 开头。

**1. 指定查询的记录类型**

你可以指定要查询的 DNS 记录类型，例如 A (IPv4 地址)，AAAA (IPv6 地址)， MX (邮件交换器)， NS (名称服务器)， CNAME (规范名称，Canonical Name Record)， TXT (文本记录)， PTR (指针记录) 等。

```bash
# dig 域名 记录类型
dig example.com MX # 查询 example.com 的 MX 记录
dig example.com NS # 查询 example.com 的 NS 记录
```

**2. 指定查询的 DNS 服务器**

默认情况下，`dig` 会查询 `/etc/resolv.conf` 文件中列出的 DNS 服务器。你可以使用 `@server` 参数指定要查询的特定 DNS 服务器的 IP 地址或主机名。

```bash
dig 域名 @DNS服务器IP或主机名
```

**示例：**

- 查询 `example.com` 在 Google Public DNS (8.8.8.8) 上的 A 记录：

  ```bash
  dig example.com @8.8.8.8 
  ```

- 查询 `example.com` 在 Cloudflare DNS (1.1.1.1) 上的 NS 记录：

  ```bash
  dig example.com NS @1.1.1.1
  ```

**3. 显示更简洁的输出**

- `+short` ：只显示答案部分，非常适合脚本或快速查看。

  ```bash
  dig example.com +short
  ```

  这将只返回 `example.com` 的 IP 地址。

**4. 跟踪 DNS 解析过程**

- `+trace`：启用跟踪模式，`dig`  会执行迭代查询，从根域名服务器开始，逐步跟踪解析过程，直到找到目标域名的权威名称服务器并显示最终答案。这对于诊断 DNS 委托问题非常有帮助。

  ```
  dig example.com +trace
  ```

  结合 `@server` 使用时，`@server` 只影响对根区名称服务器的初始查询。

**5. 控制显示的信息**

`dig` 提供了很多选项来控制输出的详细程度：

- `+noall`：禁用所有默认显示选项。
- `+answer`：只显示答案部分。
- `+nocomments`：不显示注释。
- `+noauthority`：不显示权威部分。
- `+noadditional`：不显示附加信息部分。
- `+nostats`：不显示统计信息。

**示例：**

- 只显示答案部分，不显示其他信息：

  ```bash
  dig google.com +noall +answer
  ```

**6. 其他常用选项**

- `+vc` 或 `+tcp`：使用 TCP 而不是 UDP 进行查询。在 DNSSEC 或响应过大时可能需要。

- `+time=秒`：设置查询超时时间（秒）。

- `+tries=次数`：设置重试次数。

- `+subnet=IP地址`：模拟来自特定客户端 IP 地址的查询，这对于测试 DNS 智能解析（例如 CDN 调度）很有用。

  ```bash
  dig example.com +subnet=192.168.1.1
  ```

- `-f 文件名`：从文件中读取查询请求，实现批量查询。文件中每行一个查询。

### `dig` 命令的输出结构

`dig` 命令的输出通常包含以下几个部分：

1. **Header (报头)**: 显示 `dig` 命令的版本信息、全局选项以及查询的状态码等。

   ```
   ; <<>> DiG 9.11.x <<>> example.com
   ;; global options: +cmd
   ;; Got answer:
   ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12345
   ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
   ```

   - `status: NOERROR`：表示查询成功。其他可能的状包括 `NXDOMAIN` (域名不存在), `SERVFAIL` (服务器错误) 等。
   - `flags`：显示 DNS 标志，如 `qr` (查询/响应), `rd` (递归查询), `ra` (递归可用) 等。

2. **Question Section (问题部分)**: 显示你发出的查询请求，包括查询的域名、记录类型和类 (通常是 `IN` 表示 Internet)。

   ```
   ;; QUESTION SECTION:
   ;example.com.                   IN      A
   ```

3. **Answer Section (回答部分)**: 这是最重要的部分，显示 DNS 服务器返回的实际答案，即请求的 DNS 记录。

   ```
   ;; ANSWER SECTION:
   example.com.            86400   IN      A       93.184.216.34
   ```

   - `example.com.`：域名
   - `86400`：TTL (Time To Live)，表示这条记录在缓存中可以保留的时间（秒）。
   - `IN`：Internet 类。
   - `A`：记录类型。
   - `93.184.216.34`：记录的值 (例如 IP 地址)。

4. **Authority Section (权威部分)**: 显示负责该域名的权威名称服务器。

   ```
   ;; AUTHORITY SECTION:
   example.com.            86400   IN      NS      a.iana-servers.net.
   example.com.            86400   IN      NS      b.iana-servers.net.
   ```

   - `NS`：名称服务器记录。

5. **Additional Section (附加信息部分)**: 提供一些辅助信息，通常是权威名称服务器的 IP 地址，以便客户端能够联系到它们。

   ```
   ;; ADDITIONAL SECTION:
   a.iana-servers.net.     86400   IN      A       192.0.32.10
   b.iana-servers.net.     86400   IN      A       192.0.47.10
   ```

6. **Stats Section (统计信息部分)**: 显示查询的统计信息，如查询时间、服务器 IP、响应大小等。

   ```
   ;; Query time: 1 msec
   ;; SERVER: 127.0.0.1#53(127.0.0.1)
   ;; WHEN: Thu May 29 21:06:25 2025
   ;; MSG SIZE  rcvd: 123
   ```

### 总结

`dig` 是一个功能强大且灵活的 DNS 查询工具，它能够提供详细的 DNS 解析信息，是网络管理员和开发人员诊断 DNS 相关问题的重要工具。掌握其常用选项和输出结构，可以有效地进行 DNS 故障排除和验证。

## 6. ifconfig

`ifconfig`**（interface configuration）**是一个在 Unix-like 操作系统中用于配置、控制和查询 **网络接口参数**的系统管理工具。它通常在系统启动时用于设置网络接口，也可以在系统运行期间用于调试或调整网络参数。

**请注意：** 在较新的 Linux 发行版中，***`ifconfig` 命令已被 `ip` 命令（`iproute2` 工具集的一部分）所取代***，`ip` 命令功能更强大，能够提供更详细和灵活的网络配置选项。然而，在许多旧系统或一些特定场景下，`ifconfig` 仍然被广泛使用。

### `ifconfig` 命令的基本用途

`ifconfig` 命令的主要用途包括：

1. **显示网络接口信息：** 查看当前系统上所有活动或指定网络接口的配置详情。
2. **配置 IP 地址和子网掩码：** 为网络接口分配 IP 地址和子网掩码。
3. **启用或禁用网络接口：** 激活或关闭网络接口。
4. **设置广播地址：** 为网络接口设置广播地址。
5. **更改 MAC 地址：** 修改网络接口的硬件地址（MAC 地址）。
6. **配置 MTU：** 设置网络接口的最大传输单元。
7. **创建接口别名：** 为一个物理接口配置多个 IP 地址。

### `ifconfig` 命令语法

```
ifconfig [interface] [options | address]
```

- `interface`：指定要操作的网络接口名称，例如 `eth0`、`wlan0`、`lo` 等。
- `options | address`：要执行的操作或要设置的参数。

### `ifconfig` 常用示例及输出解释

#### 1. 显示所有活动网络接口的信息

```
ifconfig
```

**输出示例：**

```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 7a:d6:32:4e:34:0e  txqueuelen 0  (Ethernet)
        RX packets 24175  bytes 35045290 (35.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8556  bytes 583553 (583.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 298769  bytes 199770596 (199.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 298769  bytes 199770596 (199.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

**输出字段解释：**

- **`eth0` / `lo`：** 网络接口的名称。`eth` 通常指以太网接口，`lo` 指环回接口（loopback）。

- `flags`：

   接口状态标志。常见的标志有：

  - `UP`：接口已启用。
  - `BROADCAST`：支持广播。
  - `RUNNING`：接口正在运行。
  - `MULTICAST`：支持组播。
  - `LOOPBACK`：环回接口。

- **`mtu`：** Maximum Transmission Unit (最大传输单元)。表示接口一次能传输的最大数据包大小（字节）。

- **`inet`：** IPv4 地址。

- **`netmask`：** 子网掩码。

- **`broadcast`：** 广播地址。

- **`inet6`：** IPv6 地址。

- **`prefixlen`：** IPv6 地址的 CIDR 前缀长度。

- **`scopeid`：** IPv6 地址的范围ID。

- **`ether`：** 硬件地址，即 MAC 地址。

- **`txqueuelen`：** 传输队列长度。

- **`RX packets` / `TX packets`：** 已接收/已发送的数据包数量。

- **`bytes`：** 已接收/已发送的数据字节数。

- **`errors`：** 接收/发送过程中发生的错误数量。

- **`dropped`：** 因各种原因被丢弃的数据包数量。

- **`overruns`：** 缓冲区溢出导致的数据包丢失数量。

- **`collisions`：** （仅适用于半双工以太网）发生冲突的次数。

#### 2. 显示所有网络接口（包括非活动的）

```bash
ifconfig -a
```

此命令会显示所有网络接口的配置信息，无论它们是否处于活动状态。

#### 3. 显示指定网络接口的信息

```bash
ifconfig eth0
```

只显示 `eth0` 接口的详细信息。

#### 4. 配置 IP 地址、子网掩码和广播地址

```bash
sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 broadcast 192.168.1.255
```

这条命令将 `eth0` 接口的 IP 地址设置为 `192.168.1.10`，子网掩码设置为 `255.255.255.0`，广播地址设置为 `192.168.1.255`。

**注意：** 更改网络接口配置通常需要 root 权限，因此需要使用 `sudo`。这些更改是临时的，系统重启后会失效。要进行永久性更改，需要修改相应的网络配置文件（如 `/etc/network/interfaces` 或 `/etc/sysconfig/network-scripts/ifcfg-eth0` 等，具体取决于 Linux 发行版）。

#### 5. 启用或禁用网络接口

- 启用接口：

  ```bash
  sudo ifconfig eth0 up
  ```

- 禁用接口：

  ```bash
  sudo ifconfig eth0 down
  ```

  禁用接口会阻止系统通过该接口传输或接收消息。

#### 6. 更改 MAC 地址

```bash
sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:11:22:33:44:55
sudo ifconfig eth0 up
```

为了避免潜在问题，通常在更改 MAC 地址之前先禁用接口，更改后再启用。

#### 7. 配置接口别名（Secondary IP Address）

```bash
sudo ifconfig eth0:0 192.168.1.20 netmask 255.255.255.0
```

这会在 `eth0` 接口上创建一个名为 `eth0:0` 的别名接口，并为其分配一个额外的 IP 地址。

#### 8. 设置 MTU

```bash
sudo ifconfig eth0 mtu 1400
```

将 `eth0` 接口的 MTU 设置为 1400 字节。

### `ifconfig` 的局限性与替代方案

如前所述，`ifconfig` 在现代 Linux 系统中逐渐被 `ip` 命令取代，原因如下：

- **功能更强大：** `ip` 命令提供更全面和细粒度的网络配置选项，包括路由、策略路由、隧道、多播等。
- **语法更一致：** `ip` 命令的语法设计更具逻辑性和一致性，例如 `ip addr` 用于地址管理，`ip link` 用于链路层配置，`ip route` 用于路由管理。
- **IPv6 支持更好：** `ip` 命令对 IPv6 的支持更完善。

如果你使用的是较新的 Linux 发行版，建议优先使用 `ip` 命令，例如：

- **显示接口信息：** `ip addr show` 或 `ip a`
- **配置 IP 地址：** `sudo ip addr add 192.168.1.10/24 dev eth0`
- **启用/禁用接口：** `sudo ip link set eth0 up` / `sudo ip link set eth0 down`

尽管 `ifconfig` 仍然可以在许多系统上使用，但了解其局限性并熟悉更现代的 `ip` 命令对于管理 Linux 网络至关重要。

## 7. ip

`ip` 命令是 Linux 系统中一个非常强大和多功能的网络管理工具，它是 `iproute2` 工具包的一部分，旨在取代老旧的 `ifconfig`、`route`、`arp` 等命令。`ip` 命令提供了更统一、更灵活的语法，并且对 IPv6 有更好的支持，同时能够管理更复杂的网络配置，例如网络命名空间、VLAN 和隧道等。

### `ip` 命令的基本语法

```
ip [OPTIONS] OBJECT { COMMAND | help }
```

- **`OPTIONS`**: 全局选项，用于修改 `ip` 命令的行为。
- **`OBJECT`**: `ip` 命令操作的网络对象，通常是其功能的第一个子命令。
- **`COMMAND`**: 对指定 `OBJECT` 执行的操作。
- **`help`**: 显示帮助信息。

### `ip` 命令的主要对象 (OBJECT)

`ip` 命令的核心在于其不同的对象，每个对象都代表网络栈的不同部分。以下是一些最常用的对象：

1. **`link` (或 `l`)**: 配置和显示网络接口（物理或虚拟设备）的状态。
   - 常用命令：
     - `ip link show` 或 `ip a`: 显示所有网络接口的详细信息。
     - `ip link show dev [interface]`：显示指定接口的信息。
     - `ip link set dev [interface] up`: 启用指定接口。
     - `ip link set dev [interface] down`: 禁用指定接口。
     - `ip link set dev [interface] mtu [value]`: 设置接口的 MTU (Maximum Transmission Unit)。
     - `ip link set dev [interface] address [mac_address]`: 修改接口的 MAC 地址。
     - `ip link add link [parent_interface] name [vlan_name] type vlan id [vlan_id]`: 创建 VLAN 接口。
     - `ip link add [device] type bridge`: 创建网桥接口。
2. **`address` (或 `addr` / `a`)**: 管理网络接口上的 IP 地址（IPv4 和 IPv6）。
   - 常用命令：
     - `ip addr show`: 显示所有网络接口的 IP 地址。
     - `ip addr show dev [interface]`: 显示指定接口的 IP 地址。
     - `ip addr add [ip_address/prefix] dev [interface]`: 为指定接口添加 IP 地址。
       - **示例：** `sudo ip addr add 192.168.1.100/24 dev eth0`
     - `ip addr del [ip_address/prefix] dev [interface]`: 从指定接口删除 IP 地址。
       - **示例：** `sudo ip addr del 192.168.1.100/24 dev eth0`
3. **`route` (或 `r`)**: 管理内核路由表。
   - 常用命令：
     - `ip route show`: 显示内核路由表。
     - `ip route show default`: 显示默认路由。
     - `ip route add [destination/prefix] via [gateway_ip] dev [interface]`: 添加一条路由。
       - **示例：** `sudo ip route add 192.168.2.0/24 via 192.168.1.1 dev eth0`
     - `ip route add default via [gateway_ip]`: 添加默认网关。
       - **示例：** `sudo ip route add default via 192.168.1.1`
     - `ip route del [destination/prefix]`: 删除一条路由。
       - **示例：** `sudo ip route del 192.168.2.0/24`
     - `ip route del default`: 删除默认路由。
4. **`neigh` (或 `n`)**: 管理邻居表（ARP 表或 IPv6 NDP 表）。
   - 常用命令：
     - `ip neigh show`: 显示邻居表（ARP 缓存）。
     - `ip neigh add [ip_address] lladdr [mac_address] dev [interface]`: 添加一个静态 ARP 条目。
     - `ip neigh del [ip_address] dev [interface]`: 删除一个 ARP 条目。
5. **`rule`**: 管理路由策略规则。这允许更复杂的路由决策，基于源地址、目标地址、服务类型等。
   - 常用命令：
     - `ip rule show`: 显示路由策略规则。
     - `ip rule add from [source_ip] table [table_id]`: 添加一条路由策略规则。
6. **`maddress` (或 `m`)**: 管理多播地址。
   - 常用命令：
     - `ip maddress show`: 显示多播地址。
     - `ip maddress add [multicast_address] dev [interface]`: 为接口添加多播地址。
7. **`monitor`**: 实时监控网络设备、地址和路由的变化。
   - 常用命令：
     - `ip monitor all`: 监控所有网络对象的变化。

### `ip` 命令与 `ifconfig` 的对比

`ip` 命令被视为 `ifconfig` 的现代化替代品，主要有以下优点：

- **统一的语法**: `ip` 命令采用更一致和分层的语法结构，所有网络配置都通过 `ip` 命令的不同对象来管理，而不是像 `ifconfig`、`route`、`arp` 等分散的命令。
- **IPv6 支持**: `ip` 命令对 IPv6 有完整的支持，而 `ifconfig` 对 IPv6 的支持有限。
- **功能更强大**: `ip` 命令提供了更高级的网络功能，例如网络命名空间、VLAN、隧道、策略路由等，这些是 `ifconfig` 无法实现的。
- **显示所有接口**: `ip link show` 可以显示所有网络接口，包括已启用和已禁用的，而 `ifconfig` 默认只显示启用的接口。
- **活跃维护**: `ip` 命令是 `iproute2` 包的一部分，仍在积极维护和更新，而 **`ifconfig` 所属的 `net-tools` 包已停止维护**。
- **更高效**: `ip` 命令使用 `Netlink sockets` 与内核交互，而 `ifconfig` 使用 `ioctl` 系统调用，`Netlink sockets` 被认为是更现代和灵活的机制。

### 总结

`ip` 命令是 Linux 网络管理的基石，掌握它对于系统管理员和网络工程师至关重要。通过灵活运用 `ip` 命令的不同对象和子命令，可以高效地完成各种网络配置、监控和故障排除任务。虽然 `ifconfig` 在一些老旧系统上可能仍然存在，但强烈建议在现代 Linux 环境中优先使用 `ip` 命令。

# 五、查看系统信息

## 1. lsb_release

`lsb_release` 是一个用于显示 **Linux 发行版相关信息** 的命令行工具。它的名称来源于 **Linux Standard Base (LSB)**，这是一个由 Linux 基金会推动的项目，旨在标准化 Linux 发行版的软件系统结构，以提高不同 Linux 发行版之间的兼容性。

### LSB 的背景和作用

在早期，不同的 Linux 发行版在文件系统布局、系统命令、库等方面存在差异，这给开发和部署跨发行版的应用程序带来了挑战。LSB 的目标就是通过定义一套通用的标准，使得应用程序开发者可以编写一次代码，然后在符合 LSB 标准的不同 Linux 发行版上运行，而无需进行大量的修改。

LSB 规范涵盖了多个方面，包括：

- **标准函数库：** 定义了应用程序可以调用的标准 C 库和其他库。
- **命令和工具：** 扩展了 POSIX 标准，定义了一系列通用的命令和工具。
- **文件系统架构：** 规定了文件系统的布局（例如 `/bin`, `/usr`, `/var` 等目录的用途）。
- **运行级别：** 定义了系统启动和关机时的不同运行级别。
- **打印系统：** 定义了打印相关的接口。
- **X 窗口系统扩展：** 定义了图形界面相关的接口。

尽管 LSB 曾经是一个重要的标准化努力，但随着时间的推移，其重要性有所下降，一些发行版（如 Debian）甚至在 2015 年停止了对其的直接支持。然而，`lsb_release` 命令作为获取发行版信息的一种方式，仍然被广泛使用。

### `lsb_release` 命令的用途

`lsb_release` 命令的主要作用是显示当前 Linux 系统的发行版信息，例如发行版名称、版本号、代号等。这对于系统管理员、开发者或任何需要了解系统详细信息的人来说都非常有用。

### `lsb_release` 的常见用法和参数

不带任何参数执行 `lsb_release` 命令通常会显示简要信息，但为了获取更详细或特定类型的信息，通常会使用以下参数：

``` bash
Usage: lsb_release [options]

Options:
  -a, --all          show all of the above information
  -h, --help         show this help message and exit
  -v, --version      show LSB modules this system supports
  -i, --id           show distributor ID
  -d, --description  show description of this distribution
  -r, --release      show release number of this distribution
  -c, --codename     show code name of this distribution
  -s, --short        show requested information in short format
```

- **`-a`, `--all`：显示所有可用信息。** 这是最常用的参数，会显示发行版 ID、描述、版本号和代号。
- **`-d`, `--description`：显示发行版的描述。**
- **`-i`, `--id`：显示发行版的 ID。**
- **`-r`, `--release`：显示发行版的版本号。**
- **`-c`, `--codename`：显示发行版的代号。**
- **`-s`, `--short`：以短格式显示信息。** 当与其他参数一起使用时，可以只显示值，而不显示描述性的前缀。
- **`-v`, `--version`：显示 LSB 模块的版本号。** 这个参数显示的是 LSB 规范本身的版本，而不是发行版的版本。

## 2.  `/etc/os-release` 

除了 `lsb_release` 命令，Linux 系统上还有其他方式可以获取发行版信息，最常见的是读取 `/etc/os-release` 文件。

- **`lsb_release`：** 这是一个可执行命令，旨在提供符合 LSB 规范的发行版信息。它可能解析 `/etc/lsb-release` 文件（如果存在）或从其他系统信息中获取数据。在某些发行版上，`lsb_release` 是一个 Python 脚本，而另一些则是 shell 脚本。
- **`/etc/os-release`：** 这是一个文本文件，由 systemd 项目引入，现在被广泛认为是获取发行版信息的事实标准。它包含了一系列键值对，提供了更丰富和标准化的发行版信息，如 `NAME`、`VERSION`、`ID`、`VERSION_ID`、`PRETTY_NAME` 等。几乎所有现代 Linux 发行版都包含此文件。

**区别和建议：**

- **标准化程度：** `/etc/os-release` 是一个更现代且更广泛接受的标准，尤其是在使用 systemd 的发行版中。
- **可靠性：** 对于程序性地获取发行版信息，建议优先读取 `/etc/os-release`，因为它是一个静态文件，解析起来更简单，并且在绝大多数发行版上都存在。
- **灵活性：** `lsb_release` 命令提供了便捷的命令行接口来获取特定信息，对于交互式使用或简单的脚本来说仍然很有用。

尽管 LSB 本身已经不再像以前那样活跃，但 `lsb_release` 命令仍然是快速获取 Linux 发行版基本信息的一个方便工具。

## 3. uanme

`uname` 是一个在类 Unix 系统（包括 Linux）中广泛使用的命令行工具，用于显示当前操作系统的名称和其他系统信息。它的名称是 "Unix name" 的缩写。

### `uname` 命令的用途

`uname` 命令的主要作用是获取关于系统内核、硬件架构以及操作系统版本等基本信息。这些信息对于系统管理员进行故障排除、了解系统配置、编写依赖特定系统环境的脚本等都非常有用。

**基本语法：**

```bash
uname [-options]
```

**常用选项：**

- **`-a`, `--all`：显示所有可用信息。** 这是最常用的选项，它会一次性显示内核名称、网络节点主机名、内核发行版本、内核版本、机器硬件名称、处理器类型（如果已知）、硬件平台（如果已知）和操作系统名称。

- `-s`, `--kernel-name`：显示内核名称。

  - 示例：`uname -s`
  - 输出示例：`Linux`

- `-n`, `--nodename`：显示网络节点主机名。

  - 示例：`uname -n`
  - 输出示例：`your_hostname` (你的计算机在网络上的名称)

- `-r`, `--kernel-release`：显示内核发行版本号。

   这是内核的主版本号和次版本号，通常用来识别一个特定的内核版本。

  - 示例：`uname -r`
  - 输出示例：`5.15.0-101-generic`

- `-v`, `--kernel-version`：显示内核版本（构建信息）。

   这通常包括内核的编译日期、时间以及构建者信息。

  - 示例：`uname -v`
  - 输出示例：`#111-Ubuntu SMP Tue Mar 5 20:16:58 UTC 2024`

- `-m`, `--machine`：显示机器硬件名称（架构）。

   这表示系统运行在什么类型的硬件上，例如 x86_64、aarch64 等。

  - 示例：`uname -m`
  - 输出示例：`x86_64`

- `-p`, `--processor`：显示处理器类型。

   （并非所有系统都支持，有时会显示 "unknown" 或与 `-m` 相同的值）

  - 示例：`uname -p`
  - 输出示例：`x86_64`

- `-i`, `--hardware-platform`：显示硬件平台信息。

   （并非所有系统都支持，有时会显示 "unknown" 或与 `-m` 相同的值）

  - 示例：`uname -i`
  - 输出示例：`x86_64`

- `-o`, `--operating-system`：显示操作系统名称。

   在 Linux 系统上通常是 "GNU/Linux"。

  - 示例：`uname -o`
  - 输出示例：`GNU/Linux`

# 六、统计代码行数

## 1. [cloc](https://github.com/AlDanial/cloc?tab=readme-ov-file#quick-start-)

cloc: **Count Lines of Code**, cloc counts **blank lines**, **comment lines**, and **physical lines** of source code in many programming languages.

### 安装

``` shell
npm install -g cloc              # https://www.npmjs.com/package/cloc
sudo apt install cloc            # Debian, Ubuntu
sudo yum install cloc            # Red Hat, Fedora
sudo dnf install cloc            # Fedora 22 or later
sudo pacman -S cloc              # Arch
sudo emerge -av dev-util/cloc    # Gentoo https://packages.gentoo.org/packages/dev-util/cloc
sudo apk add cloc                # Alpine Linux
doas pkg_add cloc                # OpenBSD
sudo pkg install cloc            # FreeBSD
sudo port install cloc           # macOS with MacPorts
brew install cloc                # macOS with Homebrew
choco install cloc               # Windows with Chocolatey
scoop install cloc               # Windows with Scoop
```

### 基本使用

#### (1) 命令行参数

``` bash
cloc [options] <file(s)/dir(s)/git hash(es)> | <set 1> <set 2> | <report files>
```

`options`表示可选的命令行选项，`<file(s)/dir(s)/git hash(es)>` 表示要统计的文件、目录或 Git 提交哈希值，`<set 1> <set 2>` 表示要比较的两个文件集合，表示要生成报告的文件列表。

#### (2) 统计当前目录下的代码行数

``` shell
calc .
```

#### (3) 按文件统计代码行数

``` 
cloc <path> --by-file
```

`path`表示要统计代码行数的目录或文件。如果使用`--by-file`选项，则会按照每个文件统计代码行数。

#### (4) 忽略指定目录

``` shell
cloc <path> --exclude-dir=<dirname>
```

`path`表示要统计代码行数的目录或文件，`dirname`表示要排除的目录名称。

例如，要排除 node_modules 目录，可以输入以下命令：

```bash
cloc . --exclude-dir=node_modules
```

#### (5) 输出指定结果到文件

```bash
cloc . --out=result.txt
```

如果需要输出 csv 格式的结果，可以使用`--csv`参数

```bash
cloc . --csv
```

#### (6) 统计指定语言

``` shell
cloc --include-lang="Language1,Language2,..." <目录或文件>
```

例如，只统计 C/C++ 文件：

``` shell
cloc . --include-lang="C,C++"
```

**注意事项:**

- 语言名称必须与 `cloc` 识别的语言名称完全匹配。你可以运行 `cloc .` 来查看 `cloc` 检测到的所有语言名称。
- 语言名称是大小写敏感的。例如，`XML` 应该写成 `XML` 而不是 `xml`。

# 七、数据传输

## 1. curl

**全称：** Client URL

**定位：** 一个多功能数据传输工具，支持多种协议。

**特点：**

- **多协议支持：** 支持的协议范围非常广泛，包括 HTTP、HTTPS、FTP、FTPS、SCP、SFTP、TFTP、SMB、SMTP、POP3、IMAP 等等。这使得它成为一个非常通用的数据传输工具。
- **灵活性和控制性：** 提供了非常丰富的选项，可以精细控制 HTTP 请求的各个方面，例如设置请求头、处理 cookie、发送 POST 请求、进行用户认证等。这使得它在与 API 交互、调试网络请求等方面非常强大。
- **输出：** 默认将接收到的数据输出到标准输出（终端）。如果需要保存到文件，需要使用 `-o` 或 `-O` 选项。
- **上传功能：** 除了下载，`curl` 也支持向服务器上传数据。
- **可编程性：** `curl` 是基于 `libcurl` 库构建的，`libcurl` 是一个 C 语言库，许多其他编程语言都提供了对 `libcurl` 的绑定，使得开发者可以在自己的程序中集成 `curl` 的功能。

## 2. wget

**全称：** GNU Wget

**定位：** 主要是一个“非交互式网络下载器”（non-interactive network downloader）。

特点：

- **非交互式：** 可以在用户不登录系统的情况下在后台运行，这使得它非常适合自动化脚本和长时间的下载任务。
- **断点续传：** 对网络连接不稳定或中断的情况具有很强的鲁棒性。如果下载中断，它会尝试从上次中断的地方继续下载，而无需从头开始。
- **递归下载和镜像：** 可以自动跟踪HTML页面中的链接，并递归地下载整个网站或部分网站，同时保持原始网站的目录结构。这对于制作网站离线副本或备份非常有用。
- **时间戳：** 可以读取服务器上的时间戳信息，并仅在远程文件比本地文件更新时才进行下载，这有助于保持本地副本的同步。
- **支持协议：** 主要支持 HTTP、HTTPS 和 FTP。
- **输出：** 默认将下载内容保存到本地文件。

## 3. wget 和 curl 的区别

| 特性         | Wget                                 | Curl                                                         |
| ------------ | ------------------------------------ | ------------------------------------------------------------ |
| **主要用途** | 文件下载，网站镜像（递归下载）       | 数据传输，API 交互，调试网络请求                             |
| **交互性**   | 非交互式，可在后台运行               | 交互式，默认输出到终端                                       |
| **协议支持** | HTTP, HTTPS, FTP                     | HTTP, HTTPS, FTP, FTPS, SCP, SFTP, 等多种协议                |
| **默认输出** | 保存到本地文件                       | 输出到标准输出（终端）                                       |
| **递归下载** | 内置支持，非常擅长                   | 不支持，需要手动配置或脚本实现                               |
| **断点续传** | 内置支持，自动重试                   | 支持，但通常需要明确指定选项                                 |
| **上传功能** | 不支持                               | 支持                                                         |
| **复杂请求** | 相对简单，不擅长复杂请求             | 高度可定制，擅长处理复杂请求（如 POST 请求，自定义 headers） |
| **使用场景** | 下载大文件，备份网站，自动化下载脚本 | 测试 API，发送自定义 HTTP 请求，脚本自动化数据传输           |

#### 原理简述

无论是 `wget` 还是 `curl`，它们的工作原理都涉及到网络通信的基本过程，大致可以概括为以下步骤：

1. **解析 URL：** 工具首先解析用户提供的 URL，提取出协议（如 HTTP、FTP）、主机名、端口号（如果未指定则使用默认端口）、路径和文件名等信息。
2. **DNS 解析：** 如果 URL 中包含主机名而不是 IP 地址，工具会进行 DNS 查询，将主机名解析为对应的 IP 地址。
3. **建立连接：**
   - **TCP 连接：** 使用解析到的 IP 地址和端口号，通过 TCP/IP 协议与目标服务器建立一个可靠的连接。
   - **SSL/TLS 握手（如果是 HTTPS/FTPS）：** 如果是加密协议（HTTPS、FTPS），在建立 TCP 连接后，客户端和服务器会进行 SSL/TLS 握手，协商加密算法和交换密钥，建立一个安全的通信通道。
4. **发送请求：**
   - **HTTP/HTTPS：** 根据 URL 和用户指定的选项（如请求方法 GET/POST、请求头、请求体等），构造并发送相应的 HTTP 请求。
   - **FTP：** 对于 FTP 协议，会发送 FTP 命令（如 `USER`、`PASS`、`CWD`、`RETR` 等）来与服务器进行交互。
5. **接收响应：** 服务器接收到请求后，会处理请求并返回相应的响应。
   - **HTTP/HTTPS：** 服务器会返回 HTTP 响应，包含状态码、响应头和响应体（即文件内容或网页内容）。
   - **FTP：** 服务器会返回 FTP 响应码和数据。
6. **处理数据：**
   - **`wget`：** 默认情况下，`wget` 会将接收到的数据直接写入本地文件。如果开启了递归下载功能，它还会解析 HTML/CSS 等文件，提取其中的链接，并重复上述过程下载关联的文件。它还会处理断点续传，记录已下载的字节数，并在需要时从上次中断的位置请求数据。
   - **`curl`：** 默认情况下，`curl` 会将接收到的数据输出到标准输出。用户可以通过 `-o` 选项指定输出文件。`curl` 的强大之处在于它对请求和响应的精细控制，用户可以更灵活地处理数据，例如只获取响应头，或者发送包含自定义数据的 POST 请求。
7. **关闭连接：** 数据传输完成后，客户端会关闭与服务器的连接。

# 二进制分析

## readelf

## nm

## pahoke

## ldd

## lddtree

## objdump

## hexdump





# Modern Linux Command Line

https://www.ruanyifeng.com/blog/2022/01/cli-alternative-tools.html

https://zhuanlan.zhihu.com/p/452374801

https://github.com/ibraheemdev/modern-unix

## 1. bat

`bat` 是 `cat` 命令的替代品，具有一些例如语法高亮、 Git 集成和自动分页等非常酷的特性。

但在使用时要用 `batcat` ？

``` cpp
# dpkg -L bat                                           
/usr
/usr/bin
/usr/bin/batcat
/usr/share
/usr/share/doc
/usr/share/doc/bat
/usr/share/doc/bat/changelog.Debian.gz
/usr/share/doc/bat/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/bat
```

## 2. duf

传统的 Linux 命令 `df` 和 `du` 整合版 —— `duf`。

## 3. htop

在 Linux 操作系统上显示进程运行状态信息最常用工具是我们熟悉的 `top`，它是每位系统管理员的好帮手。

`htop` 可以说是 `top` 的绝佳替代品，它是用 C 写的，是一个跨平台的交互式的进程监控工具，具有更好的视觉效果，一目了然更容易理解当前系统的状况，允许垂直和水平滚动进程列表以查看它们的完整命令行和相关信息，如内存和 CPU 消耗。还显示了系统范围的信息，例如[平均负载](https://zhida.zhihu.com/search?content_id=188657994&content_type=Article&match_order=1&q=平均负载&zhida_source=entity)或交换使用情况。

## 4. glances

Glances 是用 Python 写的一个跨平台的监控工具，旨在通过 curses 或基于 Web 的界面呈现大量系统监控信息，该信息根据用户界面的大小动态调整，是 GNU/Linux、BSD、Mac OS 和 Windows 操作系统的 top/htop 替代品。

## 5. exa

提到 ls 命令，大家都不陌生，在 Linux 环境下，其主要作用：列出当前目录下所包含的文件及子目录，如果当前目录下文件过多，则使用命令 ls 不是很好，因为这输出出来的结果跟你所要查找的文件未能达成一致，第一：需要进行二次过滤查找；第二：文件过多时，终端输出结果较慢；

EXA 是 Unix 和 Linux 操作系统附带的命令行程序的 ls 现代替代品，赋予它更多功能和更好的默认值。它使用颜色来区分文件类型和[元数据](https://zhida.zhihu.com/search?content_id=188657994&content_type=Article&match_order=1&q=元数据&zhida_source=entity)。它了解[符号链接](https://zhida.zhihu.com/search?content_id=188657994&content_type=Article&match_order=1&q=符号链接&zhida_source=entity)、扩展属性和 Git。它体积小、速度快，而且只有一个[二进制文件](https://zhida.zhihu.com/search?content_id=188657994&content_type=Article&match_order=1&q=二进制文件&zhida_source=entity)。

## 6. fd

fd 是一个在文件系统中查找条目的程序，它是 find 命令的一个简单、快速且用户友好的替代品，fd 目的不是取代 find 命令所提供的全部功能，而是在多数用例中提供了合理的默认值，在某些情况下非常有用。

## 7. ag

ack 和 ag 是两个文本搜索工具，比自带的 grep 要好用得多。

## 8. axel

axel 是命令行[多线程](https://zhida.zhihu.com/search?content_id=188657994&content_type=Article&match_order=1&q=多线程&zhida_source=entity)下载工具，下载文件时可以替代 curl、wget。

## 9. pydf

在 Linux 系统下，我们可以使用 df 命令来显示磁盘的相关信息。

pydf 可以说是 df 的替代品，它以更简洁的方式显示磁盘使用状态。

## 10. jq

jq 是一个命令行 JSON 处理器，类似于 sed 或 grep，但专门设计用于处理 JSON 数据。如果你是在日常任务中会用到 JSON 的开发人员或系统管理员，那么这是你工具箱中必不可少的工具。



# Shell Script

[Acwing](https://www.acwing.com/file_system/file/content/whole/index/content/2855883/)

## Linux -- ShellScript编写

### 0x0 站在巨人的肩膀上

> [一个简易的教程](https://juejin.cn/post/6930013333454061575)
>
> [进阶技巧](https://juejin.cn/post/6935365727205457928)
>
> [为什么要在可执行文件前面加 ./](https://mp.weixin.qq.com/s?__biz=MzI2OTA3NTk3Ng==&mid=2649285235&idx=2&sn=3279ca3c81725324d1d607f8b35ed3b1&chksm=f2f99114c58e1802c20535b0cd0c4e186554f3ca8892a995d19af76fdb3e5e0e487812faca68&scene=21#wechat_redirect)   
>
> [shell脚本开头的 #! 是什么](https://cloud.tencent.com/developer/article/1624809)
>
> [使用 mv 替换 rm 防止误删](https://hoxis.github.io/linux-rm-2-mv.html)
>
> [常用 shell 脚本](https://hoxis.github.io/%E5%B8%B8%E7%94%A8%E4%BB%A3%E7%A0%81%E6%AE%B5.html)



### 0x1 小的知识点

```
转义字符：escape character
~/.bashrc ：里面有alias等信息
```

### 0x2 数学运算

```
1.let
操作符和操作数间不能出现空格
不用加$
2.[] / (())
等号左侧不用加$
[]内可以出现空格
3.expr
操作数和操作服必须有空格
等号左侧不需要加$
```

>  [简单的参考](https://blog.csdn.net/google19890102/article/details/51063530)


### 0x3 判断字符串为空出现的 bug

>[-e 和 -n 参数判断结果相矛盾](https://hoxis.github.io/linux-shell-string-is-null.html)


### 0x4 语法

>[遍历数组](https://blog.csdn.net/Lockey23/article/details/74625744)

# 文本三剑客

[grep、sed、awk](https://www.bilibili.com/video/BV1rA4y1S7Hk/?spm_id_from=333.1387.favlist.content.click&vd_source=38033fe3a1f136728a1d6f8acf710b51)

# vim

https://www.acwing.com/file_system/file/content/whole/index/content/2855620/

# tmux

https://www.acwing.com/file_system/file/content/whole/index/content/2855620/

# git

git 基本概念

- 工作区：仓库的目录。工作区是独立于各个分支的。
- 暂存区：数据暂时存放的区域，类似于工作区写入版本库前的缓存区。暂存区是独立于各个分支的。
- 版本库：存放所有已经提交到本地仓库的代码版本
- 版本结构：树结构，树中每个节点代表一个代码版本。

``` bash
git reset HEAD                  如果add了的话，全都取消
git checkout filename           恢复最新版本
git commit --amend              改变提交的commit message 或者 对同一个提交进行代码上的修改
git log -p -2                   最近两次的修改详细记录

git reset test.cpp              如果add了test.cpp，要取消add
git log                         查看提交文件的 logid
git log -p  filename            查看该文件的提交历史， 可以通过关键字
git reset --hard ${logid}                       回滚该logid的提交（已经commit，没有push）f you don't care about keeping the changes you made
git reset --soft ${logid}                       use --soft if you want to keep your changes
git diff --stat --cached origin/master          看commit但没有push的文件
git log --graph                                 图形化显示
git branch -d the_local_branch                  删除对应分支


git brach tmp                                   创建一个branch分支，把当天提交记录都保存起来
git co 当前branch
git lg tmp                                      查看tmp这个分支的日志
git cherry-pick  commitid                       把tmp上某个分支的commit合并到本分支后面
git cm --amend                                  把change id 改了，要不把changeid也考到这个分支上，改分支提交合入的时候就会出现问题
git merge feature-show-create-table-partition   当前分支是feature-show-create-table-partition-info，merge一下feature-show-create-table-partition ，响应的提交也会 merge过来
git merge feature-show-create-table-partition-info --no-ff

git co develop
git branch
git diff develop master
git pull --rebase
git branch feature-split-blacklist
git add fe/src
git rebase --abort
git cm
git branch feature origin/feature               把在本地新建一个feature分支并把远端的分支feature同步下来

// 分支拉的久远了，和develop上差距比较大，先把把本地备份到 tmp分支
git rebase develop                             rebase 本地develop的分支，（我当前的分支是tmp）·

git format-patch -1                            生成对应的patch文件
git am 0001-Add-delete-range-http-and-rpc-interface.patch

git branch -d dev                              删除本地分支
git branch -a                                  显示所有分支
git push origin --delete dev                   删除远端分支

git show ce8c290d23ebaf5e1348ff74df5c61a0d8185856  看这个commitid属于哪个分支
git branch -a --contains 5c64d8be4950b0adc9352de848b1edb915c4ccd4  看远端和本地是否有这个分支


git clone http://github.com/large-repository --depth 1
cd large-repository
git fetch --unshallow
git fetch是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中。
git reset --hard origin/hotfix-leader-balance
git stash
git stash save "save message"                  执行存储时，添加备注，方便查找，只有git stash 也要可以的，但查找时不方便识别
git stash pop                                  恢复
git reset --hard origin/master                 恢复到和远端一致
git show  commit_id  可以看到每个文件具体的改动内容

```



``` bash
git config --global user.name xxx：设置全局用户名，信息记录在~/.gitconfig文件中
git config --global user.email xxx@xxx.com：设置全局邮箱地址，信息记录在~/.gitconfig文件中
git init：将当前目录配置成git仓库，信息记录在隐藏的.git文件夹中
git add XX：将XX文件添加到暂存区
git add .：将所有待加入暂存区的文件加入暂存区
git rm --cached XX：将文件从仓库索引目录中删掉
git commit -m "给自己看的备注信息"：将暂存区的内容提交到当前分支
git status：查看仓库状态
git diff XX：查看XX文件相对于暂存区修改了哪些内容
git log：查看当前分支的所有版本
git reflog：查看HEAD指针的移动历史（包括被回滚的版本）
git reset --hard HEAD^ 或 git reset --hard HEAD~：将代码库回滚到上一个版本
git reset --hard HEAD^^：往上回滚两次，以此类推
git reset --hard HEAD~100：往上回滚100个版本
git reset --hard 版本号：回滚到某一特定版本
git checkout — XX或git restore XX：将XX文件尚未加入暂存区的修改全部撤销
git remote add origin git@git.acwing.com:xxx/XXX.git：将本地仓库关联到远程仓库
git push -u (第一次需要-u以后不需要)：将当前分支推送到远程仓库
git push origin branch_name：将本地的某个分支推送到远程仓库
git clone git@git.acwing.com:xxx/XXX.git：将远程仓库XXX下载到当前目录下
git checkout -b branch_name：创建并切换到branch_name这个分支
git branch：查看所有分支和当前所处分支
git checkout branch_name：切换到branch_name这个分支
git merge branch_name：将分支branch_name合并到当前分支上
git branch -d branch_name：删除本地仓库的branch_name分支
git branch branch_name：创建新分支
git push --set-upstream origin branch_name：设置本地的branch_name分支对应远程仓库的branch_name分支
git push -d origin branch_name：删除远程仓库的branch_name分支
git pull：将远程仓库的当前分支与本地仓库的当前分支合并
git pull origin branch_name：将远程仓库的branch_name分支与本地仓库的当前分支合并
git branch --set-upstream-to=origin/branch_name1 branch_name2：将远程的branch_name1分支与本地的branch_name2分支对应
git checkout -t origin/branch_name 将远程的branch_name分支拉取到本地
git stash：将工作区和暂存区中尚未提交的修改存入栈中
git stash apply：将栈顶存储的修改恢复到当前分支，但不删除栈顶元素
git stash drop：删除栈顶存储的修改
git stash pop：将栈顶存储的修改恢复到当前分支，同时删除栈顶元素
git stash list：查看栈中所有元素
```

# ssh

[Acwing](https://www.acwing.com/file_system/file/content/whole/index/content/2897078/)

# 管道、环境变量

https://www.acwing.com/file_system/file/content/whole/index/content/3030391/



# Command Help Tools

## 1. man

## 2. apropas

> `apropos` 并不是某个词的缩写，而是一个来自拉丁语的词，意思是“关于”或“与……有关”。

`apropos` 是 Linux 和类 Unix 系统中的一个命令，它用于搜索和显示与指定关键字相关的所有手册页（man page）。这个命令非常有用，当你不确定某个命令、函数或工具的具体名称时，可以用它来查找相关的帮助文档。

### 示例：

1. **查找与 `copy` 相关的命令**：

   ```bash
   apropos copy
   ```

   该命令会返回所有与 "copy" 相关的命令或功能的手册页。例如，它可能返回 `cp`（复制文件）和其他包含 "copy" 的命令。

   输出示例：

   ```bash
   bcopy (3)            - copy byte sequence
   copy_file_range (2)  - Copy a range of data from one file to another
   copysign (3)         - copy sign of a number
   copysignf (3)        - copy sign of a number
   copysignl (3)        - copy sign of a number
   cp (1)               - copy files and directories
   dd (1)               - convert and copy a file
   debconf-copydb (1)   - copy a debconf database
   getunwind (2)        - copy the unwind data to caller's buffer
   getutmp (3)          - copy utmp structure to utmpx, and vice versa
   getutmpx (3)         - copy utmp structure to utmpx, and vice versa
   git-checkout-index (1) - Copy files from the index to the working tree
   install (1)          - copy files and set 
   ```

2. **查找与 `network` 相关的命令**：

   ```bash
   apropos network
   ```

   这会列出所有手册中与 "network" 相关的条目。

   输出示例：

   ```bash
   network (7)         - network related manual pages
   networkctl (1)      - Control and inspect the network
   ```

### 额外选项：

- **`-a` 选项**：显示所有匹配项，包括那些包含关键字的命令和描述。

  ```bash
  apropos -a <keyword>
  ```

- **`-r` 选项**：使用正则表达式进行搜索。

  ```bash
  apropos -r <regex>
  ```

### 使用场景：

- **快速查找命令**：如果你知道一个命令的功能，但忘记了它的名称，可以用 `apropos` 搜索相关的关键词来找到它。
- **学习新命令**：当你想了解某个特定领域的命令（例如网络、文件管理等），可以通过 `apropos` 查找所有相关的命令和功能。

## 3. tldr

## 4. cheat

## 5. pinfo

## 6. manpager

## 7. bropages

# 程序性能分析工具

## 1. gprof

> gprof: GNU Profiler
>
> gmon: GMI Monitor
>
> 参考自：
>
> * https://www.cnblogs.com/wlzy/p/7096063.html

大致流程：

1. 使用 `-pg` 参数编译程序，其原理就是在编译程序时，在每个函数的开头加一个 mcount 函数调用，相当于修饰器的作用，用来记录函数的调用时间、调用次数和调用关系等

   ``` bash
   g++ test.cpp -o app -g -pg  
   ```

2. 运行程序，会在当前目录下生成 `gmon.out` 文件

   ``` bash
   ./app
   ```

3. 使用 gprof 查看文件信息：

   * `./app` 是可执行文件，用来告诉 gprof 分析那个程序的性能数据
   * `gmon.out` 是 gprof 默认生成的性能数据文件，它包含了程序的执行信息
   * `-b`：输出精简的信息

   ``` bash
   gprof [-b] ./app gmon.out  
   ```

但是上面只是生成文字信息，看起来不直观，我们可以通过一些工具生成图形数据：

1. 将 gprof 输出的数据输入到 `gprof2dot`，生成 `dot` 各式的调用关系图文件：

   ``` bash
   gprof ./app gmon.out | gprof2dot > ./app.dot
   ```

2. dot 格式并不是真实的图像，它只是一种图形描述语言格式，我们还要根据 dot 格式数据生成图像：

   ``` bash
   dot -Tpng app.dot -o app.png
   ```

## 2. perf

> 参考：
>
> * https://wenfh2020.com/2020/07/30/flame-diagram/

WLS2 因为内核原因无法使用 perf？

## 3. ltract

## 4. strace

## 5. top/htop

## 6. valgrind

## 7. dstat

## 8. iotop

# 其它

``` bash
pwndbg

binwalk

file

dot

systemctl
service
```





``` bash
tar -zxvf                       解压
tar -zcvf  output.tar output/   压缩
tar -cvf  output.tar output/    打包 不压缩
tar -tvf test.tar.gz            预览压缩文件夹内容
ldd                             查看一个 应用需要哪些依赖的动态库
curl url -o obj                 下载该url的文件，类似wget
curl -vk  https                 验证https
vim --version | grep clipboard  看vim是否支持系统剪切板
ls -lht                         看目录下文件大小以K/M/G 单位
ll -tr                          看修改顺序
/usr/libexec/java_home -V       java 路径
nohup cmd &                     在后台运行cmd命令
ssh -i id_rsa root@ip     使用私钥登录目标机器
authorized_keys
file                            查看文件信息
strings                         查看bin文件下的字符串
0 stdin，1 stdout，2 stderr
2>&1                            将标准错误输出到标准输出中tai
nohup myprogram > myprogram.out 2> myprogram.err &              将标准输出到特定的文件，err分开，后台起线程运行
ctrl+A/ctrl+E                   定位到行首行未
ctrl+U/ctrl+K                   删除到行首/行未
ctrl+R                          查找历史命令
ctags --list-languages          看ctags支持哪些语言
find  ./  -name "*.xml"         递归查找一定要加双引号
cal -3 / cal -y                 查看前一个月后一个月日历/显示全年的
su - name                       切换到该用户，同时加载一些列环境配置，例如bash_profile
sudo su                         切root账户
rsync -av src/ 172.18.188.106:/Users/sunxiuyang/tmp/ 172.18.188.106为目标机器ip，copy src下的文件到目标机器tmp下
rsync -av src 172.18.188.106:/Users/sunxiuyang/tmp/  把src这个目录copy过去
for i in `cat gzns01_all`; do ssh -o StrictHostKeyChecking=no $i "cd /root && sh name_env_setup.sh"; done      root 已经是相互信任的
ln -s jdk-8u161 jdk             软链
ll | grep taf                   查看文件
sort -k3 -n filename            按照（k3）第三个列 的数字(-n) 从小到大排序
for i in `cat ip.list`;do host $i;done > tmp    按行读取ip.list文件, 并执行 host操作
for i in `cat gzns01_all`; do scp -o no StrictHostKeyChecking `pwd`/home_env_setup.sh $i:/root/; done
for i in `cat gzns01_all`; do ssh -o StrictHostKeyChecking=no $i "cd /root && sh home_env_setup.sh"; done
dig www.baidu.com               dig命令可以执行查询域名相关的任务
crontab
rm node.log.* node.log.wf.* -f &    起一个进程删掉
pstack pid                      打印出pid进程下所有的线程栈信息
jstack -l pid                   打印java进程的堆栈信息
for i in `echo -e "name1\n name2\n name3"`; do echo $i" "$RANDOM; done > ./tmp; cat ./tmp | sort -nk2        随机排序名字
cat /proc/version
cat /etc/issue
ll /proc/340/fg | grep socket | wc -l       查看fd数量
uptime                          看机器启动时间
/etc/security/limits.conf       把core文件打开
ulimit -c                       看core文件是否打开
ulimit -c unlimited             不设置core文件大小
/var/log/messages               看系统日志
ls -l /proc/15430/fd/ | wc -l   查看这个进程打开的文件描述符的个数
cat /proc/sys/fs/file-max       查看系统可打开的最大描述符
lsof -p 24405                   看这个进程打开的fd
netstat -antp | grep 24405      看该进程的链接的情况
/var/log/message                系统启动后的信息和错误日志，是Red Hat Linux中最常用的日志之一
sysctl -a | grep keepalive      看系统内核是不是那tcp得探活关了
top -Hp 32554                   查看32554进程的线程情况
lsblk -d -o name,rota           查看磁盘是否是ssd 或者 HDD， 如果ROTA：0 就是ssd
curl http://test.com:8302/metrics -o tmp 把这个url的内容输出到文本里
export TMOUT=0                  不超时

asan/pmap                       看内存泄漏
sed                             正则，各种替换
fdisk -l                        切换root 账号 看机器链接的磁盘数量
ls /dev                         看机器设备，看有多少块盘
useradd name                   机器添加 name 用户
passwd name                    给name 用户添加密码
cat /dev/null > fe.log          清空文件
awk -v RS='' -v ORS='\n\n' '/搜索的词/' 文件名字     搜出关键词所在的段落
```

