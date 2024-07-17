<template>
  <CardsComponent/>
  <PieChartComponent />
  <BarChartComponent />
</template>

<script>
import PieChartComponent from './components/PieChartComponent.vue';
import BarChartComponent from './components/BarChartComponent.vue';
import CardsComponent from './components/CardsComponent.vue';



export default {
  name: "App",
  components: {
    PieChartComponent,
    BarChartComponent,
    CardsComponent,
  },
  data() {
    return {
      email: "",
      password: "",
      technology: [],
    };
  },
  methods: {
    login() {
      alert(this.email + " email : password " + this.password);
    },
  },
};
</script>
