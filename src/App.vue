
<template>
    <the-header title="RememberMe"></the-header>
    <add-resource @add-new-resource="addResource"></add-resource>
 <ul>
   <resource-item v-for="resource in storedResources" @delete-resource="deleteResource" :key="resource.id" :title="resource.title" :description="resource.description" :link="resource.link"/>
 </ul>
</template>

<script>
    import ResourceItem from './components/ResourceItem.vue'
    import TheHeader from './components/layout/TheHeader.vue'
    import AddResource from './components/AddResource.vue'
    export default{
    components:{
        ResourceItem,
        TheHeader,
        AddResource
    },
      data(){
        return{
            storedResources: [ {
                id: 'official-guide',
                title: 'Official Guide',
                description:'The official Vue.js documentation',
                link: "https://vuejs.org"
            },
            {
                id: 'google',
                title: 'Google',
                description:'Learn to google',
                link: "https://google.org"
            }
        ]
        }
      },
      methods: {
        addResource(title, description, link) {
            const newResource = {
                id: title,
                title,
                description,
                link
            }
            this.storedResources.unshift(newResource)

        },
        deleteResource(resourceID) {

          const resourceIndex = this.storedResources.findIndex( res => res.id === resourceID)
          this.storedResources.splice(resourceIndex, 1)

        }

      }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

    * {
      box-sizing: border-box;
    }

    html {
      font-family: 'Roboto', sans-serif;
    }

    body {
      margin: 0;
    }


    </style>
