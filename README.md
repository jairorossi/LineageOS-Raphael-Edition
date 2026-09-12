# 🌿 LineageOS 19.1 - Raphael Edition (by Jairo)

<div align="center">

![LineageOS](https://img.shields.io/badge/LineageOS-19.1-008080?style=for-the-badge&logo=lineageos&logoColor=white)
![Android](https://img.shields.io/badge/Android-12.1%20%2F%2012L-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Device](https://img.shields.io/badge/Device-Xiaomi%20Mi%209T%20Pro%20(raphael)-FF6900?style=for-the-badge&logo=xiaomi&logoColor=white)
![Kernel](https://img.shields.io/badge/Kernel-4.14.x%20SM8150-blue?style=for-the-badge&logo=linux&logoColor=white)
![Status](https://img.shields.io/badge/Status-Est%C3%A1vel%20%26%20Fluido-brightgreen?style=for-the-badge)

**Build personalizada da LineageOS 19.1 (Android 12.1 / 12L) para o Xiaomi Mi 9T Pro / Redmi K20 Pro (`raphael`).**  
*Desenvolvida e otimizada por **Jairo Rossi** para máxima estabilidade, autonomia de bateria e experiência fluida.*

</div>

---

## 📋 Informações do Sistema e do Dispositivo

| Especificação | Detalhes |
| :--- | :--- |
| **Dispositivo:** | Xiaomi Mi 9T Pro / Redmi K20 Pro (`raphael` / `raphaellin`) |
| **SoC / Processador:** | Qualcomm Snapdragon 855 (SM8150) Octa-Core |
| **Versão do Android:** | 12.1 / 12L (API 32) - Linha LineageOS 19.1 |
| **Estrutura de Partições:** | Retrofit Dynamic Partitions |
| **Leitor Biométrico (FOD):** | Goodix Optical In-Display Fingerprint (100% calibrado e estável) |
| **Root / Privilégios:** | Suporte a KernelSU nativo / Magisk |
| **Firmware Base Recomendado:** | MIUI Global V12.5.2.0.RFKMIXM (Android 11 Vendor Base) |

---

## ✨ Recursos e Destaques desta Edição

1. 🌿 **Estabilidade e Fluidez Absolutas:**
   - Base LineageOS 19.1 pura, sem bloatware, focada no máximo desempenho do Snapdragon 855.
2. 🟢 **Leitor Biométrico (FOD) 100% Funcional:**
   - Leitura de impressão digital sob a tela instantânea, sem atrasos e sem falhas de cadastro.
3. 🛡️ **Suporte a KernelSU Nativo:**
   - Permite gerenciamento de root diretamente pelo kernel sem modificar partições do sistema.
4. 🔋 **Otimização de Bateria e Térmica:**
   - Perfis de governor e gerenciamento de energia calibrados para evitar aquecimento excessivo e maximizar o tempo de tela ativa (SOT).
5. 📱 **Pop-up Camera & Áudio Calibrados:**
   - Efeitos sonoros e visuais do motor da câmera pop-up e calibração de áudio de alta fidelidade nativos.

---

## 📥 Downloads dos Arquivos

> [!NOTE]
> Todos os arquivos necessários para uma instalação limpa e segura do zero.

| Arquivo | Descrição | Link de Download |
| :--- | :--- | :---: |
| 📦 **LineageOS 19.1 ROM** | Build oficial customizada `lineage-19.1-*-UNOFFICIAL-raphael.zip` | *(Link em atualização)* |
| 🦊 **OrangeFox Recovery** | Recovery compatível com Retrofit Dynamic Partitions | *(Link em atualização)* |
| 🔄 **Super Empty** | `super_empty.img` para preparar as partições dinâmicas (retrofit) | [`/files/super_empty.img`](files/super_empty.img) |
| 🛡️ **Boot com Magisk** | `boot_custom.img` (kernel 4.14 da LOS + Magisk embutido) | *(Link em atualização)* |
| 📶 **Firmware MIUI 12.5.2** | Firmware global oficial necessário para os modems | *(Link em atualização)* |
| 📦 **NikGApps (Opcional)** | Pacote Google Play Store / Serviços (Core / Basic recomendados) | [NikGApps A12.1](https://nikgapps.com/downloads) |

---

## 🚀 Guia de Instalação Passo a Passo

### ⚠️ Requisitos Prévios
* Bootloader do Xiaomi Mi 9T Pro desbloqueado.
* Cabo USB original + `adb` e `fastboot` (platform-tools) instalados no PC.
* Bateria com pelo menos 60% de carga.
* Arquivos baixados: `OrangeFox-R11.3_Unified-Unofficial-raphael.zip`, `super_empty.img` e a `lineage-19.1-*-raphael.zip`.

---

### 📲 Passo a Passo (método correto com Retrofit Dynamic Partitions)

1. **Instalar o Recovery (OrangeFox):**
   ```bash
   # no fastboot
   fastboot flash recovery OrangeFox-R11.3_Unified-Unofficial-raphael.zip
   ```
   *(se o `.img` for necessário, extraia o arquivo `recovery.img` de dentro do zip)*

2. **Wipe Inicial:**
   * Entre no OrangeFox.
   * **Wipe > Format Data** e digite `yes`.
   * Faça também Wipe de: `Dalvik / ART Cache`, `Cache` e `System`.

3. **Preparar o Super (partições dinâmicas):**
   * Reinicie para o **fastboot**.
   ```bash
   fastboot wipe-super super_empty.img
   ```

4. **Instalar a ROM:**
   * Reinicie de novo para o **recovery (OrangeFox)**.
   * Instale via ADB Sideload:
   ```bash
   adb sideload lineage-19.1-*-UNOFFICIAL-raphael.zip
   ```

5. **Opcional — Root via Magisk (boot_custom.img):**
   * Após o boot, volte ao **fastboot** e flashe o boot com Magisk embutido:
   ```bash
   fastboot flash boot boot_custom.img
   ```

6. **Finalização:**
   * **Reboot System** e aguarde o primeiro boot (pode levar alguns minutos).

---

## 🛠️ Como Compilar a ROM do Zero (Build Guide)

Se você deseja compilar esta edição da LineageOS 19.1 a partir do código-fonte:

### 1. Preparar o Ambiente de Build (Ubuntu 20.04 / 22.04 LTS)
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32readline-dev lib32z1-dev libelf-dev liblz4-tool libncurses5 libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev python3 openjdk-11-jdk -y
```

### 2. Configurar o Repo e Clonar o Manifesto
```bash
mkdir -p ~/android/lineage && cd ~/android/lineage
repo init -u https://github.com/LineageOS/android.git -b lineage-19.1 --git-lfs
```

### 3. Adicionar o Local Manifest do Raphael
Crie o arquivo `~/.android/lineage/.repo/local_manifests/raphael.xml` com o conteúdo presente na pasta [`local_manifests/raphael.xml`](local_manifests/raphael.xml) deste repositório e sincronize:
```bash
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j$(nproc --all)
```

### 3.5. Prebuilt Apps (automático)

Os apps pré-compilados (Miui Gallery, Miui Gallery Editor, GBoard e MarkupGoogle) ficam no repositório [`jairorossi/vendor_jairo_apps`](https://github.com/jairorossi/vendor_jairo_apps) (via [Git LFS](https://git-lfs.com)), já referenciado no `local_manifest`. O `repo sync` já os baixa automaticamente — **nenhum passo manual é necessário**.

### 4. Compilar a ROM
```bash
export USE_CCACHE=1
ccache -M 20G
source build/envsetup.sh
lunch lineage_raphael-userdebug
mka bacon -j$(nproc --all)
```
O arquivo `.zip` final instalável será gerado em `out/target/product/raphael/`.

> [!WARNING]
> ### ⚠️ Aviso crítico sobre o boot (kernel)
> A ROM compila normalmente (status=0), porém o **kernel CAF (`UtsavBalar1231/kernel_xiaomi_raphael`) NÃO boota** no aparelho — ele inicia e cai para fastboot.
>
> **Solução (já validada):** após flashear a ROM, flashe o **`boot_custom.img`** (kernel 4.14 da LOS + Magisk) por cima:
> ```bash
> fastboot flash boot boot_custom.img
> ```
> O `boot_custom.img` é o **kernel definitivo** que boota. Ele fica na pasta do projeto (não versionado no git por ter 128MB / exceder o limite do GitHub).
>
> **Para reproduzir em servidor novo:** pegar o `boot_custom.img` da Release/backup e copiar para a pasta do projeto.

---

## 📝 Notas de Build (estado atual & decisões)

Estas notas explicam decisões importantes para quando trocar de servidor ou recompilar:

1. **Arch tuning ativo:** `TARGET_ARCH_VARIANT := armv8-2a` + `TARGET_CPU_VARIANT := kryo385` (Cortex-A76) estão em `jairorossi/android_device_xiaomi_sm8150-common` → melhora desempenho usando ARMv8.2-A.

2. **Kernel:** o `UtsavBalar1231/kernel_xiaomi_raphael` (CAF, `android11`) compila e gera o `raphael-sm8150-overlay.dtbo`, mas **não boota** no hardware. O boot funcional é via `boot_custom.img` (flash manual). *(Pendência: investigar o kernel correto que boota direto — candidato: `firebird11`/crDroid `16.0-raphael`.)*

3. **MindTheGapps:** branch `sigma` (SDK 32 / Android 12.1) — o nome `lineage-19.1` foi renomeado no projeto MindTheGapps. A ROM sai com GApps embutida.

4. **hardware/xiaomi:** apontado para o upstream `LineageOS/android_hardware_xiaomi` (`lineage-19.1`), pois fornece o `xiaomifingerprint_headers` (necessário para o UDFPS/fingerprint).

5. **Three-finger swipe screenshot:** ⏳ **Ainda não aplicado** nesta build. O commit de referência é o do PixelOS (`c6290c54`, "base: Add three-fingers-swipe to screenshot"). Precisa de adaptação manual no `frameworks/base` (PhoneWindowManager + ActivityManagerService) pois as assinaturas divergem do LineageOS 19.1.

6. **Bootanimation "Jairo Edition"** (1080x360): ✅ restaurado via `TARGET_BOOTANIMATION` no `device.mk` do raphael.

---

## 🤝 Créditos e Agradecimentos

* [LineageOS Project](https://github.com/LineageOS)
* [TheMuppets](https://github.com/TheMuppets) (Proprietary vendor blobs)
* [@raphael_alpha](https://t.me/raphael_alpha) (Retrofit Dynamic partitions tooling)
* Comunidade Xiaomi Mi 9T Pro / Redmi K20 Pro

---

<div align="center">
  <b>Mantido por Jairo Rossi (@jairorossi)</b><br>
  <i>Desenvolvido com carinho para a comunidade Raphael!</i>
</div>
