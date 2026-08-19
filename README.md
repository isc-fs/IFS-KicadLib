# 📦 Librería de Electrónica ISC — IFS-KicadLib

Repositorio central de componentes, huellas y modelos 3D para el diseño de las placas de telemetría, distribución de potencia y sistemas del **IFS-08** y sucesivos.

> Aquí viven **todos los componentes custom** del equipo. Si lo soldas en una PCB del IFS, su símbolo, huella y modelo 3D deben estar aquí.

---

## ⚙️ Configuración del Entorno (¡Importante!)

Para que los modelos 3D y las rutas no se rompan al clonar este repositorio, debes configurar la siguiente variable de entorno en tu KiCad local:

1. Abre KiCad → **Preferencias → Configurar rutas...**
2. Crea una variable llamada **`ISC_KICAD_LIB`**
3. Asigna como valor la ruta absoluta donde has clonado esta carpeta en tu ordenador.
   - Ejemplo Windows: `C:\Users\tunombre\repos\IFS-KicadLib`
   - Ejemplo Linux/macOS: `/home/tunombre/repos/IFS-KicadLib`

### Añadir las librerías a KiCad

#### Símbolos
Abre KiCad → **Preferencias → Gestionar librerías de símbolos** → pestaña **"Global"** → botón **"+"** y añade los `.kicad_sym` de `${ISC_KICAD_LIB}/isc_lib/simbolos/`.

| Nickname | Ruta |
|---|---|
| `ISC_conectores` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_conectores.kicad_sym` |
| `ISC_ic_logica` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_ic_logica.kicad_sym` |
| `ISC_ic_potencia` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_ic_potencia.kicad_sym` |
| `ISC_sensores` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_sensores.kicad_sym` |
| `ISC_electromecanica` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_electromecanica.kicad_sym` |
| `ISC_proteccion` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_proteccion.kicad_sym` |
| `ISC_mecanica` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_mecanica.kicad_sym` |
| `ISC_modulos_pcb` | `${ISC_KICAD_LIB}/isc_lib/simbolos/isc_modulos_pcb.kicad_sym` |

#### Huellas
Abre KiCad → **Preferencias → Gestionar librerías de huellas** → pestaña **"Global"** → botón **"+"** y añade los directorios `.pretty` de `${ISC_KICAD_LIB}/isc_lib/huellas/`.

| Nickname | Ruta |
|---|---|
| `ISC_conectores` | `${ISC_KICAD_LIB}/isc_lib/huellas/isc_conectores.pretty` |
| `ISC_mecanica` | `${ISC_KICAD_LIB}/isc_lib/huellas/isc_mecanica.pretty` |
| `ISC_paquetes` | `${ISC_KICAD_LIB}/isc_lib/huellas/isc_paquetes.pretty` |
| `ISC_sensores` | `${ISC_KICAD_LIB}/isc_lib/huellas/isc_sensores.pretty` |
| `ISC_electromecanica` | `${ISC_KICAD_LIB}/isc_lib/huellas/isc_electromecanica.pretty` |
| `ISC_modulos_pcb` | `${ISC_KICAD_LIB}/isc_lib/huellas/isc_modulos_pcb.pretty` |

---

## 📁 Estructura del repositorio

```
isc_lib/
├── simbolos/                        ← Librerías de símbolos KiCad
│   ├── isc_resistencias.kicad_sym
│   ├── isc_condensadores.kicad_sym
│   ├── isc_inductores.kicad_sym
│   ├── isc_cristales.kicad_sym
│   ├── isc_proteccion.kicad_sym     ← Diodos, TVS, varistores
│   ├── isc_conectores.kicad_sym     ← Molex MicroFit, TE, XT60
│   ├── isc_ic_logica.kicad_sym      ← CAN, LDO, lógica digital
│   ├── isc_ic_potencia.kicad_sym    ← MOSFETs, relés, DC/DC
│   ├── isc_sensores.kicad_sym       ← IMU, temperatura IR, corriente
│   ├── isc_electromecanica.kicad_sym← LEDs, switches, porta-fusibles
│   ├── isc_mecanica.kicad_sym       ← Logo ISC, agujeros, elementos mec.
│   └── isc_modulos_pcb.kicad_sym    ← Símbolos de PCBs enteras del equipo
│
├── huellas/                         ← Huellas KiCad (.pretty)
│   ├── isc_conectores.pretty/
│   ├── isc_mecanica.pretty/
│   ├── isc_paquetes.pretty/         ← Encapsulados genéricos (SOT, SOIC...)
│   ├── isc_sensores.pretty/
│   ├── isc_electromecanica.pretty/
│   └── isc_modulos_pcb.pretty/      ← Huellas de PCBs externas
│
└── modelos3d/                       ← Modelos 3D (.step / .stp / .wrl)
    ├── conectores/
    ├── mecanica/
    ├── paquetes/
    ├── sensores/
    └── modulos_pcb/                 ← Modelos 3D de PCBs completas
```

---

## 📏 Nomenclatura Estándar

Todos los componentes nuevos deben seguir estrictamente este formato para mantener el BOM ordenado:

| Tipo | Formato | Ejemplo |
|---|---|---|
| Resistencias | `RES_[Tamaño]_[Valor]_[Tol]` | `RES_0603_10k_1%` |
| Condensadores | `CAP_[Tamaño]_[Valor]_[Voltaje]` | `CAP_0805_100nF_50V` |
| Conectores | `CONN_[Marca]_[Serie]_[Pines]` | `CONN_Molex_MicroFit_6P` |
| Integrados/Sensores | `[Función]_[Referencia]_[Encapsulado]` | `CAN_ISO1042_SOIC16` |
| Módulos PCB | `MOD_[Nombre]_[Versión]` | `MOD_MAIN_LITE_v1` |

---

## 🛠️ Reglas de Diseño (Atomic Parts)

1. **Símbolos completos:** Todo símbolo nuevo debe tener rellenados los campos `Footprint`, `Datasheet` y `MPN` (Manufacturer Part Number).
2. **Reutilización de huellas:** No crees huellas nuevas si el componente usa un encapsulado estándar (SOIC-8, 0603, SOT-23...). Usa las de `isc_paquetes.pretty` o directamente las de KiCad estándar.
3. **Modelos 3D:** Al asignar un modelo `.step` a una huella, usa **SIEMPRE** la variable de entorno. La ruta debe verse así:
   ```
   ${ISC_KICAD_LIB}/isc_lib/modelos3d/conectores/430450600.stp
   ```
4. **No dupliques:** Antes de añadir un componente, busca si ya existe en esta librería. Si existe y está incompleto, corrígelo en vez de duplicarlo.
5. **Un commit = un componente:** Los commits de nuevos componentes deben ser atómicos: símbolo + huella + modelo 3D en el mismo commit.

---

## 🗂️ Inventario de Componentes (v1.0)

### Módulos PCB (`isc_modulos_pcb`)

| Símbolo | Descripción | Huella | Modelo 3D |
|---|---|---|---|
| `MAIN_LITE` | Placa principal ECU IFS08 | `isc_modulos_pcb:MAIN_LITE` | `modelos3d/modulos_pcb/MAIN_LITE.step` |
| `BRK_LIGHT` | Placa luces de freno | `isc_modulos_pcb:BRK_LIGHT` | `modelos3d/modulos_pcb/ES_004-PCB_BRAKE_LIGHT.step` |
| `GPS_Ultimate` | Módulo GPS Adafruit (PA6H) | `isc_modulos_pcb:GPS_Ultimate` | `modelos3d/modulos_pcb/Adafruit_Ultimate_GPS.step` |
| `IFS06_MCU` | Placa MCU IFS06 | `isc_modulos_pcb:IFS06_MCU` | — |
| `CLQ6B_RGB_LED` | LED RGB 6mm (Cree CLQ6B) | `isc_modulos_pcb:CLQ6B` | — |

### Conectores (`isc_conectores`)

| Símbolo | MPN | Serie | Pines | Modelo 3D |
|---|---|---|---|---|
| `CONN_Molex_MF_1x02_M` | 430450200 | Micro-Fit 3.0 | 2P macho | `430450200.stp` |
| `CONN_Molex_MF_2x02_M` | 430450400 | Micro-Fit 3.0 | 4P macho | `430450400.stp` |
| `CONN_Molex_MF_2x03_M` | 430450600 | Micro-Fit 3.0 | 6P macho | `430450600.stp` |
| `CONN_Molex_MF_2x04_M` | 430450800 | Micro-Fit 3.0 | 8P macho | `430450800.stp` |
| `CONN_Molex_MF_1x03_F` | 436500300 | Micro-Fit 3.0 | 3P hembra | `436500301.stp` |
| `CONN_Molex_MF_1x02_F` | 436500200 | Micro-Fit 3.0 | 2P hembra | `436500200.stp` |
| `CONN_TE_770669-1` | 770669-1 | AMP | — | `c-770669-1-p-3d.stp` |
| `CONN_TE_282837-2` | 282837-2 | AMP | — | `c-282837-2-g2-3d.stp` |
| `CONN_TE_776267-1` | 776267-1 | AMP 14P | 14P | `776267-1.stp` |
| `CONN_TE_1-776087-1` | 1-776087-1 | AMP | — | `1-776087-1.stp` |
| `CONN_Molex_43045-1200` | 43045-1200 | SL | 12P | — |
| `CONN_XT60PW-M` | XT60PW-M | Amass XT60 | 2P power | `XT60PW-M.STEP` |

### ICs de Lógica y Regulación (`isc_ic_logica`)

| Símbolo | MPN | Función | Encapsulado |
|---|---|---|---|
| `ISO1042` | ISO1042BQDWVQ1 | CAN transceiver aislado | SOIC-16W |
| `MCP2561FD` | MCP2561FD-E/SN | CAN FD transceiver | SOIC-8 |
| `TLE4284DV33` | TLE4284DV33ATMA1 | LDO 3.3V | SC-74 |
| `LD39200PU33R` | LD39200PU33R | LDO 3.3V 2A | TO-252 |
| `MCP1755_3V3` | MCP1755ST-3302E/DB | LDO 3.3V | SOT-23-5 |
| `MC74AC74DG` | MC74AC74DG | D flip-flop dual | SOIC-14 |
| `NE555PW` | NE555PW | Timer 555 | TSSOP-8 |

### ICs de Potencia (`isc_ic_potencia`)

| Símbolo | MPN | Función | Encapsulado |
|---|---|---|---|
| `OKI-78SR-5` | OKI-78SR-5/1.5-W36-C | DC/DC step-down 5V | SIP-3 |
| `TDR_3-1212SM` | TDR 3-1212SM | DC/DC aislado ±12V | SIP |
| `RTE24012` | RTE24012 | Relé 24V | PCB relay |
| `IRLZ44N` | IRLZ44NSTRLPBF | MOSFET N logic-level | TO-263 |
| `IPN80R3K3P7` | IPN80R3K3P7ATMA1 | MOSFET N 800V | TO-263 |
| `DMN6075SQ` | DMN6075SQ-7 | MOSFET N dual | SOT-363 |

### Sensores (`isc_sensores`)

| Símbolo | MPN | Función | Encapsulado |
|---|---|---|---|
| `BMI088` | BMI088 | IMU 6-DOF (acc+gyro) | LGA-16 |
| `BNO085` | BNO085 | IMU 9-DOF fusión | LGA-28 |
| `MLX90640` | MLX90640ESF-BAB-000-SP | IR array 32×24px | TO-39 |
| `CAS-220TA1` | CAS-220TA1 | Sensor de corriente | — |

### Electromecánica (`isc_electromecanica`)

| Símbolo | MPN | Descripción |
|---|---|---|
| `FUSE_3568` | Littelfuse 3568 | Portafusibles para auto |
| `SW_1571563-6` | TE 1571563-6 | Pulsador |
| `LED_CLQ6B` | CLQ6B-TKW-S1L1R1H1TBB7935BB3 | LED RGB 6mm Cree |
| `LED_CL6K4-G` | CL6K4-G | LED |
| `LED_150080RS75000` | 150080RS75000 | LED SMD Würth |
| `DISP_ACSC02` | ACSC02-41CGKWA-F01 | Segmento LED |

### Protección (`isc_proteccion`)

| Símbolo | MPN | Descripción |
|---|---|---|
| `DIODE_GF1A` | GF1A-E3/67A | Diodo rectificador 1A |

---

## 🔄 Flujo para añadir un nuevo componente

```
1. Descarga el símbolo/huella desde UltraLibrarian o SnapEDA
2. Coloca el símbolo en isc_lib/simbolos/isc_[categoria].kicad_sym
3. Coloca la huella en isc_lib/huellas/isc_[categoria].pretty/
4. Coloca el modelo 3D en isc_lib/modelos3d/[categoria]/
5. Actualiza la ruta del modelo 3D en la huella: ${ISC_KICAD_LIB}/isc_lib/modelos3d/...
6. Completa los campos: MPN, Datasheet, Footprint, Value
7. Abre un PR con el nombre: "add: [MPN] - [descripción breve]"
```

---

## 📋 Historial de versiones

| Versión | Fecha | Descripción |
|---|---|---|
| v1.0 | 2026-08 | Primera release: componentes extraídos de IFS08, IFS05 y proyectos existentes |

---

*Mantenido por el equipo de electrónica de **ISC — ICAI Formula Student***