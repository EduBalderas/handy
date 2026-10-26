# handy

## META
- id: handy
- owner: EduBalderas
- visibility: public
- idioma: mixto
- estado: estable
- tipo: producto
- nivel: L3
  - L0=gobernanza/política
  - L1=marca/metodología
  - L2=flujo/arquitectura
  - L3=producto ejecutable
  - L4=herramienta
- familia: ninguna
- origen: upstream:https://github.com/cjpais/Handy
- experimento: no
- nacido_de: cjpais/Handy
- orquestado_por: N/A
- brief_desde: N/A

## OBJETIVO
Aplicación de escritorio para dictar en local: un atajo graba, transcribe en el equipo y pega el texto en la aplicación activa.

## QUE_CONTIENE
- App Tauri 2, versión 0.9.8: backend Rust en `src-tauri/` y UI React/TypeScript en `src/`.
- Grabación (`handy-recorder`), VAD Silero, transcripción (`transcribe-cpp` para Whisper/GGUF, `transcribe-rs` ONNX), historial SQLite, catálogo de modelos, overlay, atajos globales y CLI.
- Ajustes, onboarding, selector de modelos e i18n en `src/i18n/locales/`.
- `BUILD.md`, `CONTRIBUTING.md`, `flake.nix`, licencia MIT y notas en `src/content/release-notes/`.

## CARACTERISTICAS
- Atajo en Auto (mantener o pulsar), Hold o Toggle. Una sola instancia; en Linux el toggle también llega por `SIGUSR2`.
- Transcripción en Windows, macOS y Linux. El audio del dictado no sale del equipo. Silero filtra el silencio.
- Catálogo en `src-tauri/src/catalog/catalog.json`: whisper, parakeet, nemotron, canary, cohere, voxtral, qwen3, fun, gigaam, granite, medasr, moonshine, moss, sensevoice. GPU en la familia Whisper cuando el backend existe.
- Historial y post-proceso opcional. El proveedor custom acepta el formato Messages de Anthropic.
- CLI: `--toggle-transcription`, `--toggle-post-process`, `--cancel`, `--start-hidden`, `--no-tray`, `--debug`, `--transcribe-file`, `--list-models`, `--list-devices`.
- Debug con Cmd+Shift+D o Ctrl+Shift+D. Modelos GGML/GGUF propios en el directorio de datos o en la caché de Hugging Face.
- Releases de upstream, cask `handy`, winget `cjpais.Handy` y `.deb`. La clave pública del updater está en `src-tauri/tauri.conf.json`.

## FUERA_DE_ALCANCE
- No es un servicio de dictado en la nube ni envía el audio a transcribir.
- El nombre, el logo y el icono quedan fuera de la MIT.
- El cask de Homebrew y el paquete winget no los mantienen los desarrolladores de Handy.
- La tecla fn/Globe solo dispara el atajo en teclados Apple.
- En Wayland el atajo global lo define el escritorio. En Linux el overlay arranca en None: si toma el foco, el pegado falla. Hace falta `xdotool`, `wtype` o `dotool` según el servidor gráfico.
- Los pesos no están en el repo; se descargan o se copian a mano si hay proxy.
- `handy-cli` es otro repositorio. Una feature nueva choca con el feature freeze de upstream si no hay discusión previa.
- El post-proceso con un LLM externo puede enviar texto fuera; no forma parte de la transcripción local. En Linux ya no se escucha `SIGUSR1` (lo usa WebKitGTK).

## RELACIONES
- Upstream: https://github.com/cjpais/Handy
- Sitio: https://handy.computer
- CLI original: https://github.com/cjpais/handy-cli
- Discord: https://discord.com/invite/WVBeWsNXK4
- Extensión Raycast: https://github.com/mattiacolombomc/raycast-handy
- Sponsors: Wordcab, Epicenter, Bolt AI, Canty Digital
- MIT, copyright 2025 CJ Pais. Base: Whisper, ggml, Silero, Tauri.

## ETIQUETAS
- dictado
- voz-a-texto
- offline
- tauri
- fork
- mit

## TOPICS_GITHUB
- speech-to-text
- whisper
- tauri
- rust
- desktop-app
- voice-recognition
