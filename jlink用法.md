
# 命令
setWP 0x20004f58 W S32 0xDEADBEEF 0 0 //条件断点:当变量0x20004f58变为0xDEADBEEF时触发
  usb--------连接目标板
  r----------重启目标板
  halt-------停止cpu运行的程序
  loadbin----加载可执行的二进制文件
  g----------跳到代码段地址执行
  s----------单步执行（调试用）
  setpc-----设置pc寄存器的值（调试用）
  setbp-----设置断点
  Regs-------读寄存器组织，该命令会把所有的寄存器显示出来
  wreg-------写寄存器
  mem--------读内存
  w4---------写内存
  power off mmu---关闭mmu，这个对于裸板调试很重要
  w4 cpsr,0x0000001f------切换到系统模式
  speed------设置jtag的传输速率
  rce 0,c0,c0,0-----设置cp15寄存器的第1个寄存器为0
  exec setsn=59768901 //修改SN: 6.14可用  
# 使用步骤
1. 打开jlink
2. J-Link>usb
3. J-Link>connect
4. Device>?     选择芯片
   TIF>s
   Speed>4000
   J-Link>h     //暂停
   J-Link>go    //继续运行
   J-Link>mem32 0x20000000,1    //读取0x20000000的ram
   J-Link>w4 0x20000000,123     //写0x123到0x20000000
   J-Link>rreg "r15 (pc)" //读取PC值,会halt cpu
