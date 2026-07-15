# Fyware Dashboard Hub

Hub estatico en GitHub Pages que muestra los dashboards comerciales de Fyware (publicados como artefactos de Claude) en vista galeria, con seleccion multiple para verlos en cuadricula.

**URL:** https://otfy.github.io/fyware-dashboards/

## Como agregar un dashboard

1. **Publica el dashboard en Claude** (Cowork) como artefacto y copia su URL publica (`https://claude.ai/public/artifacts/...`).
2. **Autoriza el embed:** en el artefacto publicado, abre su configuracion y agrega `otfy.github.io` a la lista de **Allowed domains**. Sin este paso el iframe no cargara.
3. **Agrega el objeto al array `DASHBOARDS`** al inicio de `index.html`:

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

4. Haz commit y push a `main`. GitHub Pages se redespliega solo en 1 o 2 minutos.

Si `url` queda vacia (`""`), la card aparece como "URL pendiente" y no se puede seleccionar.

## Como se despliega

GitHub Pages sirve `index.html` desde la rama `main` (raiz). Cada push a `main` publica automaticamente.

## Notas

- Los dashboards son de datos en vivo: el HTML publicado jala HubSpot al cargar. Solo se republican si cambia el diseño.
- Este repo NO contiene datos de pipeline ni tokens; solo titulos, descripciones y URLs. Por eso puede ser publico.
- Un solo archivo `index.html`, sin frameworks ni build step.
