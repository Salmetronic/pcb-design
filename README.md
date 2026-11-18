# 🧩 PCB Design · Salmetronic

Repositorio central de diseños de PCB de desarrollo propio. Cada diseño se organiza en su propia carpeta con documentación, renders y esquemático.

---

## 📚 Diseños

| Proyecto | Descripción | Versión | Documentación |
| :--- | :--- | :---: | :--- |
| **[SPWM_EGS032](SPWM_EGS032/)** | Interfaz de disparo por fibra óptica para variadores de frecuencia (VFD) e inversores solares | 1.0 | [README](SPWM_EGS032/README.md) · [Esquemático](SPWM_EGS032/docs/esquemas.pdf) |
| **[DC-DC_Pot](DC-DC_Pot/)** | Conversor reductor (buck) de 3 A con LM2576HV y salida ajustable por potenciómetro | 1.0 | [README](DC-DC_Pot/README.md) · [Esquemático](DC-DC_Pot/docs/SCH_DC_DC_LM2576_2026-11-18.pdf) |

<p align="center">
  <a href="SPWM_EGS032/README.md">
    <img src="SPWM_EGS032/assets/imagen-3D.png" width="620" alt="Render 3D de la placa SPWM_EGS032">
  </a>
</p>

---

## 🗂️ Estructura del repositorio

```text
pcb-design/
├── .gitattributes            # Tratamiento de archivos binarios
├── .gitignore                # Archivos temporales y fuentes no publicadas
├── LICENSE                   # Licencia CC BY-NC-SA 4.0
├── CHANGELOG.md              # Historial de versiones
├── README.md                 # Índice del repositorio
├── SPWM_EGS032/
│   ├── README.md             # Documentación de la placa
│   ├── assets/               # Logo, renders y capturas
│   └── docs/                 # Esquemático en PDF
└── DC-DC_Pot/
    ├── README.md             # Documentación de la placa
    ├── assets/               # Render 3D y vista del PCB
    └── docs/                 # Esquemático en PDF
```

---

## 📄 Licencia

La documentación y los recursos gráficos de este repositorio se publican bajo la licencia **Creative Commons Reconocimiento-NoComercial-CompartirIgual 4.0 Internacional (CC BY-NC-SA 4.0)**. Consulta el texto completo en [LICENSE](LICENSE).

Copyright © 2026 **Salmetronic**.
