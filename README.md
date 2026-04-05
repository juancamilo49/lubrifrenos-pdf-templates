# Lubrifrenos PDF Templates

Templates HTML para generación de PDFs con Gotenberg desde n8n.

## Estructura

```
/facturas/factura.html   → Template de factura de venta
```

## Variables disponibles

Cada template usa `{{variable}}` como placeholder. En n8n reemplazarlos con el nodo **Code** antes de enviar a Gotenberg.

## Uso en n8n

1. Nodo **HTTP Request** → `GET https://raw.githubusercontent.com/juancamilo49/lubrifrenos-pdf-templates/main/facturas/factura.html`
2. Nodo **Code** → reemplazar variables con datos reales
3. Nodo **HTTP Request** → `POST http://gotenberg:3000/forms/chromium/convert/html`
   - Body: Form-Data
   - Field: `files` | Filename: `index.html` | Content: HTML resultante

## Actualizar templates

Edita el HTML en GitHub y ejecuta en el VPS:
```bash
# Solo si se usa copia local, no es necesario si n8n descarga directo del repo
git -C /opt/gotenberg/templates pull
```
