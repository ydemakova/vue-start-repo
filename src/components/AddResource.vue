<template>
   <form @submit.prevent="addResource">
    <base-dialog v-if="inputIsInvalid" @close="confirmError" title="Invalid Input">
      <template #default>
       <p>Unfortunately, at least one input is invalid.</p>
       <p>Please check all inpunts and make sure you enter valid values</p>
      </template>
      <template #actions>
      <base-button @click="confirmError">Okay</base-button>
      </template>
</base-dialog>
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
import BaseDialog from './UI/BaseDialog.vue'
    export default{
  components: { BaseDialog },
     emits: ['add-new-resource'],
     data() {
    return {
        inputIsInvalid: false
    }
     },
     methods: {
        addResource(){

            const enteredTitle = this.$refs.title.value
            const enteredDescription = this.$refs.description.value
            const enteredLink = this.$refs.link.value

            if (enteredTitle.trim() === '' || enteredDescription.trim() === '' || enteredLink.trim() === '' ) {
                this.inputIsInvalid = true
                return
            }

            this.$emit('add-new-resource', enteredTitle, enteredDescription, enteredLink)

        },
        confirmError() {
            this.inputIsInvalid = false
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
