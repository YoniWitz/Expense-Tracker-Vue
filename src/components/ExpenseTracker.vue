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
          <input
            type="date"
            v-model="date"
            class="form-control"
            id="inputDate"
            placeholder="mm/dd/yyyy"
          />
        </div>
        <label for="inputDesc" class="col-1 col-form-label">Description:</label>
        <div class="col-2">
          <input
            type="text"
            class="form-control"
            id="inputDesc"
            v-model="desc"
            placeholder="What did you spend on?"
          />
        </div>
        <div class="col-3"></div>
      </div>

      <div class="form-group row">
        <div class="col-3"></div>

        <label for="inputAmount" class="col-1 col-form-label">Amount:</label>
        <div class="col-2">
          <input
            type="number"
            class="form-control"
            id="inputAmount"
            v-model="amount"
            placeholder="How Much?"
          />
        </div>

        <label for="inputWhere" class="col-1 col-form-label">Where:</label>
        <div class="col-2">
          <input
            type="text"
            class="form-control"
            id="inputWhere"
            v-model="where"
            placeholder="Ebay, Moments Cafe etc."
          />
        </div>

        <div class="col-3"></div>
      </div>
      <br />
      <button type="submit" class="btn btn-primary my-1" v-bind:disabled="!formIsValid">Add Expense</button>
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
              <th scope="col">Actions</th>
            </tr>
          </thead>
          <tbody v-for="(expense,index) in expenses" v-bind:key="index">
            <tr>
              <th scope="row">{{index | addOne}}</th>
              <td>{{expense.date | momentDate}}</td>
              <td>{{expense.desc}}</td>
              <td>${{expense.amount}}</td>
              <td>{{expense.where}}</td>
              <td>
                <span class="table-remove">
                  <button
                    type="button"
                    v-on:click="removeExpense(index)"
                    class="btn btn-danger btn-rounded btn-sm my-0"
                  >Remove</button>
                </span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "ExpenseTracker",
  data() {
    return {
      amount: null,
      where: "",
      desc: "",
      date: null,
      expenses: null
    };
  },
  props: {
    msg: String
  },

  methods: {
    removeExpense(index) {
      this.expenses.splice(index, 1);
    },
    addExpense() {
      let expense = {
        amount: this.amount,
        where: this.where,
        desc: this.desc,
        date: this.date
      };
      this.expenses.push(expense);

      window.localStorage.setItem('expenses', JSON.stringify(this.expenses));
      this.clearForm();
    },
    clearForm() {
      this.where = "";
      this.amount = "";
      this.desc = "";
      this.date = "";
    }
  },
  filters: {
    addOne(index) {
      return index + 1;
    },
    momentDate(date) {
      return moment(date).format("LL");
    }
  },
  computed: {
    formIsValid() {
      return this.date && this.amount && this.desc && this.where;
    }
  },
  created() {
    if (typeof Storage !== "undefined") {
      this.expenses = JSON.parse(window.localStorage.getItem("expenses")) || [];
    }
  }
};
</script>

<style scoped>
table {
  background-color: white;
}
</style>
