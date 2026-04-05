# Semaforo-Vehicular-PLC
Control de semáforo vehicular con modo emergencia — Siemens S7-1500, TIA Portal, Ladder
Semáforo Vehicular con Modo Emergencia
PLC: Siemens S7-1500 (CPU 1511-1 PN)
Software: TIA Portal V21
Lenguaje: Ladder (LAD)
Descripción
Sistema de control de semáforo vehicular programado en PLC Siemens S7-1500. Implementa ciclo automático Verde → Amarillo → Rojo con modo de emergencia que fuerza luz roja inmediatamente al activarse.

Tabla de Variables
Nombre      Tipo   Dirección  Descripción
Green_Light  Bool  %Q0.0  Salida luz verde
Yellow_Light  Bool  %Q0.1  Salida luz amarilla
Red_Light  Bool  %Q0.2  Salida luz roja
Emergency_Stop  Bool  %I0.3  Entrada botón emergencia
Emergency_Mode  Bool  %M0.4  Marca modo emergencia activo
Reset_Cycle  Bool  %M0.5  Marca reset de ciclo


Lógica del Programa
Network    Función
Network 1  Activación modo emergencia
Network 2  Luz roja forzada en emergencia
Network 3  Timer 5s y activación luz verde
Network 4  Timer 2s y activación luz amarilla
Network 5  Timer 5s y activación luz roja
Network 6  Reset automático del ciclo

Ciclo Normal
- Verde: 5 segundos
- Amarillo: 2 segundos
- Rojo: 5 segundos
- Reinicio automático continuo

Modo Emergencia
Al activar Emergency_Stop todas las luces se apagan y Red_Light es forzado a estar activo mientras dure la emergencia. Al desactivarse el botón el ciclo retoma desde verde.


Software requerido
- TIA Portal V17 o superior
- SIMATIC S7-PLCSIM V21 para simulación
