<template>
    <div class="chart-container">
      <canvas ref="barChart" v-if="chartData.datasets.length"></canvas>
    </div>
  </template>
  
  <script>
  import { Chart } from "chart.js/auto";
  
  export default {
    data() {
      return {
        chart: null,
        chartData: {
          labels: [
            "January", "February", "March", "April", "May", "June",
            "July", "August", "September", "October", "November", "December"
          ],
          datasets: [
            {
              label: "Data One",
              backgroundColor: [
                "#f87979", "#7fb3ff", "#f9e79f", "#82e0aa", "#f4d03f", "#ffb347",
                "#c39bd3", "#9980fa", "#36a2eb", "#4bc0c0", "#ff6384", "#36a2eb"
              ],
              data: [345, 675, 289, 430, 870, 620, 150, 784, 237, 478, 893, 290]
            }
          ]
        },
        chartOptions: {
          responsive: true,
          maintainAspectRatio: false,
          animation: {
            duration: 3000 // Adjust animation duration as needed
          },
          hover: {
            animationDuration: 1000 // Adjust hover animation duration as needed
          },
          plugins: {
            tooltip: {
              enabled: true,
              callbacks: {
                label: function(tooltipItem) {
                  let label = tooltipItem.label || '';
                  if (label) {
                    label += ': ';
                  }
                  label += tooltipItem.raw;
                  return label;
                }
              }
            }
          }
        }
      };
    },
    mounted() {
      this.renderChart();
    },
    methods: {
      renderChart() {
        const ctx = this.$refs.barChart.getContext("2d");
        this.chart = new Chart(ctx, {
          type: "bar",
          data: this.chartData,
          options: this.chartOptions
        });
      }
    },
    beforeUnmount() {
      if (this.chart) {
        this.chart.destroy();
      }
    }
  };
  </script>
  
  <style scoped>
  .chart-container {
    width: 100%; /* Full width */
    max-width: 100vw; /* Adjust as needed */
    height: 400px; /* Increase height for larger bars */
    margin: auto; /* Center the chart */
    cursor: crosshair; /* Cursor style for hovering */
  }
  </style>
  