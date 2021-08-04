<template>
  <div class="">
    <div v-for="(item, index) in infos" :key="index">
      {{ item }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      infos: [
        {
          date: "2021-08-05T13:32:05.1385972-04:00",
          temperatureC: 46,
          temperatureF: 114,
          summary: "Sweltering",
        },
        {
          date: "2021-08-06T13:32:05.1386147-04:00",
          temperatureC: 45,
          temperatureF: 112,
          summary: "Freezing",
        },
        {
          date: "2021-08-07T13:32:05.1386216-04:00",
          temperatureC: 4,
          temperatureF: 39,
          summary: "Chilly",
        },
        {
          date: "2021-08-08T13:32:05.1386277-04:00",
          temperatureC: -16,
          temperatureF: 4,
          summary: "Sweltering",
        },
        {
          date: "2021-08-09T13:32:05.1386363-04:00",
          temperatureC: 41,
          temperatureF: 105,
          summary: "Mild",
        },
      ],
    };
  },
  created() {
    fetch("https://localhost:5001/WeatherForecast", {
      mode: "cors",
      headers: {
        "Access-Control-Allow-Origin": "*",
      },
    })
      .then((response) => response.json())
      .then((data) => {
        // console.log(data);
        this.infos = data;
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
