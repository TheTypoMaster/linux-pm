#
# Makefile for the linux kernel.
#

# Common objects
obj-y				:= timer.o console.o

# CPU objects
obj-$(CONFIG_ARCH_SH73A0)	+= setup-sh73a0.o pm-sh73a0.o
obj-$(CONFIG_ARCH_R8A73A4)	+= setup-r8a73a4.o
obj-$(CONFIG_ARCH_R8A7740)	+= setup-r8a7740.o pm-r8a7740.o
obj-$(CONFIG_ARCH_R8A7778)	+= setup-r8a7778.o
obj-$(CONFIG_ARCH_R8A7779)	+= setup-r8a7779.o pm-r8a7779.o
obj-$(CONFIG_ARCH_R8A7790)	+= setup-r8a7790.o
obj-$(CONFIG_ARCH_R8A7791)	+= setup-r8a7791.o
obj-$(CONFIG_ARCH_R8A7794)	+= setup-r8a7794.o
obj-$(CONFIG_ARCH_EMEV2)	+= setup-emev2.o
obj-$(CONFIG_ARCH_R7S72100)	+= setup-r7s72100.o

# Clock objects
ifndef CONFIG_COMMON_CLK
obj-y				+= clock.o
obj-$(CONFIG_ARCH_SH73A0)	+= clock-sh73a0.o
obj-$(CONFIG_ARCH_R8A7740)	+= clock-r8a7740.o
obj-$(CONFIG_ARCH_R8A7778)	+= clock-r8a7778.o
obj-$(CONFIG_ARCH_R8A7779)	+= clock-r8a7779.o
endif

# CPU reset vector handling objects
cpu-y				:= platsmp.o headsmp.o

# Shared SoC family objects
obj-$(CONFIG_ARCH_RCAR_GEN2)	+= setup-rcar-gen2.o platsmp-apmu.o $(cpu-y)
CFLAGS_setup-rcar-gen2.o	+= -march=armv7-a
obj-$(CONFIG_ARCH_R8A7790)	+= regulator-quirk-rcar-gen2.o
obj-$(CONFIG_ARCH_R8A7791)	+= regulator-quirk-rcar-gen2.o

# SMP objects
smp-y				:= $(cpu-y)
smp-$(CONFIG_ARCH_SH73A0)	+= smp-sh73a0.o headsmp-scu.o platsmp-scu.o
smp-$(CONFIG_ARCH_R8A7779)	+= smp-r8a7779.o headsmp-scu.o platsmp-scu.o
smp-$(CONFIG_ARCH_R8A7790)	+= smp-r8a7790.o
smp-$(CONFIG_ARCH_R8A7791)	+= smp-r8a7791.o
smp-$(CONFIG_ARCH_EMEV2)	+= smp-emev2.o headsmp-scu.o platsmp-scu.o

# PM objects
obj-$(CONFIG_SUSPEND)		+= suspend.o
obj-$(CONFIG_CPU_FREQ)		+= cpufreq.o
obj-$(CONFIG_PM_RCAR)		+= pm-rcar.o
obj-$(CONFIG_PM_RMOBILE)	+= pm-rmobile.o
obj-$(CONFIG_ARCH_RCAR_GEN2)	+= pm-rcar-gen2.o
obj-$(CONFIG_SHMOBILE_MCPM)	+= mcpm-shmobile.o

# Board objects
ifdef CONFIG_ARCH_SHMOBILE_MULTI
obj-$(CONFIG_MACH_MARZEN)	+= board-marzen-reference.o
else
obj-$(CONFIG_MACH_BOCKW)	+= board-bockw.o
obj-$(CONFIG_MACH_BOCKW_REFERENCE)	+= board-bockw-reference.o
obj-$(CONFIG_MACH_MARZEN)	+= board-marzen.o
obj-$(CONFIG_MACH_ARMADILLO800EVA)	+= board-armadillo800eva.o
obj-$(CONFIG_MACH_KZM9G)	+= board-kzm9g.o intc-sh73a0.o
endif

# Framework support
obj-$(CONFIG_SMP)		+= $(smp-y)
