+++
title = 'Como Consigo Textos Bonitos en mi Blog'
date = 2025-03-24T22:50:56+01:00
tags = ["programación", "css"]
draft = false
+++

Puede que te hayas dado cuenta al entrar en mi blog de que mi texto es un poco diferente: está justificado correctamente, las palabras no se cortan de forma extraña y, en general, es más agradable a la vista. Aunque parezca una tontería, esto hasta hace poco era muy difícil de hacer correctamente y es por esto que rara vez se ven textos justificados en la _web_.

Pero ya no hay excusa, desde la última versión de CSS esto es ahora muy sencillo. A continuación muestro el único CSS necesario para tener párrafos bien justificados.

```css
p {
    hyphens: auto;
    hyphenate-limit-chars: 7;
    text-align: justify;
    text-wrap: pretty;
}
```
(Sí, es solo esto)

Línea por línea:
- `hyphens: auto`: Divide palabras largas para evitar desbordamientos y mejorar la legibilidad. Sin esta propiedad, los textos justificados pueden tener espacios irregulares y verse desordenados.
- `hyphenate-limit-chars: 7`: Evita cortar palabras cortas, que suelen verse mal cuando se dividen. Yo he encontrado que con 7 es como más me gusta, pero puedes ajustarlo según tus preferencias.
- `text-align: justify`: Justifica el texto, creando líneas de igual longitud. Esto da un aspecto más formal y pulido al texto.
- `text-wrap: pretty`: (Experimental) Intenta evitar cortes de línea feos.


Es importante anotar que `text-wrap: pretty`, al ser todavía experimental por ser tan reciente, no funciona en todos los búscadores, según [Can I use](https://caniuse.com/?search=text-wrap%3A%20pretty%3B) solo funciona en búscadores basados en _chromium_, y no en _firefox_ o _safari_, por lo que para casos más formales sería mejor no usarlo todavía.

**¿Qué busca mejorar `text-wrap: pretty`?**

Evita que una única palabra quede al final de un párrafo o al inicio de una página. Reduce los guiones innecesarios, sobre todo en palabras cortas. Además, intenta que todas las líneas tengan una longitud similar. Y por último y lo más importante, rompe las líneas donde naturalmente harías una pausa al hablar (tras comas, puntos, etc.) por lo que queda un resultado mucho más natural.

Espero que te haya sido útil y puedas aprovecharlo en tu próximo proyecto.
