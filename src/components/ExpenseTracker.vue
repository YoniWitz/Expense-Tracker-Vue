<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Add a new item:</h2>
    <form>
      <div class="form-group row">
        <div class="col-3"></div>

        <label for="inputDate" class="col-1 col-form-label">Date:</label>
        <div class="col-2">
          <input type="date" class="form-control" id="inputDate" placeholder="mm/dd/yyyy" />
        </div>
        <label for="inputDesc" class="col-1 col-form-label">Description:</label>
        <div class="col-2">
          <input
            type="text"
            class="form-control"
            id="inputDesc"
            placeholder="What did you spend on?"
          />
        </div>
          <div class="col-3"></div>
      </div>

      <div class="form-group row">
        <div class="col-3"></div>
        <label for="inputAmount" class="col-1 col-form-label">Amount:</label>
        <div class="col-2">
          <input type="number" class="form-control" id="inputAmount" placeholder="How Much?" />
        </div>

        <div class="col-3"></div>
        <div class="col-3"></div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "ExpenseTracker",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
