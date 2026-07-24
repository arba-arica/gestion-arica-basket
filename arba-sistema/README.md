# Sistema ARBA · ABA

Sistema de gestión deportiva para básquetbol de la XV Región (Arica y Parinacota).

## Estructura del repo

```
├── index.html          # Frontend — se despliega en Netlify (aricabasquet.netlify.app)
└── apps-script/
    └── Code.gs          # Backend — Google Apps Script (doGet / doPost), vive en el proyecto
                          # de Apps Script vinculado a la planilla Google Sheets (base de datos)
```

## Cómo se despliega cada parte

**Frontend (`index.html`)**
Se sirve como sitio estático en Netlify. Si este repo queda conectado a Netlify
(Site settings → Build & deploy → Link repository), cada `git push` a la rama
principal dispara un deploy automático — no requiere build step, es HTML plano.

**Backend (`apps-script/Code.gs`)**
Este archivo es la fuente de verdad versionada, pero **Apps Script no lee directo
desde GitHub**. Para que un cambio hecho aquí quede activo en el sistema real, hay
que copiarlo manualmente al editor de Apps Script (Extensiones → Apps Script, en la
planilla de Google Sheets) — o sincronizar con [`clasp`](https://github.com/google/clasp)
si más adelante se quiere automatizar el push.

## Versión actual

- Apps Script backend: **v3.7**
- Frontend: Sistema de Gestión Deportiva Básquetbol XV Región

## Convenciones

- Commits en español, en tiempo presente y descriptivos (ej. `agrega módulo de carga masiva FEBA`).
- Cambios al backend: probar en una copia de la planilla antes de pegar en producción.
- No subir credenciales, tokens ni el ID de la planilla de Google Sheets a este repo.
