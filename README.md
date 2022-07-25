# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)

# Declarative in nature/ enable declarative rendering :
{{}} - > Mustache operation
for instance :
<div> {{ render your JS statement }}</div>

# Reactive Natire :
Allows realtime update / render upon change

# Single File Component
- has an extension of .vue
- encanspulates / bundles together the logic, template and style into a single file to now what is know as a component. Hence the name 'Single File Component'

#Method to use when authorising your Single File Component :
- Options API
- Composition API

# Create  a new branch name it develop
'git branch develop'
- git add .
- git commit -m "New branch added"
- git push
# Project Details :
 Functionality : 
 -> Display Two items for sale
 -> Add feature to "Add to Cart"
 -> Calculate the total price : "Total price"
 ->Add more items to cart ( increment the item quantity plus one)
 -> Event ( mousehover and onclick)

# Common Decalartives  : 
preceded by the term "v-"
- v-for // when having lists m, we can loop through the list and acces all elements using the v-for declarative

- v-bind // allows one to bind logic/ JS features to your DOM Element

- v-on // it checks for events and acts upon the defines or target event ->  you explicitly define your event eg. mouse-hover, click, scroll

- v-if // conditional, use when you would like to ascertain a particular condition has been met

- v-else-if // consditional decalarative that allows your to combine your expression / condition  eg islight === true && isPerson === false

- v-show // conditional rendering, you can display an image only if a particular condition has been met  -> is more preferred approach as oppposed to the v-if 