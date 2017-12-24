<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>Username: {{ switchName() }} </p>
        <button @click="resetName()">Reset name</button>
        <button @click="call()">Call Anna</button>
    </div>
</template>

<script>
  export default {
    props: {
      name: {
        type: String,
        required: true
      },
      call: {
        type: Function
      }
    },
    methods: {
      switchName(){
        return this.name.split("").reverse().join("");
      },
      resetName(){
        this.name = "Max";
        this.$emit('nameWasReset', this.name);
      }
    }
  }
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
