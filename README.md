# 🚀 Guías de Prácticas Laravel - TaskBoard: Pasarela de Pagos

![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

---

<p align="center">
  <img src="https://res.cloudinary.com/bcwlyire/image/upload/v1785118882/NUEVO-LOGO-UPED-A-COLOR-scaled_szoqws.jpg" alt="Logo UPED" width="300"/>
</p>

## 🏛️ Información Académica

- **Institución:** Universidad Pedagógica de El Salvador *Luis Alonso Aparicio*
- **Facultad:** Ingeniería
- **Asignatura:** Integración de Sistemas
- **Ciclo:** 02-2026
- **Docente:** Ing. Oscar Contreras
- **Proyecto Integrador:** TaskBoard - Pasarela de Pagos

---

## 📌 Descripción del Proyecto

Este repositorio contiene el trabajo de la **Semana 10** del proyecto **TaskBoard**, una plataforma de **Pasarela de Pagos** desarrollada en el framework **Laravel 11**.

En la Semana 9 el formulario "Nueva Transacción" ya guardaba datos, pero confiaba ciegamente en lo que recibía. Esta semana aprende a **rechazar datos inválidos** y a **organizar esa lógica**, a través de dos guías de laboratorio:

1. **Guía N.° 7 (jueves) — Validación de formularios:** reglas con `$request->validate()`, mensajes de error visibles junto a cada campo con `@error`, repoblado de los datos ya escritos con `old()`, **mensajes personalizados en español**, y la regla `exists:comercios,id` como capa extra que verifica contra la base de datos.
2. **Guía N.° 8 (viernes) — Form Requests:** la misma validación migrada a su propia clase `GuardarTransaccionRequest`, con `authorize()`, `rules()`, `messages()` y `attributes()`. Es un **refactor**: el controlador queda más corto y el formulario se comporta exactamente igual para el usuario final.

Al terminar, la validación vive en un solo archivo con nombre claro, reutilizable cuando el proyecto crezca.

---

## 📁 Estructura del Proyecto

A continuación se detalla la estructura principal del repositorio y del proyecto Laravel `taskboard`:

```text
taskboard/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── ComercioController.php                # Listado con buscador y filtro por rubro
│   │   │   └── TransaccionController.php             # store() con type-hint del Form Request
│   │   └── Requests/
│   │       └── GuardarTransaccionRequest.php         # authorize, rules, messages y attributes
│   └── Models/
│       ├── Comercio.php                              # hasMany(Transaccion)
│       ├── Transaccion.php                           # belongsTo(Comercio)
│       └── EventoTransaccion.php                     # belongsTo(Transaccion)
├── config/                                           # Archivos de configuración general del sistema
├── database/
│   ├── migrations/                                   # Tablas de comercios, transacciones y eventos
│   └── seeders/
│       └── ComercioSeeder.php                        # Datos de ejemplo usados en todas las guías
├── public/                                           # Punto de entrada de la aplicación (index.php) y assets
├── resources/
│   └── views/
│       ├── layouts/
│       │   └── app.blade.php                         # Layout maestro, mensaje flash y estilos de error
│       ├── components/                               # badge-estado, badge-actividad, resumen-actividad
│       ├── comercios/
│       │   ├── index.blade.php                       # Listado con buscador GET y filtro por rubro
│       │   └── show.blade.php                        # Detalle + enlace "Nueva transacción"
│       ├── transacciones/
│       │   └── create.blade.php                      # Formulario con @error, old() y resumen de errores
│       └── practica/
│           └── formulario_demo.blade.php             # Sandbox de formularios (no toca la base)
├── routes/
│   └── web.php                                       # Rutas de comercios, transacciones y práctica
├── storage/                                          # Registros (logs), archivos cargados y caché de la app
├── vendor/                                           # Dependencias de PHP administradas por Composer
├── .env.example                                      # Variables de entorno de ejemplo
├── composer.json                                     # Configuración de Composer y paquetes
└── README.md                                         # Documentación principal del repositorio
```
