# miOS

Un sistema operativo x86 de 32 bits escrito desde cero en **C** y **ensamblador (NASM)**, arrancado con GRUB (Multiboot). Proyecto de aprendizaje, diseñado para escalar después a x86_64.

> Estado: en desarrollo temprano. Por ahora solo se distribuyen las imágenes ISO.

## Descargas

Las ISO están en la sección [Releases](../../releases).

| Versión | Qué incluye |
|---|---|
| **v0.3** | Timer (PIT), buffer de teclado, mini shell con comandos |
| **v0.2** | GDT, IDT, PIC, interrupciones y teclado básico |

Verifica la integridad con `SHA256SUMS.txt`:

```bash
sha256sum -c SHA256SUMS.txt
```

## Cómo ejecutarlo

### VMware Workstation

1. Crea una VM nueva: **Custom → I will install the OS later → Other**.
2. **Firmware: BIOS** (no UEFI; la ISO usa GRUB para BIOS).
3. 1 procesador, 128-256 MB de RAM, disco de 1 GB.
4. CD/DVD → **Use ISO image file** → selecciona `miOS-vX.Y.iso` y marca *Connect at power on*.
5. Enciende la VM.

### QEMU

```bash
qemu-system-i386 -cdrom miOS-v0.3.iso
```

## Comandos de la shell (v0.3)

| Comando | Descripción |
|---|---|
| `help` | Lista los comandos |
| `clear` | Limpia la pantalla |
| `echo <texto>` | Imprime el texto |
| `uptime` | Tiempo desde el arranque |
| `sleep <ms>` | Espera N milisegundos |
| `about` | Información del sistema |
| `reboot` | Reinicia la máquina |
| `halt` | Detiene la CPU |

## Características técnicas

- Arquitectura: x86 (i386), modo protegido de 32 bits
- Bootloader: GRUB 2 con Multiboot 1
- GDT con modelo flat (código y datos kernel)
- IDT con 32 excepciones del CPU y 16 IRQs
- PIC 8259 remapeado a los vectores 32-47
- PIT a 100 Hz (1 tick = 10 ms)
- Driver de teclado PS/2 con buffer circular
- Driver de texto VGA (80x25) con scroll y cursor por hardware

## Limitaciones conocidas

- El mapa de teclado es **US**; en teclados en español algunos símbolos cambian de lugar.
- Sin gestión de memoria, multitarea ni sistema de archivos todavía.

## Hoja de ruta

- [ ] Gestión de memoria (mapa de GRUB, paginación, `kmalloc`)
- [ ] Multitarea y scheduler
- [ ] Layouts de teclado
- [ ] Sistema de archivos
- [ ] Espacio de usuario y syscalls
- [ ] Port a x86_64

## Licencia

Por definir.

## Primer imagen del sistema

<img src="Captura de pantalla 2026-10-11 005531.png" alt="miOS ejecutándose" width="600">
