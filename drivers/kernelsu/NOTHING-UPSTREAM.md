# Pinned replacement CI KernelSU input

Repository: https://github.com/manipvlator/KernelSU
Branch inspected: main
Revision: `acd94e233100d388f98baef6e4cf5c64ee9ea71a`

The replacement beta1 workflow fetches this fork separately; the kernel checkout
itself had KSU config declarations but no driver or Kconfig/Makefile integration.
This commit vendors the fork's kernel subtree and adds only the normal driver
wiring, without executing its setup script or the maintainer's CI workflow.
The downloaded setup.sh is not included here. Other imported files, including
the upstream embedded preinit-runner source header, are unchanged source inputs;
no locally built executable, object, kernel Image or private signing key is added.
Original notices, LICENSE and upstream authorship remain attributable to the fork.

Source-advertised versions: official KernelSU v3.3.1 / 32731; KernelSU-Next
v3.4.2 / 33390; BakaSU v4.2.0 / 35206; OriginSU v4.3.0 / 35499; FinaSU
v1.6.0 / 33181. UAPI: **6**. Existing base SUSFS hooks/config are retained.
Public APK identity checks are upstream behavior, not a module-signing identity
assertion. No manager APK, root grant, daemon or module compatibility is certified.

V2's tested manager v3.3.0-spoofed / 33214 worked with its different UAPI-2
integration only. **The replacement base and this integration are UNBOOTED.**
NoMount, CI OEM panel changes and bundled DTB/DTBO are intentionally not imported;
systemless-module behavior may differ from the maintainer CI variant and is untested.
