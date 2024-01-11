``` js

type Style = 'default' | 'dia' | 'primary'

type Size = '16' | '24' | '32' | '108'

  

defineProps({

size: {

type: String as PropType<Size>,

required: true

},

iconStyle: {

type: String as PropType<Style>

}

})

</script>

<template>

<svg

:class="iconStyle"

:width="size"

:height="size"

viewBox="0 0 16 17"

fill="none"

xmlns="http://www.w3.org/2000/svg"

>

<path

fill-rule="evenodd"

clip-rule="evenodd"

d="M14 7.25C13.5858 7.25 13.25 6.91421 13.25 6.5V3.83333C13.25 3.67862 13.1885 3.53025 13.0791 3.42086C12.9697 3.31146 12.8214 3.25 12.6667 3.25L3.33333 3.25C3.17862 3.25 3.03025 3.31146 2.92085 3.42085C2.81146 3.53025 2.75 3.67862 2.75 3.83333L2.75 6.5C2.75 6.91421 2.41421 7.25 2 7.25C1.58579 7.25 1.25 6.91421 1.25 6.5V3.83333C1.25 3.2808 1.46949 2.75089 1.86019 2.36019C2.25089 1.96949 2.7808 1.75 3.33333 1.75H12.6667C13.2192 1.75 13.7491 1.96949 14.1398 2.3602C14.5305 2.7509 14.75 3.2808 14.75 3.83333V6.5C14.75 6.91421 14.4142 7.25 14 7.25ZM11.8637 10.3636C11.5708 10.6565 11.0959 10.6565 10.803 10.3636L8.75 8.31058L8.75 14.5C8.75 14.9142 8.41421 15.25 8 15.25C7.58579 15.25 7.25 14.9142 7.25 14.5L7.25 8.31058L5.197 10.3636C4.9041 10.6565 4.42923 10.6565 4.13634 10.3636C3.84344 10.0707 3.84344 9.59582 4.13634 9.30292L7.46967 5.96959C7.76256 5.6767 8.23744 5.6767 8.53033 5.96959L11.8637 9.30292C12.1566 9.59582 12.1566 10.0707 11.8637 10.3636Z"

fill="white"

/>

</svg>

</template>

<style lang="sass" scoped>

svg

path

fill: $primary

  

&.dia

path

fill: $white

</style>
```



**VB-402**

- Merging to **Development** branch
- DD-231-Typescript ticket
- PRs pending


Drop a message about PR estimate





