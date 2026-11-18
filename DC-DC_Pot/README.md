<p align="center">
  <img src="../SPWM_EGS032/assets/180pixel.png" width="160" alt="Salmetronic">
</p>

<h1 align="center">DC-DC_Pot · Conversor reductor ajustable con LM2576HV</h1>

<p align="center">
  <b>Módulo conversor DC-DC <i>step-down</i> (buck) de 3 A basado en el regulador conmutado LM2576HVS-ADJ, con tensión de salida ajustable mediante potenciómetro multivuelta.</b>
</p>

<p align="center">
  <img alt="Versión de hardware" src="https://img.shields.io/badge/hardware-Ver%201.0-informational">
  <img alt="Estado" src="https://img.shields.io/badge/estado-prototipo-yellow">
  <img alt="Licencia" src="https://img.shields.io/badge/licencia-CC%20BY--NC--SA%204.0-blue">
</p>

<p align="center">
  <img src="assets/Captura%20de%20pantalla%202026-11-18%20190457.png" width="750" alt="Render 3D del conversor DC-DC_Pot">
</p>

---

## 📑 Índice

- [Descripción](#-descripción)
- [Características principales](#-características-principales)
- [Especificaciones técnicas](#-especificaciones-técnicas)
- [Ajuste de la tensión de salida](#-ajuste-de-la-tensión-de-salida)
- [Lista de materiales (BOM)](#-lista-de-materiales-bom)
- [Esquemático](#-esquemático)
- [Galería](#-galería)
- [Estructura del proyecto](#-estructura-del-proyecto)
- [Seguridad](#-seguridad)
- [Licencia](#-licencia)
- [Autor](#-autor)

---

## ⚡ Descripción

**DC-DC_Pot** es una placa compacta de desarrollo propio que implementa un conversor reductor (*buck*) no aislado a partir del regulador conmutado **LM2576HVS-ADJ** en encapsulado **TO-263-5**. Está pensada para obtener una tensión regulada (por defecto **+5 V**) a partir de un bus de alimentación de mayor tensión (nominal **+18 V**), como los presentes en tarjetas de control, drivers y bancos de pruebas de electrónica de potencia.

La tensión de salida se ajusta mediante un **potenciómetro multivuelta (trimmer)** en el lazo de realimentación, lo que permite reutilizar el mismo módulo para distintas tensiones de salida sin cambiar componentes.

## 🚀 Características principales

- **Regulador conmutado LM2576HV:** versión de alta tensión con entrada de hasta **60 V** y corriente de salida de hasta **3 A**.
- **Salida ajustable:** potenciómetro multivuelta (R1) para fijar con precisión la tensión de salida.
- **Alta eficiencia:** topología *buck* con diodo Schottky **SS310** (3 A / 100 V) como diodo de libre circulación.
- **Filtrado de entrada y salida:** condensadores electrolíticos SMD de baja ESR y condensador cerámico de desacoplo en la salida.
- **Conexión sencilla:** pads de gran superficie con taladro pasante para **IN+ / IN−** y **OUT+ / OUT−**.
- **Diseño compacto:** todos los componentes en la cara superior; plano de masa para mejorar la disipación térmica y reducir la EMI.

## 📋 Especificaciones técnicas

| Parámetro | Valor |
| :--- | :--- |
| Versión de hardware | **Ver 1.0** |
| Topología | Reductor (*buck*) no aislado |
| Regulador | **LM2576HVS-ADJ** (TO-263-5) |
| Tensión de entrada | **+18 V** nominal (máx. 60 V según LM2576HV*) |
| Tensión de salida | **+5 V** por defecto, ajustable (≈ 1,23 V … V<sub>IN</sub> − ~2 V) |
| Corriente de salida | Hasta **3 A** |
| Frecuencia de conmutación | 52 kHz (fija, interna del LM2576) |
| Inductancia | 100 µH |
| Diodo de libre circulación | **SS310** Schottky (3 A / 100 V) |
| Pin ENABLE | Conectado a GND → conversor siempre activo |
| Software de diseño | EasyEDA Pro |

> \* La tensión máxima real de entrada queda limitada también por la tensión nominal del condensador de entrada **C1**. Verifícala antes de superar la tensión nominal de diseño.

## 🎛️ Ajuste de la tensión de salida

La tensión de salida la fija el divisor resistivo formado por **R1** (potenciómetro de 20 kΩ) y **R2** (750 Ω) sobre el pin **FEEDBACK** del LM2576-ADJ:

$$V_{OUT} = V_{REF} \cdot \left(1 + \frac{R_1}{R_2}\right) \qquad V_{REF} = 1{,}23\ \text{V}$$

| V<sub>OUT</sub> deseada | Valor aproximado de R1 (con R2 = 750 Ω) |
| :---: | :---: |
| 3,3 V | ≈ 1,26 kΩ |
| 5 V | ≈ 2,30 kΩ |
| 9 V | ≈ 4,74 kΩ |
| 12 V | ≈ 6,57 kΩ |

**Procedimiento recomendado:**

1. Antes de alimentar, gira el potenciómetro hacia el valor mínimo de resistencia (mínima tensión de salida).
2. Alimenta la placa por **IN+ / IN−** sin carga conectada.
3. Mide la salida en **OUT+ / OUT−** con un multímetro y ajusta R1 hasta la tensión deseada.
4. Conecta la carga y verifica de nuevo la tensión.

> Para un correcto funcionamiento, la tensión de entrada debe ser al menos ~2 V superior a la tensión de salida ajustada.

## 🧾 Lista de materiales (BOM)

| Ref. | Componente | Valor / Modelo | Encapsulado |
| :--- | :--- | :--- | :--- |
| U8 | Regulador conmutado reductor | LM2576HVS-ADJ | TO-263-5 |
| L1 | Inductor de potencia | 100 µH | SMD apantallado |
| D1 | Diodo Schottky | SS310 | SMA / SMB |
| C1 | Condensador electrolítico (entrada) | 100 µF | SMD electrolítico |
| C2 | Condensador electrolítico (salida) | 300 µF | SMD electrolítico |
| C3 | Condensador cerámico (desacoplo) | 100 nF | SMD |
| R1 | Potenciómetro multivuelta | 20 kΩ | Trimmer vertical |
| R2 | Resistencia | 750 Ω | SMD |

## 📐 Esquemático

El esquemático completo está disponible en **[docs/SCH_DC_DC_LM2576_2026-11-18.pdf](docs/SCH_DC_DC_LM2576_2026-11-18.pdf)** (hoja *POWER DC-DC*, revisión Ver 1.0).

Resumen del circuito:

- **+18 V** entra por el pin **INPUT** de U8, filtrado por **C1**.
- El nodo de conmutación **SW_OUT** se conecta al cátodo de **D1** y a la bobina **L1**, que entrega la salida **+5 V**.
- **C2** y **C3** filtran la tensión de salida.
- El divisor **R1 / R2** realimenta la salida al pin **FEEDBACK**.
- El pin **ENABLE** (ON/OFF) está conectado a GND, manteniendo el regulador siempre activo.

## 🖼️ Galería

| Render 3D | Vista superior (PCB) |
| :---: | :---: |
| ![Render 3D](assets/Captura%20de%20pantalla%202026-11-18%20190457.png) | ![Vista superior del PCB](assets/Captura%20de%20pantalla%202026-11-18%20190429.png) |

## 📂 Estructura del proyecto

```text
DC-DC_Pot/
├── README.md                                   # Documentación de esta placa
├── assets/                                     # Renders y capturas de la PCB
│   ├── Captura de pantalla 2026-11-18 190429.png   # Vista superior del PCB
│   └── Captura de pantalla 2026-11-18 190457.png   # Render 3D
└── docs/
    └── SCH_DC_DC_LM2576_2026-11-18.pdf         # Esquemático completo
```

> **Nota:** el archivo fuente de EasyEDA Pro (`DC-DC_LM2576.eprj2`) no se publica en este repositorio (excluido mediante `.gitignore`). Si necesitas el diseño editable, solicítalo al autor.

## ⚠️ Seguridad

Aunque se trata de un conversor de baja tensión, puede manejar corrientes elevadas y algunos componentes (U8, L1, D1) **se calientan** durante el funcionamiento a plena carga. Respeta la polaridad de entrada (la placa **no** incorpora protección contra inversión de polaridad), no superes las tensiones nominales de los condensadores y ajusta la salida **sin carga** antes de conectar equipos sensibles.

## 📄 Licencia

La documentación y los recursos gráficos de este proyecto se publican bajo la licencia **Creative Commons Reconocimiento-NoComercial-CompartirIgual 4.0 Internacional (CC BY-NC-SA 4.0)**. Consulta el texto completo en [LICENSE](../LICENSE).

## 🛡️ Propiedad intelectual y marca

© 2026 **Salmetronic**. El nombre comercial «Salmetronic» y su logotipo son marcas protegidas y **no** están cubiertas por la licencia de contenido. Queda prohibido su uso para la comercialización o distribución de productos de terceros sin autorización previa por escrito.

## 👤 Autor

**Salmetronic** — Diseño y desarrollo de hardware de potencia.
