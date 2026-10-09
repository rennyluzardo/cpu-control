# 💻 Sistema de Control y Mantenimiento de CPUs (CPU Control)

¡Bienvenido al repositorio de **CPU Control**! Este proyecto es una solución integral para el diagnóstico, control y mantenimiento de equipos informáticos (CPUs), que integra tecnologías modernas para ofrecer una experiencia rápida, segura e inteligente.

## 🚀 Arquitectura y Stack Tecnológico

El sistema está diseñado bajo una arquitectura modular y desacoplada, asegurando escalabilidad y facilidad de mantenimiento:

### 🌐 Frontend (Interfaz de Usuario)
- **Framework:** React + Vite
- **Enrutamiento:** TanStack Router
- **Estilos/UI:** Diseño moderno, responsivo y dinámico.

### ⚙️ Backend (API y Lógica de Negocio)
- **Framework:** Laravel 11 (PHP 8.3+)
- **Base de Datos:** PostgreSQL (BD: `diagnostico_cpus`)
- **Autenticación:** Implementación segura mediante la tabla personalizada `usuarios`.

### 🧠 Microservicio de Inteligencia Artificial (AI Worker)
- **Framework:** FastAPI (Python)
- **Servidor:** Uvicorn
- **Función:** Procesamiento asíncrono para automatización y diagnósticos inteligentes.
- **Ubicación:** `services/ai-worker/`

---

## 🛠️ Requisitos Previos

Antes de comenzar, asegúrate de tener instalado en tu entorno local:
- [PHP 8.3 o superior](https://www.php.net/) (Recomendado usar Laragon en Windows, aunque funciona en cualquier entorno)
- [Composer](https://getcomposer.org/) para dependencias de Laravel
- [Node.js y npm/pnpm](https://nodejs.org/) para el entorno frontend
- [PostgreSQL](https://www.postgresql.org/) (Esquema estricto)
- [Python 3.10+](https://www.python.org/) para el microservicio de IA

---

## 📦 Instalación y Configuración Local

### 1. Clonar el repositorio
```bash
git clone https://github.com/rennyluzardo/cpu-control.git
cd cpu-control
```

### 2. Configurar la Base de Datos (PostgreSQL)
1. Crea una base de datos vacía llamada `diagnostico_cpus` en tu gestor PostgreSQL.
2. Asegúrate de configurar correctamente el esquema `public`.

### 3. Configurar el Backend (Laravel)
```bash
cd backend
composer install
cp .env.example .env
php artisan key:generate

# IMPORTANTE: Actualizar las credenciales de PostgreSQL en el archivo .env
# DB_CONNECTION=pgsql
# DB_DATABASE=diagnostico_cpus

php artisan migrate
```

### 4. Configurar el Frontend (React + Vite)
```bash
cd frontend
npm install
npm run dev
```

### 5. Configurar el Microservicio de IA (FastAPI)
```bash
cd services/ai-worker

# Crear entorno virtual (Recomendado)
python -m venv venv

# Activar el entorno virtual
# En macOS/Linux: source venv/bin/activate 
# En Windows: venv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt

# Iniciar el servicio
uvicorn main:app --reload
```

---

## 🏗️ Estructura del Proyecto

```text
cpu-control/
├── backend/               # API REST construida con Laravel 11
├── frontend/              # Aplicación SPA construida con React y Vite
├── services/
│   └── ai-worker/         # Microservicio en FastAPI para procesamiento con IA
└── README.md              # Documentación principal del proyecto
```

---

## 📜 Principios de Desarrollo y Arquitectura

Este proyecto obedece estrictamente a los siguientes principios para mantener un código limpio, seguro y mantenible:
- **KISS y YAGNI:** Soluciones simples. No se deben crear abstracciones para problemas hipotéticos.
- **DRY:** Lógica centralizada; cero repetición de código.
- **Single Responsibility (SRP):** Cada módulo, controlador (delgado) o clase resuelve una tarea específica.
- **Seguridad Estricta:** Las contraseñas siempre se validan mediante `Hash::check()` y la integración con el frontend debe ser completamente a través de rutas API.

**Nota:** Todo el código fuente es estrictamente moderno. No se mezcla lógica ni estilo de frameworks heredados (como CodeIgniter). Toda la documentación, comentarios y respuestas deben ser en **español**.
