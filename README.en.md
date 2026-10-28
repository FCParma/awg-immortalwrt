# AmneziaWG for ImmortalWrt firmware (Kernel 6.12.103 and others)

This repository was created for automatic assembly of the AmneziaWG kernel module (`kmod-amneziawg`) for the **ImmortalWrt** system. Unlike pure OpenWrt, the original ImmortalWrt SDK is used here, which solves the problem of incompatibility of kernel versions and hashes (`breaks kernel` error during installation).

---

## 🚀 Option 1: Quick installation for Xiaomi Mi Router 3G (and analogues)
If you have **ImmortalWrt 25.12.2** with a **MediaTek MT7621 (ramips)** processor and **6.12.103** kernel, you don't need to build anything. The packages are already in the **Releases** section.

Just log into your router via SSH, copy the command below, paste it into the router console and press **Enter**:

```bash
cd /tmp && \
wget -O kmod-amneziawg.apk https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/kmod-amneziawg_v25.12.2_mipsel_24kc_ramips_mt7621.apk && \
wget -O amneziawg-tools.apk https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/amneziawg-tools_v25.12.2_mipsel_24kc_ramips_mt7621.apk && \
wget -O luci-proto-amneziawg.apk https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/luci-proto-amneziawg_v25.12.2_mipsel_24kc_ramips_mt7621.apk && \
wget -O luci-i18n-amneziawg-ru.apk https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/luci-i18n-amneziawg-ru_v25.12.2_mipsel_24kc_ramips_mt7621.apk && \
apk add --allow-untrusted kmod-amneziawg.apk amneziawg-tools.apk luci-proto-amneziawg.apk luci-i18n-amneziawg-ru.apk
```

---

## 🛠 Option 2: Build for your router and your kernel version (for other models)
If you have a different firmware version or a different processor, you can build the package for free directly on GitHub servers in a few minutes:

1. Make a **Fork** (copy) of this repository to your account.
2. Go to the **Actions** tab at the top and click the green activation button (if prompted).
3. In the left column, select the **Build ImmortalWrt Packages** script.
4. On the right, click the green **Run workflow** button and fill in the fields with your device data:
   * **ImmortalWrt Version:** Enter your firmware version (for example: `25.12.2`).
   * **CPU platform:** your chip architecture (for example: `ramips`, `mediatek`, `ipq40xx`). You can see it in the router menu or firmware file.
   * **Subplatform/chipset:** specific chip model (for example: `mt7621`).
5. Click the green **Run workflow** button. 
6. After 7-10 minutes, the yellow circle will be replaced by a green tick. Go to **Releases** and pick up ready-made packages for your kernel.

