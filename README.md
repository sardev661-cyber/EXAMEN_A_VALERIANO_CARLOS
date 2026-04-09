# 🤖 Bot Consulta ONPE (Dockerizado & Optimizado)

Bot automatizado para la consulta de miembros de mesa de la ONPE usando Docker + Selenium + Chromium (headless).

## 🏗️ Arquitectura

El sistema utiliza una arquitectura basada en contenedores Docker con volúmenes compartidos.

## 🔧 Componentes

### Host (Tu PC)
- Archivo onpe.xlsx
- Docker instalado

### Contenedor
- Alpine Linux (ultra ligero)
- Python 3.11
- Chromium (modo headless)
- Selenium
- Usuario seguro AppUser (no root)

## 🚀 Uso rápido

### 1. 📄 Preparar archivo
Crear archivo: onpe.xlsx  
Colocar DNIs en:  
Columna A (desde A2)  
Guardar y cerrar

### 2. 📥 Descargar imagen
```bash
docker pull cerex1452/reniec-app:latest
```

### 3. ▶️ Ejecutar (Docker)
```bash
docker run -it --rm -v "$(pwd)":/app cerex1452/reniec-app:latest
```

🪟 Windows (PowerShell)
```powershell
docker run -it --rm -v ${PWD}:/app cerex1452/reniec-app:latest
```

## 📊 Resultados

El archivo Excel se actualiza automáticamente con colores:

- 🟨 Amarillo → Miembro de mesa
- 🟩 Verde → Ciudadano regular
- 🟥 Rojo → Error / DNI inválido

## ⚙️ Build de la imagen (para GitHub / desarrollo)

Si quieres construir la imagen localmente:

```bash
docker build -t reniec-app .
```

Luego ejecutar:

```bash
docker run -it --rm -v "$(pwd)":/app reniec-app
```

## 📁 Estructura del proyecto
```
.
├── Dockerfile
├── requirements.txt
├── bot.py
├── onpe.xlsx
└── README.md
```

## ⚡ Optimización

| Característica | Standard | Optimizado |
|----------------|----------|------------|
| OS | Debian Slim | Alpine |
| Tamaño | ~1.57 GB | ~450 MB |
| Navegador | Chrome | Chromium |
| Seguridad | Root | No-Root |

## 🔐 Seguridad

- Usuario sin privilegios (AppUser)
- Contenedor aislado
- Sin acceso directo al sistema host (solo volumen montado)

## ☁️ Escalabilidad

Este bot puede ejecutarse sin cambios en:

- AWS (EC2 / ECS)
- Azure
- Google Cloud
- VPS

## 🧠 ¿Por qué usar Docker?

- Portabilidad total
- Entorno reproducible
- Sin conflictos de dependencias
- Fácil despliegue

## 🛠️ Requisitos

- Docker instalado → https://www.docker.com/
- Archivo onpe.xlsx

## 📌 Notas

- No abrir el Excel mientras corre el bot
- Requiere conexión a internet
- Puede haber bloqueos si la web cambia

## 📄 Licencia

MIT License

## ⭐ Contribuir

Pull requests y mejoras son bienvenidas.