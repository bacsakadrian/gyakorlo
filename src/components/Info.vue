<template>
    <button class="gomb" design scoped @click="figyelmeztet" type="button">Első gomb</button>
    <button class="gomb" design betustilus @click="reset" type="button">Második gomb</button>
</template>

<script>
    export default {
    name: 'Info',

    props: {
        num : Number
    },

    methods: {
        figyelmeztet() {
            alert(this.num)
        },
        reset() {
            this.$emit('myEvent')
        }
    }
    }
</script>

<style>
.gomb[design] {
  color: red;
  background-color: black
}

.gomb[betustilus] {
    border-style: dotted
}
</style>