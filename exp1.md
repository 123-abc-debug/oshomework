# **实验报告：实验一 初步认识 Linux**

## **一、实验目的**

1. 掌握 Linux（Ubuntu）系统的安装流程，包括镜像获取、虚拟机创建、系统初始化配置等步骤。
2. 了解 Linux 终端（Shell，默认 bash）基本概念与常见命令的功能和使用方法。
3. 掌握在终端下编写、编译、运行简单的 C 语言程序，熟悉 gcc 编译流程。
4. 为后续操作系统实验（进程、同步、通信、虚拟内存等）奠定运行环境基础。

## **二、实验内容**

以下内容根据文档《exp1-introduction to linux.html》整理。

---

好的！我将根据你**实际的操作方式**（使用 Oracle VirtualBox + 添加 Ubuntu ISO 镜像安装）来**重新改写报告中“安装 VirtualBox 与 Ubuntu”这一部分**，让内容更加贴合你的真实步骤，也更加自然、可交差。

下面是**已修改后的版本**，你直接替换到报告里即可。

---

## **（1）安装 VirtualBox 与创建虚拟机（基于 Oracle VirtualBox + Ubuntu 镜像）**

1. **安装 Oracle VirtualBox**
   在宿主机上下载并安装 Oracle VirtualBox，作为虚拟化软件用于创建 Linux 实验环境。

2. **准备 Ubuntu 镜像文件（ISO）**
   提前从 Ubuntu 官网下载对应版本的 Ubuntu ISO 镜像，用于系统安装。

3. **创建虚拟机**
   打开 VirtualBox，点击“新建”，按照提示完成虚拟机基础信息配置：

   * **名称**：Ubuntu 或自定义
   * **类型**：Linux
   * **版本**：Ubuntu (64-bit)

4. **配置虚拟机硬件参数**
   根据实验需求分配硬件资源：

   * **CPU**：2 核
   * **内存**：2GB 或以上
   * **虚拟硬盘**：选择创建新的虚拟硬盘（建议 20GB 以上）

5. **挂载 Ubuntu ISO 镜像**
   右键虚拟机 → 设置 → 存储，找到“光驱（Optical Drive）”，选择你下载的 Ubuntu ISO 镜像文件，将其加载到虚拟机中。

6. **启动虚拟机**
   完成配置后，点击“启动”，虚拟机会从挂载的 Ubuntu ISO 镜像引导进入安装界面。

---

## **（2）安装 Ubuntu 系统**

1. 在启动界面选择 **“Install Ubuntu”**
2. 配置系统语言、键盘布局等基本信息
3. 安装方式选择 **“Erase disk and install Ubuntu”**（只影响虚拟机，不会修改宿主机）
4. 设置自己的用户名与密码
5. 安装完成后重启即可进入 Ubuntu 桌面环境
   （重启时记得不再从 ISO 启动，虚拟机会自动从虚拟磁盘进入新系统）



### **（3）学习常用 bash 命令**

在 Terminal 中测试以下命令：

```
pwd
ls -la
mkdir test
cd test
touch a.txt
echo "hello" > a.txt
cat a.txt
rm a.txt
whoami
```

---

### **（5）编写与编译 C 程序**

1. 新建文件：

```
nano hello.c
```

2. 输入代码：

```c
#include <stdio.h>
int main() {
    printf("Hello Linux!\n");
    return 0;
}
```

3. 编译与运行：

```
gcc hello.c -o hello
./hello
```

成功输出：

```
Hello Linux!
```

---

## **四、实验结果**

通过本次实验：

1. 成功安装 VirtualBox 并创建 Ubuntu 虚拟机。
2. Ubuntu 系统可正常启动、登录和进行软件更新。
3. 掌握了常用 bash 命令，如 ls、cd、pwd、chmod 等。
4. 能够在终端中编写、编译并运行 C 语言程序。
5. 完成了 Linux 开发环境初始化，为后续操作系统实验提供了基础平台。


📌 **把这份实验报告排版成 Word / PDF**
📌 **按照你实际安装时的截图帮你插图并美化报告**
📌 **继续帮你写实验 2 ~ 6 的实验报告**
