我们为什么要学习操作系统，它和一般的裸机系统有什么区别？

## 裸机系统

在我们一开始学习单片机的时候，写的程序都是在一个大循环中不停地运行，基本的代码形式如下：

```c
void main(void) {
    // 初始化代码，只执行一次
	
    // 主体代码，循环执行
    while (1) {

    }
}

// 中断服务函数
void isr1(void) {
    
}

// 中断服务函数
void isr2(void) {
    
}
```

程序开始运行时，首先会执行单片机的初始化代码，之后会在主体代码里循环执行，这样的系统被称为 **轮询系统**。当单片机只执行一些非常简单的任务时，例如一个 LED 闪灯，LCD 的显示等任务时，效果会很不错。

但是当我们需要处理一些外部事件时，例如按键的按下，整个系统的实时性就不会那么好了。当按键按下时，可能需要经过一段时间程序才会运行至按键的判断代码，但这个时候按键可能已经松开了，就会造成事件的丢失。

为了提高系统对外部事件的实时响应性，我们引入了 **中断**，当指定的外部事件产生时，程序会立即跳至对应的中断服务函数中运行，处理完事件后返回中断的位置继续运行，这样的系统被称为 **前后台系统**。其中中断服务函数称为前台，主循环代码称为后台。

引入前后台系统后，整个系统对外部事件的响应速度（实时性）得到了提高，在大多数项目中，前后台系统运用得好，可以达到跟操作系统媲美的效果。

## 实时操作系统

**实时操作系统**，一般简写成 **RTOS (Realtime Operating System)**。一般使用 RTOS 的程序代码结构如下：

```c
int main(void) {
    // 硬件初始化
    hardware_init();
    
    // RTOS 初始化
    rtos_init();
    
    // 初始化各个任务
    task1_init();
    task2_init();
    
    // 开启任务调度
    scheduler_start();
}

void task1(void *parameter) {
    // 任务 1 相关初始化代码
    
    // 循环执行
    while (1) {
        
    }
}

void task2(void *parameter) {
    // 任务 2 相关初始化代码
    
    // 循环执行
    while (1) {
        
    }
}

// 中断服务函数
void isr1(void) {
    
}

// 中断服务函数
void isr2(void) {
    
}
```

可见，当我们引入 RTOS 后，程序的代码被拆分成了多个独立的小模块，每个任务的执行由操作系统去进行调度，我们不再需要精心设计代码执行的顺序，编程难度也随之降低。

**同一时间，单核 CPU 只能运行一个程序。**在使用裸机系统的时候，程序中最浪费 CPU 的就是 **延时代码**；使用操作系统后，我们需要使用操作系统提供的延时函数，当任务运行至延时函数（任务被置为 **挂起状态**）时，操作系统会让 CPU 执行其他处于就绪状态的任务，延时结束后，会继续运行之前的任务。这样，每个任务会被交替执行，看起来 **好像是多任务同时运行** 一样，这种在同一时间段内运行多个任务的形式我们成为 **并发运行**[^1]。这种方式大大提高了 CPU 的使用效率（减少了延时等无用代码的执行）。

### 一些 RTOS 的介绍

- [FreeRTOS](https://www.freertos.org/index.html)：老牌 RTOS，被广泛运行于各类 MCU 上，开放源代码，采用 MIT 许可证[^2]许可。
- [RT-Thread](https://www.rt-thread.org/)：国产物联网 RTOS，中文文档资料丰富，提供了软件包生态，同样开源，采用 Apache-2.0 许可证[^3]许可。
- [μC/OS](https://www.micrium.com/rtos/kernels/)：历史悠久，已被广泛移植，国内教学大多采用此操作系统，开源，采用 Apache-2.0 许可证[^3]许可。
- [Zephyr](https://zephyrproject.org/)：一款物联网操作系统，但是在国内没怎么看到它的身影，采用 Apache-2.0 许可证[^3]许可。

## FAQ

-   说到操作系统，怎么不讲讲 Linux？

    Linux 的运行依赖于 MMU（内存管理单元）[^4]，然而 Cortex-M 架构的 CPU 是没有 MMU 的。虽然说有 no-MMU[^5] 的版本，但是 Linux 实在是过于复杂，一开始我们选择较为简单的 RTOS 上手。

-   怎样学习 RTOS？

    最好的办法就是 **自己写一个**！不要畏惧，当你从零开始编写一个 RTOS 的内核后，你会对它的工作原理了如指掌。推荐阅读野火的教程[^6]。

## 参考链接及资料

[^1]: [并发运行_百度百科 (baidu.com)](https://baike.baidu.com/item/并发运行)
[^2]: [The MIT License | Open Source Initiative](https://opensource.org/licenses/MIT)
[^3]: [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
[^4]: [MMU_百度百科 (baidu.com)](https://baike.baidu.com/item/MMU)
[^5]: [No-MMU memory mapping support (Linux Kernel Documentation)](https://www.kernel.org/doc/Documentation/nommu-mmap.txt)
[^6]: [[野火\]《FreeRTOS内核实现与应用开发实战指南》系列 — 野火产品资料下载中心 文档 (embedfire.com)](http://doc.embedfire.com/products/link/zh/latest/tutorial/ebf_freertos_tutorial.html)

