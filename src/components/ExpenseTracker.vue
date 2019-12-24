<template>
  <div class="expenseTracker">
    <h1>{{ msg }}</h1>
    <br />
    <h2>Add a new item:</h2>
    <br />
    <form v-on:submit.prevent="addExpense">
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

        <label for="inputWhere" class="col-1 col-form-label">Where:</label>
        <div class="col-2">
          <input
            type="text"
            class="form-control"
            id="inputWhere"
            placeholder="Ebay, Moments Cafe etc."
          />
        </div>

        <div class="col-3"></div>
        <div class="col-3"></div>
      </div>
      <br />
      <button type="submit" class="btn btn-primary my-1">Add Expense</button>
    </form>

    <br />

    <div class="form-group row">
      <div class="col-3"></div>
      <div class="col-6">
        <table class="table table-hover table-bordered">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Date</th>
              <th scope="col">Description</th>
              <th scope="col">Amount</th>
              <th scope="col">Where</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <th scope="row">1</th>
              <td>Mark</td>
              <td>Otto</td>
              <td>@mdo</td>
              <td>@mdo</td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ExpenseTracker",
  data() {
    return {
      amount:null,
      where:"",
      desc:"",
      expenses: {}
    };
  },
  props: {
    msg: String
  },

  methods: {
    addExpense() {
      console.log("expense added");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
  background-color: white;
}
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
