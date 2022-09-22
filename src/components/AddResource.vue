<template>
   <form @submit="addResource">
    <base-card>
     <div class="form-field">
        <label for="">Title: </label>
        <input type="text" ref="title">
     </div>
     <div class="form-field">
        <label for="">Description: </label>
        <textarea type="text" ref="description"></textarea>
     </div>
     <div class="form-field">
        <label for="">Link: </label>
        <input type="text" ref="link">
     </div>
     <base-button type="submit">Add resource</base-button>
    </base-card>
   </form>
</template>

<script>
    export default{
     emits: ['add-new-resource'],

     methods: {
        addResource(){
            this.$emit('add-new-resource', this.$refs.title.value, this.$refs.description.value, this.$refs.link.value)
        }
     }
    }
</script>




<style scoped>
    label {
      font-weight: bold;
      display: block;
      margin-bottom: 0.5rem;
    }

    input,
    textarea {
      display: block;
      width: 100%;
      font: inherit;
      padding: 0.15rem;
      margin-bottom: 2rem;
      border: 1px solid #ccc;
    }

    input:focus,
    textarea:focus {
      outline: none;
      border-color: #3a0061;
      background-color: #f7ebff;
    }

    </style>