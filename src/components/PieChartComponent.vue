<template>
    <div class="charts-container">
      <div class="chart-container">
        <div class="chart-caption">{{ chartData.datasets[0].label }}</div>
        <canvas ref="pieChart" v-if="chartData.datasets.length"></canvas>
        <div class="chart-legend">
          <div v-for="(label, index) in chartData.labels" :key="index">
            <span :style="{ backgroundColor: gradientColors[index] }" class="legend-color"></span>
            <span class="legend-label">{{ label }}:</span>
            <span class="legend-value">{{ chartData.datasets[0].data[index] }}</span>
          </div>
        </div>
      </div>
      <div class="chart-container">
        <div class="chart-caption">{{ chartDataRight.datasets[0].label }}</div>
        <canvas ref="pieChartRight" v-if="chartDataRight.datasets.length"></canvas>
        <div class="chart-legend">
          <div v-for="(label, index) in chartDataRight.labels" :key="index">
            <span :style="{ backgroundColor: gradientColorsRight[index] }" class="legend-color"></span>
            <span class="legend-label">{{ label }}:</span>
            <span class="legend-value">{{ chartDataRight.datasets[0].data[index] }}</span>
          </div>
        </div>
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
        gradientColors: [],
        gradientColorsRight: [],
        chartData: {
          labels: ["Data1", "Data2", "Data3", "Data4"],
          datasets: [
            {
              label: "Transaction History",
              backgroundColor: [], // We'll set this dynamically
              data: [55, 28, 10, 7],
            },
          ],
        },
        chartDataRight: {
          labels: ["Data5", "Data6", "Data7", "Data8"],
          datasets: [
            {
              label: "Data Two",
              backgroundColor: [], // We'll set this dynamically
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
            legend: {
              display: false,
            },
          },
        },
      };
    },
    mounted() {
      this.createGradientColors();
      this.renderChart();
      this.renderChartRight();
    },
    methods: {
      createGradientColors() {
        const ctx = this.$refs.pieChart.getContext("2d");
        const ctxRight = this.$refs.pieChartRight.getContext("2d");
  
        const createGradient = (ctx, colors) => {
          const gradient = ctx.createLinearGradient(0, 0, 0, 400);
          colors.forEach((color, index) => {
            gradient.addColorStop(index / (colors.length - 1), color);
          });
          return gradient;
        };
  
        this.gradientColors = [
          createGradient(ctx, ["#f17ba8", "#960779"]),
          createGradient(ctx, ["#c7aaf1", "#4336ab"]),
          createGradient(ctx, ["#44c4f1", "#88ddee"]),
          createGradient(ctx, ["#ffb82c", "#ffe066"]),
        ];
  
        this.gradientColorsRight = [
          createGradient(ctxRight, ["#8e44ad", "#c080d0"]),
          createGradient(ctxRight, ["#d35400", "#ff9966"]),
          createGradient(ctxRight, ["#2980b9", "#66aadd"]),
          createGradient(ctxRight, ["#27ae60", "#66cc88"]),
        ];
  
        this.chartData.datasets[0].backgroundColor = this.gradientColors;
        this.chartDataRight.datasets[0].backgroundColor = this.gradientColorsRight;
      },
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
    margin: 20px auto;
  }
  
  .chart-container {
    flex: 1;
    margin: 10px;
    padding: 20px;
    height: 400px; /* Fixed height for charts */
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .chart-caption {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 10px;
  }
  
  .chart-legend {
    margin-top: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .legend-color {
    display: inline-block;
    width: 12px;
    height: 12px;
    margin-right: 8px;
  }
  
  .legend-label {
    font-weight: bold;
    margin-right: 4px;
  }
  
  .legend-value {
    font-weight: bold;
  }
  </style>
  