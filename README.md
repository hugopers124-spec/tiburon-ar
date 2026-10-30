# Tiburón AR

Experiencia de realidad aumentada hecha con **A-Frame 1.5.0** y **MindAR 1.2.5**. La cámara reconoce la tarjeta del tiburón y muestra el modelo 3D encima. El tiburón gira 360° solo, se mueve suavemente como si nadara, y también se puede girar arrastrando el dedo.

Página publicada: https://hugopers124-spec.github.io/tiburon-ar/

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La página de realidad aumentada |
| `targets.mind` | La tarjeta del tiburón compilada para MindAR (objetivo 0) |
| `marcador-tiburon.png` | La imagen que reconoce la cámara: imprímela o ábrela en otra pantalla |
| `tiburon.glb` | Modelo 3D del tiburón, optimizado de 23.2 MB a 2.8 MB |

## Cómo probarlo

1. Abre la página desde una dirección **https** (por ejemplo, GitHub Pages). La cámara no funciona si abres el archivo directo desde la computadora.
2. Acepta el permiso de la cámara.
3. Apunta a la tarjeta, impresa o en otra pantalla.

## Giro 360°

- El tiburón da una vuelta completa cada 12 segundos.
- Arrastra el dedo (o el mouse) a los lados para girarlo a mano. El giro automático vuelve 2 segundos después de soltar.
- El botón **Pausar** detiene el giro; **Girar** lo reanuda.

## Ajustes

En `index.html` hay 3 niveles:

1. La entidad de base: `position` (x, y, z) es dónde va el tiburón sobre la tarjeta y `rotation` es su inclinación. La tarjeta mide 1 de ancho.
2. `giro-360`: `inicio` es el ángulo con el que arranca y `velocidad` son los grados por segundo (30 = una vuelta cada 12 s; 0 = sin giro automático).
3. `<a-gltf-model>`: `scale` es el tamaño y `animation` es el vaivén de arriba abajo.

Si cambias la imagen de la tarjeta, vuelve a compilar `targets.mind` con el [compilador de MindAR](https://hiukim.github.io/mind-ar-js-doc/tools/compile).

## Cómo se optimizó el modelo

```
npx @gltf-transform/cli optimize original.glb tiburon.glb --compress quantize --texture-compress webp --texture-size 1024 --simplify-ratio 0.2 --simplify-error 0.001
```
