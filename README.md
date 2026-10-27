

  1. Primary Location:
  👉 **`/home/dc/Jio_ODU_ESim_Architecture_Study_Guide.md`**
  2. Project Folder Copy:
  👉 **`/home/dc/Downloads/J Filed/Jio_ODU_ESim_Architecture_Study_Guide.md`**
  ──────
  ### 📑 Ee Study Guide-il Ulladakkam (Table of Contents):
  1. Executive Overview & Ecosystem Triad:
      • Physical Outdoor Unit hardware (JODU52240), Firmware (52240-21.img), and Mobile Client apps thammilulla core
      relationship.
      • Installation environment and the need for a hybrid wireless bootstrap (BLE discovery + local HTTPS data
      flow).
  2. Comparative Analysis of Mobile Artifacts:
      • JioFieldDiagnostics_1.0.20.apks (com.jio.test.scanner): The lightweight scanner and AES-128-GCM intent hand-
      off mechanism.
      • ESim.apk (com.jio.esim v1.7.157): The full core provisioning engine, RxBluetooth, Retrofit services, and
      room database.
  3. Complete End-to-End Provisioning Lifecycle (with Mermaid Sequence Diagram):
      • Phase 1: Barcode QR acquisition & XML decoding (SRNO, MODELNO, EID, BTMAC).
      • Phase 2: Bluetooth Low Energy GATT handshake (Service UUID 0000ca77..., Characteristic 0000ca7a...).
      • Phase 3: Dynamic PAN IP retrieval over BLE (192.168.44.32).
      • Phase 4: Local HTTPS authentication (/cgi-bin/app/account/auth, default credentials Admin / Jiocentrum).
      • Phase 5: eSIM profile injection (/cgi-bin/app/esim/profile_install) and 5G cellular RF telemetry testing
      (api/cellularInfo).
  4. Networking & Embedded SSL/TLS Engineering:
      • The embedded device HTTPS dilemma (why private local IPs cannot have public CA certificates).
      • In-depth line-by-line analysis of getUnsafeOkHttpClient() in RetrofitClient.java.
      • Complete Java and Kotlin code implementations for custom X509TrustManager (Trust-All) and HostnameVerifier.
      • Security implications (MITM vulnerabilities) and production alternatives (Certificate Pinning, Private Root
      CA, Android Network Security Config).
  5. Firmware Image Analysis (52240-21.img):
      • Identification as a Quectel FOTA package for RG520FJO (Qualcomm Snapdragon SDX62 "sdxlemur").
      • Internal partition layout: sdxlemur-boot.img, sdxlemur-sysfs.ubi, NON-HLOS.ubi.
      • The embedded Linux web server and CGI binaries running inside the ODU.
  6. Alternative Developer & Engineering Access Interfaces:
      • Direct PoE Ethernet connection to a laptop (http://192.168.225.1:8080, http://192.168.225.1/jiooscc/).
      • Indoor Unit (IDU) Wi-Fi Mesh Gateway link.
      • Remote Cloud TR-069 / CWMP ACS management.
      • Hardware UART Serial console (TX/RX debug pins on the PCB).

