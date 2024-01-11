# table select
<script lang="ts" setup>

import { ref, computed, type PropType } from 'vue'

  

import InputTextControl from '@/components/molecules/form/inputControls/InputTextControl.vue'

import ConfirmModal from "@/components/molecules/list/ConfirmModal.vue"

import CoreButton from '../form/buttons/CoreButton.vue'

import { type StatusOptions,type DropdownOptions } from '@/types/form'

import type { Item } from "vue3-easy-data-table"

  

type Size = 'small'

type InputType = 'default' | 'search'

type InputStyle = 'table'

// type Status = null | 'disabled' | 'validated' | 'error' | 'warning'

  

const props = defineProps({

id: {

type: String

},

options: {

type: Array as PropType<DropdownOptions[]>,

required: true

},

selectedOption: {

type: String,

requied: true

},

hasOptionIcon: {

type: Boolean,

},

type: {

type: String as PropType<InputType>,

default: 'default'

},

// status: {

// type: String as PropType<Status>

// },

size: {

type: String as PropType<Size>

},

name: {

type: String

},

placeholder: {

type: String

},

  

inputStyle: {

type: String as PropType<InputStyle>,

default:'table'

},

modelValue: {}

})

  

const emit = defineEmits(['dropdown-select', 'dropdown'])

  

const currentOption = ref<String>()

const showDropdown = ref<boolean>(false)

  

const closeDropdown = () => {

showDropdown.value = false

}

  

const showStatusChangeModal = ref<boolean>(false);

  

const onConfirmStatusChange = (option: String) => {

emit('dropdown-select', option)

closeModal()

};

  

const isOptionDisabled = (option: DropdownOptions): boolean => {

return option.disabled || false

}

  

const closeModal = () => {

showStatusChangeModal.value = false;

};

  

const selectOption = (option? : String) => {

console.log(option)

// if(option){

currentOption.value = option

console.log(currentOption.value)

showStatusChangeModal.value = true;

// }

}

  

// const selectedOptionvalue = computed(() => {

// if (props.selectedOption && props.selectedOption.length > 0) {

// const firstOption = props.selectedOption[0];

// if (firstOption.status === 'active') {

// return 'Active';

// } else if (firstOption.status === 'inactive') {

// return 'Inactive';

// }

// }

// return 'Not Verified';

// });

</script>

  

<template>

<div v-click-away="closeDropdown" class="dropdown">

<InputTextControl

id="dropdownControl"

:class="[

'dropdown__control',

`dropdown__control-style--${inputStyle}`,

`dropdown__control--${type}`,

{ 'dropdown__control--dropdown-active': showDropdown && type === 'default' },

{ 'dropdown__control--disabled': isOptionDisabled }

]"

:value="props.selectedOption == 'active' ? 'Active' : selectedOption== 'inactive' ? 'Inactive' : 'Not Verified'"

:placeholder="placeholder"

:readonly="type === 'default' ? true : false"

@focus="() => (type === 'search' ? (showDropdown = true) : null)"

@click="() => (type === 'default' ? (showDropdown = !showDropdown) : null)"

/>

<div v-if="showDropdown" class="dropdown__dropdown" >

<label

v-for="option in options"

:key="option.id"

:class="['dropdown__option', { 'dropdown__option--disabled': option.disabled }, `dropdown__option--${inputStyle}`]"

@click="selectOption(option.value)"

>

<div class="dropdown__option-row">

<div

v-if="hasOptionIcon"

class="dropdown__option-icon"

:style="{ backgroundImage: `url(${option.icon})` }"

></div>

<p :class="['dropdown__option-text', { 'dropdown__option-text--disabled': option.disabled }]">

{{ option.label }}

</p>

</div>

</label>

</div>

<Teleport to="body">

<ConfirmModal

:isModalVisible="showStatusChangeModal"

@cancel="closeModal"

v-if="currentOption"

>

<template #header>

Are you sure you want to change status?

</template>

<template #actions>

<CoreButton @click="onConfirmStatusChange(currentOption)" text="Confirm" buttonColor="primary">Confirm</CoreButton>

<CoreButton @click="closeModal" text="Cancel" buttonColor="secondary">Cancel</CoreButton>

</template>

</ConfirmModal>

</Teleport>

</div>

</template>

  

<style lang="sass">

.dropdown

width: auto

position: relative

&__control

cursor: pointer

background-position-y: 50%

background-repeat: no-repeat

-moz-appearance: none

-webkit-appearance: none

  

&--status

border: 0.1rem solid $primary

color: $primary

font-size: 1.4rem

  

&--disabled

color: $disabled

  

&--default

background-position-x: calc(100% - 1.2rem)

background-image: url("data:image/svg+xml;utf8,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 6L8 10L12 6' stroke='%230E1E36' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&--dropdown-active

background-image: url("data:image/svg+xml;utf8,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 10L8 6L12 10' stroke='%230E1E36' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&--search

padding-left: calc(1.2rem + 1.6rem + 0.8rem)

background-position-x: 1.2rem

background-image: url("data:image/svg+xml;utf8,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='6.4' cy='6.4' r='3.65' stroke='%236E7886' stroke-width='1.5'/%3E%3Cpath d='M9.19971 9.19971L13.9997 13.9997' stroke='%236E7886' stroke-width='1.5' stroke-linecap='round'/%3E%3C/svg%3E%0A")

&-style

&--filter

width: 13rem

height: 3.5rem

color: $primary

background-position-x: calc(100% - 1.2rem)

background-size: 1rem 1rem

background-image: url("data:image/svg+xml;utf8,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 6L8 10L12 6' stroke='%230E1E36' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&__dropdown

width: 100%

position: absolute

z-index: 1 !important

top: calc(100% + -0.1rem)

border-radius: 0.2rem

border: 0.1rem solid $primary

background: red

  

&__option

background-color: $white

padding: 0.8rem 1.2rem

display: flex

align-items: center

justify-content: space-between

height: 3.4rem

cursor: pointer

  

&--filter

.dropdown__option-text

font-size: 1.2rem

color: $black

  

&--disabled

pointer-events: none

  

&-icon

width: 2.4rem

height: 2.4rem

border-radius: 50%

background-size: cover

background-position: center

background-repeat: no-repeat

  

&-text

@include paragraph-01

color: $primary

  

&--disabled

color: $disabled

  

&-row

display: flex

align-items: center

gap: 0.8rem

  

.input-control

&__container

display: flex

align-items: center

  

&__checkbox

display: none

  

&__custom-checkbox

height: 1.6rem

width: 1.6rem

border-radius: 0.2rem

border: 0.1rem solid $black

cursor: pointer

transition: all 0.2s ease

transition-property: border, background-color

  

&::after

content: ""

width: 100%

height: 100%

background-size: 100%

background-repeat: no-repeat

background-position: center 90%

background-image: url("data:image/svg+xml,%3Csvg width='14' height='12' viewBox='0 0 14 12' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cg filter='url(%23filter0_d_2952_2129)'%3E%3Cpath d='M4 5L6 7L10 3' stroke='%23EEF0F8'/%3E%3C/g%3E%3Cdefs%3E%3Cfilter id='filter0_d_2952_2129' x='0.737355' y='0.319212' width='12.5253' height='10.8787' filterUnits='userSpaceOnUse' color-interpolation-filters='sRGB'%3E%3CfeFlood flood-opacity='0' result='BackgroundImageFix'/%3E%3CfeColorMatrix in='SourceAlpha' type='matrix' values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0' result='hardAlpha'/%3E%3CfeOffset dy='0.581818'/%3E%3CfeGaussianBlur stdDeviation='1.45455'/%3E%3CfeColorMatrix type='matrix' values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0'/%3E%3CfeBlend mode='normal' in2='BackgroundImageFix' result='effect1_dropShadow_2952_2129'/%3E%3CfeBlend mode='normal' in='SourceGraphic' in2='effect1_dropShadow_2952_2129' result='shape'/%3E%3C/filter%3E%3C/defs%3E%3C/svg%3E")

display: none

  

&__checkbox:checked ~ &__custom-checkbox

background-color: $primary

border-color: $primary

  

&__checkbox:checked ~ &__custom-checkbox::after

display: block

</style>
# input dropdown select


``` vue
<script lang="ts" setup>

import { ref, computed,type Ref } from 'vue'

import type { PropType } from 'vue'

import InputTextControl from "@/components/molecules/form/inputControls/InputTextControl.vue"

import { type DropdownOptions } from '@/types/form'

  

type Size = 'small' | 'default'

type InputType = 'default' | 'search'

type InputStyle = 'default' | 'filter' | 'formTag'

type Status = null | 'disabled' | 'validated' | 'error' | 'warning'

  

const props = defineProps({

id: {

type: String

},

options: {

type: Array as PropType<DropdownOptions[]>,

required: true,

},

selectedOption: {

type: Array as PropType<DropdownOptions[]>,

},

hasOptionIcon: {

type: Boolean,

default: true

},

type: {

type: String as PropType<InputType>,

default: 'default'

},

status: {

type: String as PropType<Status>

},

size: {

type: String as PropType<Size>

},

name: {

type: String

},

placeholder: {

type: String

},

inputStyle: {

type: String as PropType<InputStyle>,

default: 'default'

},

modelValue: {}

})

  

const emit = defineEmits(['select', 'dropdown'])

  

const showDropdown = ref<Boolean>(false)

  

const closeDropdown = () => {

showDropdown.value = false

}

  

const isOptionDisabled = (option: DropdownOptions): boolean => {

return option.disabled || false

}

const selectOption = (option: DropdownOptions) => {

emit('select', option)

showDropdown.value = false

}

  

const selectedOptionvalue = computed((): String | undefined => {

console.log(props.selectedOption)

if (props.selectedOption && props.selectedOption.length > 0) {

const firstDropdownOption: DropdownOptions = props.selectedOption[0];

if (firstDropdownOption.status === 'active') {

return 'Active';

} else if (firstDropdownOption.status === 'inactive') {

return 'Inactive';

} else if (firstDropdownOption.status === 'notVerified') {

return 'Not Verified';

}

}

return undefined;

});

</script>

  

<template>

<div v-click-away="closeDropdown" class="dropdown">

<InputTextControl

id="dropdownControl"

:status="status"

:class="[

'dropdown__control',

`dropdown__control-style--${inputStyle}`,

`dropdown__control--${type}`,

{ 'dropdown__control--dropdown-active': showDropdown && type === 'default' },

{ 'dropdown__control--disabled': isOptionDisabled }

]"

:border="inputStyle == 'filter' ? false : true"

:value="selectedOptionvalue"

:placeholder="placeholder"

:readonly="type === 'default' ? true : false"

@focus="() => (type === 'search' ? (showDropdown = true) : null)"

@click="() => (type === 'default' ? (showDropdown = !showDropdown) : null)"

/>

<div v-if="showDropdown" class="dropdown__dropdown">

<label

v-for="option in options"

:key="option?.id"

:class="['dropdown__option', { 'dropdown__option--disabled': option?.disabled }, `dropdown__option--${inputStyle}`]"

@click="selectOption(option)"

>

<div class="dropdown__option-row">

<div

v-if="hasOptionIcon"

class="dropdown__option-icon"

:style="{ backgroundImage: `url(${option?.icon})` }"

></div>

<p :class="['dropdown__option-text', { 'dropdown__option-text--disabled': option?.disabled }]">

{{ option?.label }}

</p>

</div>

</label>

</div>

</div>

</template>

  

<style lang="sass" scoped>

.dropdown

width: auto

position: relative

  

&__control

cursor: pointer

background-position-y: 50%

background-repeat: no-repeat

-moz-appearance: none

-webkit-appearance: none

  

&--status

border: 0.1rem solid $primary

color: $primary

font-size: 1.4rem

  

&--disabled

color: $disabled

&--default

background-position-x: calc(100% - 1.2rem)

background-image: url("data:image/svg+xml;utf8,%3Csvg width='14' height='14' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 6L8 10L12 6' stroke='%2382868C' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&--dropdown-active

background-image: url("data:image/svg+xml;utf8,%3Csvg width='14' height='14' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 10L8 6L12 10' stroke='%2382868C' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&--search

padding-left: calc(1.2rem + 1.6rem + 0.8rem)

background-position-x: 1.2rem

background-image: url("data:image/svg+xml;utf8,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='6.4' cy='6.4' r='3.65' stroke='%236E7886' stroke-width='1.5'/%3E%3Cpath d='M9.19971 9.19971L13.9997 13.9997' stroke='%236E7886' stroke-width='1.5' stroke-linecap='round'/%3E%3C/svg%3E%0A")

&-style

&--filter

padding: 0.8rem

max-width: 13rem

border: 0.1rem solid $primary

color: $primary

box-shadow:0.1rem 0.5rem 0.6rem -0.1rem rgba(0, 0, 0, 0.25)

&::placeholder

color: $primary

&--formTag

border: none

  

&__dropdown

width: 100%

position: absolute

z-index: 10

top: calc(100% + -0.1rem)

border-radius: 0.4rem

border: 0.1rem solid $primary

z-index: 10

background-color: $white

  

&__option

padding: 0.4rem 1.2rem

display: flex

align-items: center

justify-content: space-between

cursor: pointer

color: $primary

&:hover

background-color: $primary

color: $white

.dropdown__option-text

color: $white

&--filter

.dropdown__option-text

font-size: 1.2rem

color: $primary

  

&--disabled

pointer-events: none

color: $disabled

opacity: 0.5

  

&-icon

width: 2.4rem

height: 2.4rem

border-radius: 50%

background-size: cover

background-position: center

background-repeat: no-repeat

&-text

@include paragraph-01

color: $primary

&--disabled

color: $placeholderText

&-row

display: flex

align-items: center

gap: 0.8rem

  
  

.input-control

&__container

display: flex

align-items: center

  

&__checkbox

display: none

  

&__custom-checkbox

height: 1.6rem

width: 1.6rem

border-radius: 0.2rem

border: 0.1rem solid $borderLight

cursor: pointer

transition: all 0.2s ease

transition-property: border, background-color

  

&::after

content: ""

width: 100%

height: 100%

background-size: 100%

background-repeat: no-repeat

background-position: center 90%

background-image: url("data:image/svg+xml,%3Csvg width='14' height='12' viewBox='0 0 14 12' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cg filter='url(%23filter0_d_2952_2129)'%3E%3Cpath d='M4 5L6 7L10 3' stroke='%23EEF0F8'/%3E%3C/g%3E%3Cdefs%3E%3Cfilter id='filter0_d_2952_2129' x='0.737355' y='0.319212' width='12.5253' height='10.8787' filterUnits='userSpaceOnUse' color-interpolation-filters='sRGB'%3E%3CfeFlood flood-opacity='0' result='BackgroundImageFix'/%3E%3CfeColorMatrix in='SourceAlpha' type='matrix' values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0' result='hardAlpha'/%3E%3CfeOffset dy='0.581818'/%3E%3CfeGaussianBlur stdDeviation='1.45455'/%3E%3CfeColorMatrix type='matrix' values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0'/%3E%3CfeBlend mode='normal' in2='BackgroundImageFix' result='effect1_dropShadow_2952_2129'/%3E%3CfeBlend mode='normal' in='SourceGraphic' in2='effect1_dropShadow_2952_2129' result='shape'/%3E%3C/filter%3E%3C/defs%3E%3C/svg%3E")

display: none

  

&__checkbox:checked ~ &__custom-checkbox

background-color: $primary

border-color: $primary

&__checkbox:checked ~ &__custom-checkbox::after

display: block

</style>
``` vue
<script lang="ts" setup>

import { ref, computed,type Ref } from 'vue'

import type { PropType } from 'vue'

import InputTextControl from "@/components/molecules/form/inputControls/InputTextControl.vue"

import { type DropdownOptions } from '@/types/form'

  

type Size = 'small' | 'default'

type InputType = 'default' | 'search'

type InputStyle = 'default' | 'filter' | 'formTag'

type Status = null | 'disabled' | 'validated' | 'error' | 'warning'

  

const props = defineProps({

id: {

type: String

},

options: {

type: Array as PropType<DropdownOptions[]>,

required: true,

},

selectedOption: {

type: Array as PropType<DropdownOptions[]>,

},

hasOptionIcon: {

type: Boolean,

default: true

},

type: {

type: String as PropType<InputType>,

default: 'default'

},

status: {

type: String as PropType<Status>

},

size: {

type: String as PropType<Size>

},

name: {

type: String

},

placeholder: {

type: String

},

inputStyle: {

type: String as PropType<InputStyle>,

default: 'default'

},

modelValue: {}

})

  

const emit = defineEmits(['select', 'dropdown'])

  

const showDropdown = ref<Boolean>(false)

  

const closeDropdown = () => {

showDropdown.value = false

}

  

const isOptionDisabled = (option: DropdownOptions): boolean => {

return option.disabled || false

}

const selectOption = (option: DropdownOptions) => {

emit('select', option)

showDropdown.value = false

}

  

const selectedOptionvalue = computed((): String | undefined => {

console.log(props.selectedOption)

if (props.selectedOption && props.selectedOption.length > 0) {

const firstDropdownOption: DropdownOptions = props.selectedOption[0];

if (firstDropdownOption.status === 'active') {

return 'Active';

} else if (firstDropdownOption.status === 'inactive') {

return 'Inactive';

} else if (firstDropdownOption.status === 'notVerified') {

return 'Not Verified';

}

}

return undefined;

});

</script>

  

<template>

<div v-click-away="closeDropdown" class="dropdown">

<InputTextControl

id="dropdownControl"

:status="status"

:class="[

'dropdown__control',

`dropdown__control-style--${inputStyle}`,

`dropdown__control--${type}`,

{ 'dropdown__control--dropdown-active': showDropdown && type === 'default' },

{ 'dropdown__control--disabled': isOptionDisabled }

]"

:border="inputStyle == 'filter' ? false : true"

:value="selectedOptionvalue"

:placeholder="placeholder"

:readonly="type === 'default' ? true : false"

@focus="() => (type === 'search' ? (showDropdown = true) : null)"

@click="() => (type === 'default' ? (showDropdown = !showDropdown) : null)"

/>

<div v-if="showDropdown" class="dropdown__dropdown">

<label

v-for="option in options"

:key="option?.id"

:class="['dropdown__option', { 'dropdown__option--disabled': option?.disabled }, `dropdown__option--${inputStyle}`]"

@click="selectOption(option)"

>

<div class="dropdown__option-row">

<div

v-if="hasOptionIcon"

class="dropdown__option-icon"

:style="{ backgroundImage: `url(${option?.icon})` }"

></div>

<p :class="['dropdown__option-text', { 'dropdown__option-text--disabled': option?.disabled }]">

{{ option?.label }}

</p>

</div>

</label>

</div>

</div>

</template>

  

<style lang="sass" scoped>

.dropdown

width: auto

position: relative

  

&__control

cursor: pointer

background-position-y: 50%

background-repeat: no-repeat

-moz-appearance: none

-webkit-appearance: none

  

&--status

border: 0.1rem solid $primary

color: $primary

font-size: 1.4rem

  

&--disabled

color: $disabled

&--default

background-position-x: calc(100% - 1.2rem)

background-image: url("data:image/svg+xml;utf8,%3Csvg width='14' height='14' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 6L8 10L12 6' stroke='%2382868C' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&--dropdown-active

background-image: url("data:image/svg+xml;utf8,%3Csvg width='14' height='14' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 10L8 6L12 10' stroke='%2382868C' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E%0A")

  

&--search

padding-left: calc(1.2rem + 1.6rem + 0.8rem)

background-position-x: 1.2rem

background-image: url("data:image/svg+xml;utf8,%3Csvg width='16' height='16' viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='6.4' cy='6.4' r='3.65' stroke='%236E7886' stroke-width='1.5'/%3E%3Cpath d='M9.19971 9.19971L13.9997 13.9997' stroke='%236E7886' stroke-width='1.5' stroke-linecap='round'/%3E%3C/svg%3E%0A")

&-style

&--filter

padding: 0.8rem

max-width: 13rem

border: 0.1rem solid $primary

color: $primary

box-shadow:0.1rem 0.5rem 0.6rem -0.1rem rgba(0, 0, 0, 0.25)

&::placeholder

color: $primary

&--formTag

border: none

  

&__dropdown

width: 100%

position: absolute

z-index: 10

top: calc(100% + -0.1rem)

border-radius: 0.4rem

border: 0.1rem solid $primary

z-index: 10

background-color: $white

  

&__option

padding: 0.4rem 1.2rem

display: flex

align-items: center

justify-content: space-between

cursor: pointer

color: $primary

&:hover

background-color: $primary

color: $white

.dropdown__option-text

color: $white

&--filter

.dropdown__option-text

font-size: 1.2rem

color: $primary

  

&--disabled

pointer-events: none

color: $disabled

opacity: 0.5

  

&-icon

width: 2.4rem

height: 2.4rem

border-radius: 50%

background-size: cover

background-position: center

background-repeat: no-repeat

&-text

@include paragraph-01

color: $primary

&--disabled

color: $placeholderText

&-row

display: flex

align-items: center

gap: 0.8rem

  
  

.input-control

&__container

display: flex

align-items: center

  

&__checkbox

display: none

  

&__custom-checkbox

height: 1.6rem

width: 1.6rem

border-radius: 0.2rem

border: 0.1rem solid $borderLight

cursor: pointer

transition: all 0.2s ease

transition-property: border, background-color

  

&::after

content: ""

width: 100%

height: 100%

background-size: 100%

background-repeat: no-repeat

background-position: center 90%

background-image: url("data:image/svg+xml,%3Csvg width='14' height='12' viewBox='0 0 14 12' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cg filter='url(%23filter0_d_2952_2129)'%3E%3Cpath d='M4 5L6 7L10 3' stroke='%23EEF0F8'/%3E%3C/g%3E%3Cdefs%3E%3Cfilter id='filter0_d_2952_2129' x='0.737355' y='0.319212' width='12.5253' height='10.8787' filterUnits='userSpaceOnUse' color-interpolation-filters='sRGB'%3E%3CfeFlood flood-opacity='0' result='BackgroundImageFix'/%3E%3CfeColorMatrix in='SourceAlpha' type='matrix' values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0' result='hardAlpha'/%3E%3CfeOffset dy='0.581818'/%3E%3CfeGaussianBlur stdDeviation='1.45455'/%3E%3CfeColorMatrix type='matrix' values='0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.1 0'/%3E%3CfeBlend mode='normal' in2='BackgroundImageFix' result='effect1_dropShadow_2952_2129'/%3E%3CfeBlend mode='normal' in='SourceGraphic' in2='effect1_dropShadow_2952_2129' result='shape'/%3E%3C/filter%3E%3C/defs%3E%3C/svg%3E")

display: none

  

&__checkbox:checked ~ &__custom-checkbox

background-color: $primary

border-color: $primary

&__checkbox:checked ~ &__custom-checkbox::after

display: block

</style>
```

