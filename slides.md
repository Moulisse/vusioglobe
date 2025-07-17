---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://images.unsplash.com/photo-1550025899-5f8a06b1b3a8?q=80&w=2574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
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

# Vue 3 my beloved

1 introduction de 2 minutes à Vue 3 sans sans passer par 4 chemins

---

# Prérequis

<div></div>

Les bases de ces langages :

- html
- Javascript
- CSS

Optionnel :

- 250mg de caffeine

---

# Declarative Rendering

Afficher un truc qui bouge

````md magic-move {lines: true}
```vue {*}
<!-- Du javascript dans la balise script -->
<script setup>
const counter = 0
</script>
```

```vue {1,6-8}
<!-- De l'html dans la balise template -->
<script setup>
const counter = 0
</script>

<template>
  <p>Count is: {{ counter }}</p>
</template>
```

```vue {1,3-5}
<!-- On rend reactif la variable 'counter' -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <p>Count is: {{ counter }}</p>
</template>
```

```vue {*}
<!-- '.value' pour acceder à la valeur -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)

setInterval(() => counter.value++, 1000)
</script>

<template>
  <p>Count is: {{ counter }}</p>
</template>
```
````

<p v-if="$clicks >= 3">
Résultat :

<Autocounter />
</p>

---

# Attribute Bindings

Modifier des trucs du html

````md magic-move {lines: true}
```vue {*}
<!-- Pas très réactif tout ca -->
<script setup>
</script>

<template>
  <h1 class="title">Make me red</h1>
</template>

<style>
.title {
  color: red;
}
</style>
```

```vue {*}
<!-- deux points pour rendre l'attribut 'class' réactif -->
<script setup>
import { ref } from 'vue'

const titleClass = ref('title')
</script>

<template>
  <h1 :class="titleClass">Make me red</h1>
</template>

<style>
.title {
  color: red;
}
</style>
```
````

<p v-if="$clicks >= 0">
<Attribute />
</p>

---

# Event listeners

Ca fait un truc quand je clique

````md magic-move {lines: true}
```vue {*}
<!-- On reprend notre compteur -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <p>Count is: {{ counter }}</p>
</template>
```

```vue {1,7-9,14}
<!-- @click pour écouter la souris -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)

function add(n) {
  counter.value += n
}
</script>

<template>
  <p>Count is: {{ counter }}</p>
  <button @click="add(1)">+1</button>
</template>
```
````

<p v-if="$clicks >= 1">
<Counter />
</p>

---

# Form Bindings

Deux trucs qui se partagent une variable

````md magic-move {lines: true}
```vue {5,13|7-9,13}
<!-- Two-way binding avec un :truc et un @truc -->
<script setup>
import { ref } from 'vue'

const text = ref('Hello')

function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <input :value="text" @input="onInput">
  <p>{{ text }}</p>
</template>
```

```vue {*}
<!-- Simplifion avec 'v-model' -->
<script setup>
import { ref } from 'vue'

const text = ref('Hello')
</script>

<template>
  <input v-model="text">
  <p>{{ text }}</p>
</template>
```
````

<p v-if="$clicks >= 0">
<Twoway />
</p>

---

# Conditional Rendering

Des if / else dans le template

````md magic-move {lines: true}
```vue {*}
<!-- Encore ce bon vieux compteur -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <p>Count is: {{ counter }}</p>
  <button @click="counter++">+1</button>
</template>
```

```vue {*}
<!-- Encore ce bon vieux compteur -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)
</script>

<template>
  <p v-if="counter === 0">Count is zero</p>
  <p v-else-if="counter <= 1">Count is one</p>
  <p v-else>Count is too much</p>
  <button @click="counter++">+1</button>
</template>
```
````

<p v-if="$clicks >= 0">
<Cond />
</p>

---
layout: two-cols
---

# List Rendering

Afficher N trucs

````md magic-move {lines: true}
```vue {*}
<!-- v-for et v-key -->
<script setup lang="ts">
import { ref } from 'vue';

const l = ref([1, 2, 3])
</script>

<template>
  <ul>
    <li v-for="item of l" :key="item">
      {{ item }}
    </li>
  </ul>
</template>
```

```vue {1,9-11}
<!-- Une fonction pour ajouter un element -->
<script setup lang="ts">
import { ref } from 'vue';

const l = ref([1, 2, 3])
</script>

<template>
  <button @click="l.push(Math.random())">
    Add a random number
  </button>
  <ul>
    <li
      v-for="item of l"
      :key="item"
    >
      {{ item }}
    </li>
  </ul>
</template>
```

```vue {1,16}
<!-- Une fonction pour supprimer un element -->
<script setup lang="ts">
import { ref } from 'vue';

const l = ref([1, 2, 3])
</script>

<template>
  <button @click="l.push(Math.random())">
    Add a random number
  </button>
  <ul>
    <li
      v-for="item of l"
      :key="item"
      @click="l = l.filter(i => i !== item)"
    >
      {{ item }}
    </li>
  </ul>
</template>
```
````

::right::

<p v-if="$clicks >= 1">
<List />
</p>

---

# ref, reactive, computed

- ref : pour créer une variable réactive
<v-click>
<ul>
<li>
reactive : comme ref mais pour les objets/tableaux, et pas besoin de .value
</li>
</ul>

```ts {monaco-run}
import { reactive } from 'vue'

const l = reactive([1,2,3])

l.push(4)
l.splice(1, 1);
console.log(l)

```
</v-click>

<v-click>
<ul>
<li>
computed : transforme une variable reactive, renvoie une ref non modifiable
</li>
</ul>

```ts {monaco-run}
import { ref, computed } from 'vue'

const n = ref(2)

const double = computed(() => n.value * 2)
console.log(double.value)
```
</v-click>

---

# Watchers

Executer un truc quand un truc change

```ts {monaco-run}
import { ref, watch } from 'vue'

const count = ref(0)

// setInterval(() => count.value++, 1000)

watch(count, (newCount) => {
  console.log(`new count is: ${newCount}`)
})
```

---

# Components

En général on les range dans un dossier 📁 components

```vue
<!-- /pages/index.vue -->
<script setup>
import Child from  '../components/Child.vue'
</script>

<template>
  <Child />
</template>
```

```vue
<!-- /components/Child.vue -->
<template>
  Child
</template>
```

---

# Props

Passer des trucs à Child.vue

```vue
<!-- /pages/index.vue -->
<script setup>
import Child from  '../components/Child.vue'
</script>

<template>
  <Child msg="coucou" />
</template>
```

```vue
<!-- /components/Child.vue -->
<script setup>
defineProps>({
  msg: String
})
</script>

<template>
  Child {{ msg }}
</template>
```

---

# Emits

Passer des trucs de Child.vue à index.vue

```vue
<!-- /pages/index.vue -->
<script setup>
import Child from  '../components/Child.vue'
</script>

<template>
  <Child @response="(msg) => console.log(msg)"/>
</template>
```

```vue
<!-- /components/Child.vue -->
<script setup>
defineEmits(['response'])
</script>

<template>
  <button @click="$emit('response', 'coucou')">
    Click to emit
  </button>
</template>
```

---

# Slots

Passer du html à Child.vue

```vue
<!-- /pages/index.vue -->
<script setup>
import Child from  '../components/Child.vue'
</script>

<template>
  <Child @response="(msg) => console.log(msg)">
    Hello from the other side
  </Child>
</template>
```

```vue
<!-- /components/Child.vue -->
<script setup>
defineEmits(['response'])
</script>

<template>
  <button @click="$emit('response', 'coucou')">
    <slot />
  </button>
</template>
```

---
layout: cover
background: https://banner2.cleanpng.com/20231213/eya/transparent-birthday-celebration-colorful-birthday-celebration-with-confetti-and-1710976214004.webp
---

# Bravo vous être maintenant un expert Vue 3
