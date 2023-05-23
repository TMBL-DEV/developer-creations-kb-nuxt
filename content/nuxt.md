---
title: 'KB - Nuxt (vue framework)'
description: 'knowledge base of developer-creations about nuxt the vue framework. This contains. Composables, routing, directories, modules and more'
---

# Nuxt (the vue framework)

---
Nuxt is one of the most popular frameworks. It is build upon vue and has many features to offer.

## The main Features

---

- Server side rendering (ssr)
- api routes
- rich module community
- directory / file based routing
- build in composables to use
- automatic imports
- automatic types from api routes

---

## Pro's of using nuxt over default vue

---

It is very simple default vue is good but building a website with multiple pages, api routes and server side rendering is not that easy
Thats where nuxt jumps in. It offers all those features and more, but with the ability to opt-out of the stuff that you dont want.<br><br>

  *You dont want multiple pages?* sure here you go only 1 app component without any routing for other pages.

*Dont want ssr?* just turn on client side rendering in the config.

*You want to deploy it with static files?* just update your config file <br><br>

As you might notice a lot of the default behaveiour is focussed on use cases that you might encounter building out your projects. As a company it mainly just saves time to use nuxt over vue. But not only does it save time, it also develops easier which means as a developer you will enjoy it more then writing basic vue projects (this is an opinionized take).

Besides it offers more functions out of the box than you can ever think of.

## Resources

---

### Links To resources

Here is a list of resoruces that you will definitly need:

1. [Nuxt modules](https://nuxt.com/modules/)
2. [Nuxt Docs](https://nuxt.com/docs)
3. [CLI Helper](https://nuxt.com/docs/api/commands/add)
4. [Nuxt Icons (Packs)](https://icones.js.org/)
5. [TailwindCss Nuxt module](https://tailwindcss.nuxtjs.org/getting-started/setup)

### Code Examples

#### Api routes

you register an api route in the `server/api` folder. Here You can for example make an
`server/api/hello-world.ts` this will goto route `https://your-domain/api/hello-world`.

In `server/api/hello-world.ts`

```ts{1,3-5}[hello-world.ts]
export default defineEventHandler((event) => {
  return {
    hello: 'world'
  }
});
```

And now in your vue component you can fetch the data.

```vue{1,3-5}[hello-world.vue]
<script setup>
const { data } = await useFetch('/api/hello')
</script>
<template>
  <pre>{{ data }}</pre>
</template>
```

Your Code editor will automaticly figure out that on the data object there is a hello property of type string. And the data variable is a Ref object, meaning that if you were to change the values in data the ui would automaticly update based on your changes.

Ofcourse this only works on your own api routes. So if you were to call a different server that the types would not be automaticly recognized.
