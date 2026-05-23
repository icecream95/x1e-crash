# x1e-crash

A program to cause Snapdragon X Elite SoCs to hang and then reset.

**Warning:** May cause filesystem corruption, especially with files
that are currently being edited, though doing a sync beforehand makes
this less likely.

## Usage

```
gcc -O2 crash.c -o crash && sync && ./crash
```

## Notes

A mitigation is to remove `SCTLR_EL1_DZE` from `INIT_SCTLR_EL1_MMU_ON`
in `arch/arm64/include/asm/sysreg.h`, in the Linux kernel source code,
in order to disable the `DC ZVA` instruction.

Windows uses a different mitigation, which is currently unknown.
