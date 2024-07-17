<template>
    <div class="charts-container">
      <div class="chart-container">
        <canvas ref="pieChart" v-if="chartData.datasets.length"></canvas>
      </div>
      <div class="chart-container">
        <canvas ref="pieChartRight" v-if="chartDataRight.datasets.length"></canvas>
      </div>
    </div>
  </template>
  
  <script>
  import { Chart } from "chart.js/auto";
  
  export default {
    data() {
      return {
        chart: null,
        chartRight: null,
        chartData: {
          labels: ["Data1", "Data2", "Data3", "Data4"],
          datasets: [
            {
              label: "Data One",
              backgroundColor: [
                "#2c3e50", // Dark navy
                "#d35400", // Pumpkin
                "#16a085", // Teal
                "#f39c12", // Golden
              ],
              data: [55, 28, 10, 7],
            },
          ],
        },
        chartDataRight: {
          labels: ["Data5", "Data6", "Data7", "Data8"],
          datasets: [
            {
              label: "Data Two",
              backgroundColor: [
                "#8e44ad", // Purple
                "#d35400", // Pumpkin
                "#2980b9", // Blue
                "#27ae60", // Green
              ],
              data: [25, 40, 15, 20],
            },
          ],
        },
        chartOptions: {
          responsive: true,
          maintainAspectRatio: false,
          animation: {
            duration: 3000,
          },
          hover: {
            animationDuration: 1000,
          },
          plugins: {
            tooltip: {
              enabled: true,
              callbacks: {
                label: function (tooltipItem) {
                  let label = tooltipItem.label || "";
                  if (label) {
                    label += ": ";
                  }
                  label += tooltipItem.raw;
                  return label;
                },
              },
            },
          },
        },
      };
    },
    mounted() {
      this.renderChart();
      this.renderChartRight();
    },
    methods: {
      renderChart() {
        const ctx = this.$refs.pieChart.getContext("2d");
        this.chart = new Chart(ctx, {
          type: "pie",
          data: this.chartData,
          options: this.chartOptions,
        });
      },
      renderChartRight() {
        const ctx = this.$refs.pieChartRight.getContext("2d");
        this.chartRight = new Chart(ctx, {
          type: "pie",
          data: this.chartDataRight,
          options: this.chartOptions,
        });
      },
    },
    beforeUnmount() {
      if (this.chart) {
        this.chart.destroy();
      }
      if (this.chartRight) {
        this.chartRight.destroy();
      }
    },
  };
  </script>
  
  <style scoped>
  .charts-container {
    display: flex;
    justify-content: space-between;
    width: 100%;
    max-width: 1200px;
    margin: auto;
  }
  
  .chart-container {
    flex: 1;
    margin: 10px;
    padding: 20px;
    height: 400px; /* Fixed height for charts */
  }
  </style>
  