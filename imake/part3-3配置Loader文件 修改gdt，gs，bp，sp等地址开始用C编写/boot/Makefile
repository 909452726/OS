# Makefile for boot

# Programs, flags, etc.
ASM		= nasm
ASMFLAGS	= -I include/

# This Program
TARGET		= boot.bin loader.bin

# All Phony Targets
.PHONY : everything clean all

# Default starting position
everything : $(TARGET)

clean :
#rm -f boot.bin loader.bin
	rm -f $(TARGET)

all : clean everything

#1. 要想得到loader.bin，需要执行“$(ASM) $(ASMFLAGS) -o $@ $<”。
#2. loader.bin依赖于以下文件： 
#	loader.asm 
#	include/load.inc 
#	include/pm.inc 
#	include／fat12hdr.inc
#	$@ 代表boot.bin  $< 代表 boot.asm（boot.asm include/load.inc include/fat12hdr.inc 的第一个名字）

boot.bin : boot.asm include/load.inc include/fat12hdr.inc
	$(ASM) $(ASMFLAGS) -o $@ $<

loader.bin : loader.asm include/load.inc include/fat12hdr.inc include/pm.inc
	$(ASM) $(ASMFLAGS) -o $@ $<

