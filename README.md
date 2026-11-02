# Ventanilla: catálogo público de portales

Catálogo de portales web de la administración que consume la app **Ventanilla** para
Sailfish OS (Jolla). La app lleva una copia dentro y comprueba aquí si hay una versión nueva.

- `catalogo-ventanilla.json`: el catálogo. Campo `version` entero que sube en cada publicación.
- `catalogo-ventanilla.json.sig`: firma Ed25519 del fichero anterior (64 bytes, base64).

La app solo acepta el catálogo si la firma valida con la clave pública que lleva compilada:

```
f1920c6f101f291930f78a55297b1b999dea95ba7aaf403acaebe78b1757051b
```

Por eso **solo el mantenedor puede publicar aquí**. Si quieres proponer un portal nuevo o
corregir una URL, abre un *issue* o un *pull request*: se revisa, se firma y se publica.

## Estructura

```json
{
  "version": 1,
  "secciones": [
    {
      "id": "ESP", "nombre": "España (AGE)",
      "entradas": [
        { "id": "carpeta", "nombre": "Mi Carpeta Ciudadana", "url": "https://carpetaciudadana.gob.es/",
          "desc": "Datos, expedientes y notificaciones", "auth": "clave", "estado": "pendiente", "favorito": true }
      ]
    }
  ]
}
```

`auth`: `ninguna` | `clave` | `certificado` | `usuario`. `estado`: `pendiente` | `ok` | `parcial` | `falla`
(lo que se ha probado en el navegador de Sailfish). Secciones actuales: ESP (Administración
General del Estado), AND (Junta de Andalucía), SEV (Diputación de Sevilla), ADR (Alcalá del Río)
y UE (Unión Europea). Cada usuario elige en la app qué secciones ve.

## Criterios para incluir un portal

- Trámite o consulta útil que funciona en un navegador web sin app nativa obligatoria.
- URL https estable del organismo (no enlaces a noticias ni PDF sueltos).
- Sin dependencia de NFC ni de Google Play Services.
