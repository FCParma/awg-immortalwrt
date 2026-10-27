# AmneziaWG для прошивок ImmortalWrt (Ядро 6.12.103 и другие)

Этот репозиторий создан для автоматической сборки ядерного модуля AmneziaWG (`kmod-amneziawg`) под систему **ImmortalWrt**. В отличие от чистой OpenWrt, здесь используются оригинальные SDK ImmortalWrt, что решает проблему несовместимости версий и хэшей ядра (ошибка `breaks kernel` при установке).

---

## 🚀 Вариант 1: Быстрая установка для Xiaomi Mi Router 3G (и аналогов)
Если у вас **ImmortalWrt 25.12.2** с процессором **MediaTek MT7621 (ramips)** и ядром **6.12.103**, вам ничего собирать не нужно. Пакеты уже лежат в разделе **Releases**.

Просто зайдите по SSH на роутер, скопируйте команду ниже, вставьте в консоль роутера и нажмите **Enter**:

```bash
cd /tmp && wget https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/kmod-amneziawg_v25.12.2_mipsel_24kc_ramips_mt7621.apk && wget https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/amneziawg-tools_v25.12.2_mipsel_24kc_ramips_mt7621.apk && wget https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/luci-proto-amneziawg_v25.12.2_all.apk && wget https://github.com/FCParma/awg-immortalwrt/releases/download/v25.12.2/luci-i18n-amneziawg-ru_v25.12.2_all.apk && apk add --allow-untrusted *amneziawg*.apk
```

---

## 🛠 Вариант 2: Сборка под ваш роутер и вашу версию ядра (Для других моделей)
Если у вас другая версия прошивки или другой процессор, вы можете бесплатно собрать пакет прямо на серверах GitHub за 5 минут:

1. Сделайте **Fork** (копию) этого репозитория к себе в аккаунт.
2. Перейдите на вкладку **Actions** сверху и нажмите зеленую кнопку активации (если попросит).
3. В левой колонке выберите сценарий **Build ImmortalWrt Packages**.
4. Справа нажмите серое меню **Run workflow** и заполните поля данными вашего устройства:
   * **Версия ImmortalWrt:** введите версию вашей прошивки (например: `25.12.2`).
   * **Платформа процессора:** архитектура вашего чипа (например: `ramips`, `mediatek`, `ipq40xx`). Её можно подсмотреть в меню роутера или файле прошивки.
   * **Подплатформа/чипсет:** конкретная модель чипа (например: `mt7621`).
5. Нажмите зеленую кнопку **Run workflow**. 
6. Через 7-10 минут желтый кружок сменится зеленой галочкой. Зайдите внутрь задачи, прокрутите вниз и в блоке **Artifacts** скачайте ваш архив с готовыми пакетами под ваше ядро.
