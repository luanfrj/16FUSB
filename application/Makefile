# Compiler command. Make sure it's in your PATH
AS := gpasm

# Linker command. Make sure it's in your PATH
LD := gplink

#16FUSB core location
16FUSB := ../16fusb

# CPU version
CPUTYPE := 16f628a


16FUSB.hex : func.o isr.o usb.o stdreq.o out.o main.o setup.o
	$(LD) "$(16FUSB)/func.o" "$(16FUSB)/isr.o" "$(16FUSB)/usb.o" "$(16FUSB)/stdreq.o" "out.o" "main.o" "setup.o" -o 16FUSB.hex

func.o : $(16FUSB)/func.asm def.inc $(16FUSB)/def.inc 
	$(AS) -c -p$(CPUTYPE) "$(16FUSB)/func.asm"

isr.o : $(16FUSB)/isr.asm def.inc $(16FUSB)/def.inc 
	$(AS) -c -p$(CPUTYPE) "$(16FUSB)/isr.asm"

usb.o : $(16FUSB)/usb.asm def.inc $(16FUSB)/def.inc 
	$(AS) -c -p$(CPUTYPE) "$(16FUSB)/usb.asm" 

stdreq.o : $(16FUSB)/stdreq.asm def.inc $(16FUSB)/def.inc 
	$(AS) -c -p$(CPUTYPE) "$(16FUSB)/stdreq.asm"

out.o : out.asm def.inc $(16FUSB)/def.inc 
	$(AS) -c -p$(CPUTYPE) "out.asm"

main.o : main.asm def.inc $(16FUSB)/def.inc 
	$(AS) -c -p$(CPUTYPE) "main.asm"

setup.o : setup.asm def.inc rpt_desc.inc $(16FUSB)/def.inc
	$(AS) -c -p$(CPUTYPE) "setup.asm"

clean :
	rm -f $(16FUSB)/*.o $(16FUSB)/*.lst *.o *.lst *.cod *.mcp *.hex