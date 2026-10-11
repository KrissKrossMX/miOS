# Changelog

## [0.3] - 2026-10-11
### Añadido
- Timer PIT a 100 Hz con `timer_ticks()` y `timer_sleep()`
- Buffer circular de teclado con `keyboard_getchar()`
- Mini shell con los comandos `help`, `clear`, `echo`, `uptime`, `sleep`, `about`, `reboot` y `halt`
- Funciones básicas de cadenas y memoria (`strlen`, `strcmp`, `memset`, `memcpy`)
- Cursor de hardware que sigue la escritura
- `term_print_dec()` para imprimir números decimales

### Cambiado
- El teclado ya no imprime directamente; entrega las teclas a la shell
- Máscara del PIC: ahora IRQ0 (timer) e IRQ1 (teclado) activas

## [0.2] - 2026-10-11
### Añadido
- GDT propia con modelo flat
- IDT con manejo de las 32 excepciones del CPU (pantalla roja con EIP y código de error)
- PIC remapeado a los vectores 32-47
- Driver de teclado PS/2 con soporte de Shift y Backspace (layout US)

## [0.1] - 2026-10-11
### Añadido
- Arranque Multiboot con GRUB
- Salida de texto VGA con scroll y colores
