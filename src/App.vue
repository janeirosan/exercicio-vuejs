<script setup>
  const operations = [{
    name:'Select operation',
    op: 0
  },{
    name:'addition',
    op: num1 + num2
  },{
    name:'subtraction',
    op: num1 - num2
  },{
    name:'multiplication',
    op: num1 * num2
  },{
    name:'division',
    op: num1 / num2
  }]
  let result = 'my bals'

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
            <select class="form-select text-capitalize" v-model="selected">
              <option class="dropdown-item" v-for="operation in operations">{{ operation.name }}</option>
            </select>
          </div>
        </div>
        <button type="button" class="col btn btn-primary" @click.prevent="operations()">Do it!</button>
      </div>
    </form>
    <hr class="border border-dark-subtle col-5 mx-auto">
    <div class="container bg-info-subtle p-5 my-2 rounded-3">
      <h1 class="display-1 text-center" id="result" v-if="operations">
        {{ result }}
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
