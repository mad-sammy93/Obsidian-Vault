


```
  

type Size = '14' | '16' | '20' | '22' | '24'
defineProps({

	size: {
	
		type: String as PropType<Size>,
		default: '14'
	},
	color: {
		
		type: String,
		
		required: false,
		
		default: "white",
	
	},
	theme: {
	
		type: String as PropType< 'primary' | 'light' | 'dark' | 'red' | 'grey'>,
		
		default: 'light'
	
	}

});
```



```
<script lang="ts" setup>

import type { PropType } from 'vue'

  

type Size = '14' | '16' | '20' | '22' | '24'

defineProps({

size: {

type: String as PropType<Size>,

default: '14'

},

theme: {

type: String as PropType< 'primary' | 'light' | 'red' | 'grey'>,

default: 'light'

}

});

</script>

<template>

<svg :width="size" :height="size" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">

<circle :class="['fill', theme]" cx="8" cy="8" r="8" />

<path :class="['stroke', theme]" d="M5 5L11 11" stroke-width="1.5" />

<path :class="['stroke', theme]" d="M11 5L5 11" stroke-width="1.5" />

</svg>

</template>

  

<style lang="sass" scoped>

svg

cursor: pointer

position: absolute

left: -2rem

  

.fill

&.light

fill: $secondary

  

&.dark

fill: $secondaryDark

&.red

fill: $white

.stroke

&.light

stroke: $secondaryLight

&.dark

stroke: $primary

&.red

stroke: $error

</style>
```


```
type Size = '14' | '16' | '20' | '22' | '24'

  

defineProps({

size: {

type: String as PropType<Size>,

default: '14'

},

color: {

type: String,

default: "white",

},

});
```