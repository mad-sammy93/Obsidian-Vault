### Url : 
[http://localhost:5002/project/add](http://localhost:5002/project/add)

#### References:

[https://byby.dev/](https://byby.dev/)

#### New Components: 
- [x] Tag dropdown [inputformtagcontrol.vue]
- [x] toggle conteol [inputToggleControl]
- [ ] sadsad
- [ ] dsadsadsadsad
- [ ] Url input with tag 

## Notes

```
<!-- <form @submit.prevent="fetchMetaTitle">

<input v-model="url_link" placeholder="Enter URL">

<button type="submit">Fetch Title</button>

<p>{{ title }}<p></p> {{ favicon }}</p>

</form>

<img src="{{ favicon }}" alt=""> -->
```


script
```
  

// ----------------------------

  
  

const url_link = ref('');

const title = ref('Title not found')

const favicon = ref();

  

const fetchMetaTitle = async () => {

try {

const response = await fetch( url_link.value , {

method: "GET",

mode: "no-cors",

credentials: "include",

headers: {

"Content-Type": "application/json"

},

body: null

},

);

  

// console.log(response)

if (response.ok) {

const html = await response.text();

const titleInfo = extractTitleFromHTML(html);

title.value = titleInfo.title;

favicon.value = titleInfo.favicon;

console.log(titleInfo)

} else {

title.value = 'Error fetching info';

favicon.value = null;

}

} catch (error) {

title.value = 'An error occurred';

favicon.value = null;

}

}

  

const extractTitleFromHTML = (html:any) => {

const matchTitle = /<title[^>]*>([^<]*)<\/title>/i.exec(html);

const title = matchTitle && matchTitle[1] ? matchTitle[1] : 'Title not found';

  

const matchFavicon = /<link[^>]*rel="icon"[^>]*href="([^"]+)"/i.exec(html);

const favicon = matchFavicon && matchFavicon[1] ? matchFavicon[1] : null;

  

return { title, favicon };

}
```




```<md>
<InputControlWrapper id="addProject-projectUrl" label="Project URL" inputStyle="inner-form"

:status="errorExist('projectUrl')" :status-message="fieldErrors('projectUrl')">

<template #control="slotProps">

<div>

<InputTextControl id="addProject-website" class="addProject-form__input-control"

placeholder="Project URL" :status="slotProps.status" name="website"

v-model="addProjectDetails.projectUrl"></InputTextControl>

</div>

<!-- TODO Add multiple url options -->

</template>

</InputControlWrapper>
```