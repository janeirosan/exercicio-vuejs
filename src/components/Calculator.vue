<script setup>
    import { reactive } from 'vue';
    
    const num1 = defineModel('num1');
    const num2 = defineModel('num2');

    const operations = [{
        name: 'Select operation',
        value: ''
    },{
        name:'addition',
        value: addNum()
    },{
        name:'subtraction',
        value: subNum()
    },{
        name:'multiplication',
        value: multNum()
    },{
        name:'division',
        value: divNum()
    }];

    function addNum() {
    num1 + num2
    }

    function subNum() {
    num1 - num2
    }

    function multNum() {
    num1 * num2
    }

    function divNum() {
    num1 / num2
    }
</script>

<template>
    <div class="container">
    <header class="p-5 my-4 bg-light rounded-3">
        <h1 class="display-1">Calculator I guess 🙄</h1>
        <p class="lead">
        why math of all things
        </p>
    </header>
    <form class="mx-5 mb-5">
        <div class="row rounded-2">
        <div class="col-10">
            <div class="input-group input-group-lg">
            <input type="number" class="form-control" placeholder="Input number here" v-model.number="num1">
            <input type="number" class="form-control" placeholder="Input number here" v-model.number="num2">
            <select class="form-select text-capitalize" :value="select" @change="event => operations.value = event.target.selected">
                <option v-for="operation in operations">{{ operation.name }}</option>
            </select>
            </div>
        </div>
        </div>
    </form>
    <hr class="border border-dark-subtle col-5 mx-auto">
    <div class="container bg-info-subtle p-5 my-2 rounded-3">
        <h1 class="display-1 text-center">
        <span v-for="operation in operations">{{ operation.value[v-model] }}</span>
        </h1>
    </div>
    </div>
</template>

<style scoped>
    input[type=number] {
    -moz-appearance:textfield;
    appearance:textfield;
    }
</style>
