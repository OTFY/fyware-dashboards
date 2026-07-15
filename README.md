# Fyware Dashboard Hub

Hub estatico en GitHub Pages que organiza los dashboards comerciales de Fyware (publicados como artefactos de Claude) en vista galeria, con seleccion multiple para abrirlos de un solo clic.

**URL:** https://otfy.github.io/fyware-dashboards/

## Como funciona

Los artefactos de Claude no se pueden embeber en iframes de otros sitios (claude.ai lo bloquea con la cabecera `frame-ancestors 'self'`). Por eso el hub funciona como **lanzador**: seleccionas los dashboards que quieres y los abre cada uno en su propia pestaña de claude.ai, donde cargan con datos en vivo y tu sesion de Claude.

Si el navegador bloquea la apertura multiple, el hub lo detecta y muestra un boton "Abrir" por dashboard. Para abrir varios de un clic, permite las ventanas emergentes de `otfy.github.io` la primera vez (icono en la barra de direcciones).

## Como agregar un dashboard

1. **Publica el dashboard en Claude** (Cowork) como artefacto y copia su URL publica (`https://claude.ai/public/artifacts/...`).
2. **Agrega el objeto al array `DASHBOARDS`** al inicio de `index.html`:

```js
{
  id: "mi-dashboard",              // unico, sin espacios
  titulo: "Mi Dashboard",
  descripcion: "Que muestra y para que sirve.",
  url: "https://claude.ai/public/artifacts/...",
  tags: ["Ventas"],                // uno o varios
  editado: "hace 3 dias"           // texto manual
}
```

3. Haz commit y push a `main`. GitHub Pages se redespliega solo en 1 o 2 minutos.

Si `url` queda vacia (`""`), la card aparece como "URL pendiente" y no se puede seleccionar ni abrir.

## Como se despliega

GitHub Pages sirve `index.html` desde la rama `main` (raiz). Cada push a `main` publica automaticamente.

## Notas

- Los dashboards son de datos en vivo: el HTML publicado jala HubSpot al cargar dentro de claude.ai. Solo se republican si cambia el diseño.
- Ver los datos requiere sesion activa de Claude; el hub solo lanza las pestañas.
- Este repo NO contiene datos de pipeline ni tokens; solo titulos, descripciones y URLs. Por eso puede ser publico.
- Un solo archivo `index.html`, sin frameworks ni build step.
