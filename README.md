# Nothing sweet2 v3 — UNBOOTED-TEST

**This replacement base has never been booted on the intended phone. V2 booted
successfully and remains the fallback. All v3 ROM, root, manager, module and
performance behavior is untested. This is not a stable release.**

Intended target: Redmi Note 12 Pro 4G, exact model **2209116AG** (sweet2/sweet_k6a).
The replacement source only identifies shared sweet support, described upstream
as Redmi Note 10 Pro. No explicit sweet2 DT commit or target handling was found;
an exact-model installer gate is not proof of kernel compatibility.

## Base and credits

Based on [memedooooo/los_kernel_xiaomi_sm6150](https://github.com/memedooooo/los_kernel_xiaomi_sm6150),
branch `beta1`, at `a5cf6de24e3f579b3c07d393c4666edcbe051795`, supplied as the
replacement by MiDoNaSR545. Credit belongs to the original Linux/OpenELA,
Qualcomm, Xiaomi, Android, KernelSU/SUSFS, BORE and other upstream contributors.
Original history, authorship and source licenses are retained. See `COPYING`
and the original Linux `README`.

The actual defconfig is `arch/arm64/configs/vendor/sweet_defconfig`.
The local build retains O2, generic arm64 ISA, ThinLTO and no outlined atomics;
it uses existing Android Clang/LLD 14.0.6 r450784d, not the maintainer CI's declared
Neutron Clang 24.0.0/greenforce GCC combination. Resolved config, flags, symbols
and build provenance belong with the host-verified release, not a boot claim.

Ports are separate commits with their original v2 IDs. Applicable defaults cover
performance, short input boost, swappiness 100, deadline/mq-deadline, and BBR/fq.
LZ4 primary zram and no DWARF are already in beta1. Scheduler/debug/stats, IPC,
GPIO and tracing/BPF interfaces are retained/restored. The KGSL reference fix is
ported separately; the thermal notifier correction is already in beta1.
The old raised OSM minima and later-reversed diagnostic-removal commits are not
ported. Stock minima remain writable; no min=max pin is added.

## Root and manager scope

The beta1 checkout declares KSU options but contains no integrated driver. Its
CI fetches `manipvlator/KernelSU main` separately. A manual pinned import, when
included, records its revision and source-advertised version in
`drivers/kernelsu/NOTHING-UPSTREAM.md`; no downloaded setup script is executed.
NoMount, CI panel edits and CI bundled DTB/DTBO are not added here.

**KSU-Next Manager v3.3.0-spoofed / 33214 worked with v2 only.** V2's integration
advertised 35035/v4.1.0, UAPI 2. The inspected replacement CI fork advertises
official v3.3.1/32731 and UAPI 6, with additional per-manager version identifiers.
No manager/daemon/API compatibility, root grant or module behavior is verified
for v3. Do not infer compatibility or a required manager upgrade from version labels.

No SELinux/AVB/dm-verity configuration or hardware-critical thermal trips are
changed by these ports; inherited KernelSU/SUSFS behavior is not reworked.
No overclock, GPU tuning, pstore/observer, thermal bypass or F2FS safeguard
weakening is included. Actual CPU OPP reachability and Franco-write persistence
remain runtime questions under the owner's no-device-testing override.
