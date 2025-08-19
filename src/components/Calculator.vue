<script setup>
    import { ref } from 'vue'
    const num1 = defineModel('num1');
    const num2 = defineModel('num2');
    const result = ref('penis jade');
    const selectedOp = ref('Select Operation');

    const operations = ['addition', 'subtraction', 'multiplication', 'division'];
    // delete value later

    function addNum() {
    return num1.value + num2.value
    }

    function subNum() {
    return num1.value - num2.value
    }

    function multNum() {
    return num1.value * num2.value
    }

    function divNum() {
    return num1.value / num2.value
    }

    function maths() {
        // let operation = event.target.selectedOptions[0].value; // < this fucken thing
        // ^ event is the variable storing the operation stored by the user
        let operation = selectedOp.value
        switch(operation) {
            case 'addition':
            result.value = addNum()
            break;

            case 'subtraction':
            result.value = subNum()
            break;

            case 'multiplication':
            result.value = multNum()
            break;

            case 'division':
            result.value = divNum()
            break;
        }
    }
</script>

<template>
    <div class="container">
        <header class="p-5 my-4 bg-light rounded-3 text-center">
            <h1 class="display-1">Calculator I guess 🙄</h1>
            <p class="lead">
            why math of all things
            </p>
        </header>
        <form class="mx-5 mb-5">
            <div class="row rounded-2">
                <div class="col-10">
                    <h2>This thing</h2>
                    <div class="input-group input-group-lg">
                    <input type="number" class="form-control" placeholder="Input number here" v-model.number="num1" @input="maths">
                    <input type="number" class="form-control" placeholder="Input number here" v-model.number="num2" @input="maths">
                    <select class="form-select text-capitalize" @change="maths" v-model="selectedOp">
                        <option selected disabled>Select Operation</option>
                        <option v-for="operation in operations">{{ operation }}</option>
                    </select>
                    </div>
                </div>
            </div>
        </form>
        <hr class="border border-dark-subtle col-5 mx-auto">
        <div class="container bg-info-subtle p-5 my-2 rounded-3 display-1 text-center">
            <h1 v-if = "!isNaN(result)">Equals {{ result }}</h1>
            <h1 v-else>Is a mystery!</h1>
        </div>
    </div>
</template>

<style scoped>
    input[type=number] {
    -moz-appearance:textfield;
    appearance:textfield;
    }
</style>
