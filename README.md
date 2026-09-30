# EDAT

**EDAT** es un prototipo de seguimiento de vacantes y candidatos para El Puerto de Liverpool, desarrollado para Liverhack 2026. Reúne en un solo flujo la requisición, la evaluación de candidatos y el avance hasta la oferta e incorporación.

🔗 **Demo live:** [luisangelfc.github.io/EDAT](https://luisangelfc.github.io/EDAT/)

> La aplicación es una demostración con información ficticia. No es un sistema de autenticación ni debe usarse para almacenar información real de candidatos.

## Perfiles disponibles

Desde la pantalla de inicio se puede entrar a cualquiera de estos espacios. Para el prototipo basta con elegir un perfil e ingresar cualquier correo con formato válido.

| Perfil | Espacio |
| --- | --- |
| Atracción de Talento | Tablero de vacante, candidatos, entrevistas, evaluaciones y cierre |
| HRBP | Requisición y seguimiento de la vacante |
| Hiring Manager | Alineación, revisión de candidatos y entrevistas |
| Candidato | Seguimiento del proceso, entrevistas, oferta y comunicación |

El flujo visible de la vacante consta de seis etapas: requisición, alineación, búsqueda, entrevistas de Atracción de Talento, entrevistas de Hiring Manager y oferta/cierre. Las acciones de los distintos perfiles actualizan el estado compartido de la demo.

## Ejecutar localmente

No se requiere instalar dependencias ni compilar el proyecto. Sirve los archivos estáticos desde la raíz del repositorio; por ejemplo, con Python:

```bash
python -m http.server 8000
```

Después abre [http://localhost:8000](http://localhost:8000). También puedes usar cualquier servidor local de archivos estáticos. Es preferible a abrir `index.html` directamente, ya que el prototipo navega entre varias páginas.

## Estructura

```text
.
├── index.html             # Inicio y selección de perfil
├── html/
│   ├── login.html         # Espacio de Atracción de Talento
│   ├── hrbp.html
│   ├── hiring-manager.html
│   └── candidato.html
├── css/                   # Estilos por pantalla y flujo
├── js/
│   ├── login.js           # Selección de perfil e inicio de sesión demo
│   ├── edat-flow.js       # Flujo y estado compartido
│   ├── candidatos-db.js   # Datos ficticios de candidatos
│   └── ...                # Lógica de cada perfil
└── recursos/              # Logos e imágenes
```

## Datos y estado

El prototipo funciona enteramente en el navegador, sin backend. Los registros de ejemplo están definidos en `js/candidatos-db.js`; el estado del proceso y la sesión se guardan en `localStorage` bajo las claves `edatFlujo` y `talentoSession`. Por ello, el estado se conserva entre recargas en el mismo navegador y origen. Para empezar de nuevo, borra esas claves desde las herramientas de desarrollo del navegador o usa una ventana privada.

## Tecnologías

- HTML, CSS y JavaScript sin framework ni proceso de build.
- `localStorage` para persistencia local de la demo.
- Google Fonts (Inter); se requiere conexión a internet para cargar esa tipografía.
- GitHub Pages para publicar el demo live.
