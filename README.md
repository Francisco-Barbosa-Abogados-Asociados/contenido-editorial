# Contenido editorial

Aquí vive el contenido que se publica en **fbarbosaabogados.com**: las publicaciones, las fichas del
equipo y las áreas de práctica. El código del sitio **no está aquí** — está en un repositorio
privado aparte.

Se edita desde el panel, no a mano:

> **https://fbarbosaabogados.com/admin**

---

## Por qué el contenido está separado del código

Por dos razones, y las dos importan.

**La primera es el candado.** Ningún texto llega al sitio sin que un administrador lo apruebe. Eso lo
hace cumplir GitHub con la protección de la rama `main`: quien redacta puede proponer, no publicar.
En repositorios privados esa función se paga; en públicos es gratuita. Separar el contenido —que va a
ser público de todos modos, está en el sitio— permite tener el candado sin pagar por él y sin abrir
el código.

**La segunda es el alcance de los permisos.** Quien redacta las publicaciones tiene acceso a este
repositorio y a ninguno más. No puede ver ni tocar las funciones de servidor, las reglas de la base
de datos ni la configuración de seguridad del sitio.

⚠ **Este repositorio es público.** Un borrador en revisión vive como *pull request*, y en un
repositorio público los *pull requests* los puede leer cualquiera. No aparece en el sitio ni lo
indexan los buscadores, pero **no es privado**. Si un texto no puede leerse antes de aprobarse, no
se redacta aquí.

---

## Qué hay en cada archivo

| Ruta | Qué es | Quién lo edita |
|---|---|---|
| `es/publicaciones/*.md` | Una publicación por archivo. El encabezado son los datos; debajo va el texto | Mercadeo y administración |
| `es/equipo.yaml` | Las fichas del carrusel de equipo | Solo administración |
| `es/areas.yaml` | Las tres áreas de práctica | Solo administración |
| `assets/contenido/publicaciones/` | Las imágenes que se suben desde el panel | Se llena solo |

El orden de `es/equipo.yaml` y `es/areas.yaml` **es** el orden en que salen en la página. En las
publicaciones lo decide el campo `orden`.

`PENDIENTE` en un campo significa que el despacho todavía debe ese texto: el sitio dibuja el hueco
del diseño en lugar de un vacío. No es un error.

---

## Cómo se publica algo

1. Entras a **fbarbosaabogados.com/admin** con tu cuenta de GitHub.
2. Redactas. Lo que guardas queda en **borrador**: no está en el sitio.
3. Cuando esté listo, **enviar a revisión**.
4. Un administrador lo lee, lo previsualiza y lo aprueba.
5. El sitio se vuelve a generar y a publicar solo. **Tarda unos minutos.**

Mientras una publicación no tenga texto en el cuerpo, sale como tarjeta en la portada y «Leer más» no
lleva a ninguna parte. En cuanto tiene cuerpo, gana su propia página en `/publicaciones/`.

---

## Para quien mantiene esto

- La estructura de los campos la define el esquema del sitio (`src/content.config.mjs` en el
  repositorio privado) y la del panel (`public/admin/config.yml`). **Los dos tienen que decir lo
  mismo**, y hay un test que falla si divergen.
- `.github/workflows/verificar.yml` compila el sitio con este contenido en cada *pull request* y
  publica una vista previa real.
- `.github/workflows/avisar.yml` avisa al repositorio del sitio cuando algo se aprueba, que es lo
  que dispara el despliegue.

<!-- prueba de fusion directa -->
