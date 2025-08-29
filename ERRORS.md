# 📘 Bitácora de Errores – CalmUp!

Registro cronológico de errores, causas y soluciones aplicadas durante el desarrollo de **CalmUp! (Flutter)**.

# Entradas

### 🗓️ 2025-08-28 — _Build/Entorno_

#### Error #1 – `<span>flutter doctor</span>`: Licencias Android no aceptadas + conexión iPhone (code -27)

- **Error/Mensaje:**
  - `<span>Some Android licenses not accepted. To resolve this, run: flutter doctor --android-licenses</span>`
  - `<span>Error: Browsing on the local area network for Jefferson’s iPhone 16 pro ... The device must be opted into Developer Mode to connect wirelessly. (code -27)</span>`
- **Síntomas:**`<span>flutter doctor</span>` reportaba 2 advertencias.
- **Causa raíz:**
  - Faltaba aceptar licencias del Android SDK.
  - iPhone sin **Developer Mode** activo y/o intento de conexión inalámbrica sin confiar el dispositivo.
- **Solución aplicada:**
  1. Ejecutado `<span>flutter doctor --android-licenses</span>` y aceptadas todas las licencias.
  2. Conexión del iPhone por **cable**, dispositivo **desbloqueado**, **Confiar en este ordenador**, y activación de **Modo Desarrollador** (Ajustes → Privacidad y seguridad → Modo desarrollador → On).
- **Validación/Resultado:**`<span>flutter doctor</span>` → **No issues found!** ✅
- **Notas/Prevención:** Aceptar licencias tras actualizar SDK; preferir conexión por cable y mantener Developer Mode activo para debug iOS.

---

### 🗓️ 2025-08-28 — _Ejecución en dispositivo iOS_

#### Error #2 – iOS: “Untrusted Developer” al abrir la app

- **Error/Mensaje:\***“Untrusted Developer – Your device management settings do not allow using apps from developer ‘Apple Development: _[_jeffersonguzman167@icloud.com_]()_’ (AQN3CXDFW9)…”\*
- **Síntomas:** iPhone bloquea la apertura de la app instalada desde Flutter/Xcode.
- **Causa raíz:** El dispositivo no confiaba aún en el certificado **Apple Development** del Apple ID utilizado.
- **Solución aplicada:**
  - iPhone → **Ajustes → General → VPN y gestión de dispositivos (o Perfiles)** → **Apple Development: [Apple ID]** → **Confiar**.
  - (En caso de no aparecer) Reinstalar desde Xcode con **Automatically manage signing**, seleccionar **Personal Team** y usar **Bundle Identifier** único; asegurarse de que **Developer Mode** está activo.
- **Validación/Resultado:** La app abre normalmente en el dispositivo físico. ✅
- **Notas/Prevención:** Mantener el dispositivo en **Developer Mode** y firmado con **Personal Team**. Cambiar el `<span>Bundle Identifier</span>` por uno único (p. ej. `<span>com.jeffer.calmup</span>`).
