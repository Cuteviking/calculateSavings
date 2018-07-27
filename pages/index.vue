<template>
  <section class="container">
    <p>Calculate amount to save each month</p>
    <form>

      Monthly Saving: <input v-model="monthSave" type="number" name=""><br>
      Years: <input v-model="time" type="number" name=""><br>
      Profit: <input v-model="profit" type="number" name=""><br>
    </form>
    <p>Your goal will be {{fromMonthSaveToGoal}} kr</p>
  </section>
</template>

<script>

export default {
  data() {
    return{
      time: 1,
      profit: 0,
      monthSave: 10000
    }
  },
  computed: {
    fromMonthSaveToGoal: function() {
      const amountOfMonths = this.time*12;
      const profitDecimal = (this.profit / 100) + 1;
      var sum = 0;

      for(var month = 0; month < amountOfMonths; month++) {
        sum += Number(this.monthSave);

        var monthInPrecentage = (month + 1) / 12;
        if(monthInPrecentage % 1 == 0) {
          sum = sum * profitDecimal;
        }
      }

      return sum;
    }
  }
}
</script>

<style>

</style>

