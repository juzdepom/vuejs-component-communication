<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>Username: {{ switchName() }} </p>
        <p> User age: {{ userAge }}</p>
        <button @click="resetName()">Reset name (send event to parent)</button>
        <button @click="call()">Call Anna (prop function)</button>
    </div>
</template>

<script>
  import { eventBus } from '../main';

  export default {
    props: {
      name: {
        type: String,
        required: true
      },
      call: Function,
      userAge: Number,
    },
    methods: {
      switchName(){
        return this.name.split("").reverse().join("");
      },
      resetName(){
        this.name = "Max";
        this.$emit('nameWasReset', this.name);
      }
    },
    created() {
        eventBus.$on('ageWasEdited', (age) => {
        this.userAge = age;
      });
    }
  }
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
