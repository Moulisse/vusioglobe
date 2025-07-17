---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://plus.unsplash.com/premium_photo-1670872717035-d84647297aa8?q=80&w=1740&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
# some information about your slides (markdown enabled)
title: Vettting started
titleTemplate: '%s'
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
colorSchema: dark
fonts:
  sans: Comic Neue
favicon: 'https://cdn.francetravail.fr/studio/logos/marque/favicon/favicon.svg'
---

# Vusioglobe

Présentation d'outils à utiliser dans vos projets vue

---

# Voici quelques outils bien sympatiques :

(par ordre de sympathie)

- Typescript
- Linter
- VueUse
- UnJS / auto import
- Tailwind
- Iconify

---

# Typescript

Utilisez typescript s'il vous plait ceci est un appel à l'aide.

Un projet bien typé est un projet sain

<img src="./assets/ts_is_hard.png" class="scale-70 absolute left-0 top-40">
<img src="./assets/heart.jpg" class="scale-50 absolute -left-10 top-60">
<img src="./assets/heart.jpg" class="scale-50 absolute right-0 top-10">

---

# Choisissez un linter

- Détecter les erreurs
- Applique des rêgles de formatage

On utilise :

<img src="./assets/eslint.png" class="w-[40%] m-auto">

Nouveau cool kid :

<img src="./assets/oxc.png" class="w-[40%] m-auto">

---

# VueUse

Une collection de composables d'utilité publique

```vue
<script setup lang="ts">
import { useMouse } from '@vueuse/core';

const { x, y } = useMouse()
</script>

<template>
  Pointer X : {{ x }}<br>
  Pointer Y : {{ y }}
</template>
```

C'est réactif !

<WindowSize />

<br>
<br>

`useStorage`, `useElementSize`, `useWindowScroll`, `useBreakpoints`, `useClipboard`, `useTitle`, `useFocus`, `useFps`, `useWebSocket`, `useVirtualList`, 
`useDateFormat`, `useTimeAgo`, `useDraggable`, `useMouseInElement`, `useDark`, `useCeQueVousVoulez`, `useCaffée`, `useJacuzzi`, `usePizza4Fromage`,

---

# UnJS / auto import

\- de code = + de place pour plus de code 

Grace à `unplugin-auto-import` et `unplugin-vue-components`

````md magic-move {lines: true}
```vue
<script setup lang="ts">
import { useMouse } from '@vueuse/core';
import AppHeader from '@/components/AppHeader.vue'

const { x, y } = useMouse()
</script>

<template>
  <AppHeader />
</template>
```

```vue
<script setup lang="ts">
const { x, y } = useMouse()
</script>

<template>
  <AppHeader />
</template>
```
````

---

# Tailwind CSS

(Ou UnoCSS)

Plus besoin de réecrire

```css
.flex {
  display: flex;
}
```

dans chaque projet !

Avantages :

- Moins de css dans le code
- Moins de css dans le bundle final
- Meilleur collaboration d'équipe

Inconvénients :
- Peu devenir illisible si mal utilisé (mais je sais que vous être de super dev donc ca ne devrait pas arriver) 

---

# Iconify

200 000 icônes open source

Une liste se trouve ici https://icones.js.org/ :

<img src="./assets/icones.png" class="w-[60%] m-auto">

---
