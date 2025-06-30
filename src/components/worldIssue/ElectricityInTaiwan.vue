<template>
  <div class="bg-gray-50 py-12 sm:py-16">
    <div class="mx-auto max-w-2xl px-6 lg:max-w-7xl lg:px-8">
      <!-- <h2 class="text-center text-base/7 font-semibold text-indigo-600">Deploy faster</h2> -->
      <p
        class="mx-auto mt-2 max-w-4xl text-center text-4xl font-semibold tracking-tight text-balance text-gray-950 leading-tight sm:text-5xl"
      >
        <!-- https://www.iea.org/reports/global-energy-review-2025/co2-emissions#abstract -->
        Electricity in Taiwan 2024
      </p>
      <div class="mt-10 grid gap-8 sm:mt-16 lg:grid-cols-2">
        <!-- 左欄：文字內容 -->
        <div class="relative">
          <div class="absolute inset-px rounded-lg bg-white" />
          <div class="relative p-6 sm:p-8 space-y-6">
            <div>
              <p class="text-sm text-gray-600">
                根據2024年的數據，台灣的電力消費中，化石燃料電力仍占大多數，達到約83%。在化石燃料中，天然氣以超過四成的比例為主力，而燃煤的貢獻則接近四成。與此同時，低碳能源佔台灣電力消費的比例約為17%。其中太陽能佔了大約5%，核能約占4%，風力發電則略低於4%，水力發電約占2.5%。其他再生能源如油和未明確的再生能源則占比接近忽略不計。這表明在清潔電力發展上，台灣仍有很大的提升空間。
              </p>
              <p class="mt-4 text-xs text-gray-500">資料來源: 低碳力</p>
            </div>
            <div>
              <p class="text-sm text-gray-600">
                In 2024, electricity consumption in the Republic of China (Taiwan) remains heavily dominated by fossil fuels, which account for over 80% of the total supply. Gas and coal contribute almost equally to this majority, comprising nearly 40% each. On the low-carbon side, clean energy accounts for about 17% of electricity generation. Among these, solar power leads with a little over 5%, followed by nuclear at slightly more than 4%. Wind and hydropower contribute less, with close to 4% and 2% respectively. It's evident that a significant shift towards low-carbon sources is necessary to balance the current heavy reliance on fossil fuels.
              </p>
              <p class="mt-4 text-xs text-gray-500">Source: LowCarbonPower</p>
            </div>
          </div>
        </div>

        <!-- 右欄：圖表 -->
        <div class="relative">
          <div class="absolute inset-px rounded-lg bg-white" />
          <div class="relative p-6 sm:p-8 h-full flex items-center justify-center">
            <div class="w-full max-w-md mx-auto">
              <div id="chart" class="w-full">
                <ApexChart type="donut" :options="chartOptions" :series="series" />
              </div>
            </div>
          </div>
        </div>
      </div>

      <p
        class="mx-auto mt-2 max-w-4xl text-center text-4xl font-semibold tracking-tight text-balance text-gray-950 leading-tight sm:text-5xl"
      >
        So we started looking for answers, starting from Matou Mountain!
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import VueApexCharts from 'vue3-apexcharts';

// Register the component
const ApexChart = VueApexCharts;

const series = ref([42.36, 39.19, 1.45, 5.29, 4.21, 3.63, 2.52, 1.26, 0.01]);
const chartOptions = ref({
  chart: {
    type: 'donut',
  },
  plotOptions: {
    pie: {
      donut: {
        size: '70%',
        labels: {
          show: true,
          name: {
            show: true,
            fontSize: '14px',
            color: '#6B7280',
            offsetY: 20
          },
          value: {
            show: true,
            fontSize: '28px',
            fontWeight: 'bold',
            color: '#111827',
            offsetY: -10,
            formatter: function (val) {
              return '17%';
            }
          },
          total: {
            show: true,
            showAlways: true,
            label: 'Low Carbon',
            fontSize: '16px',
            fontWeight: 600,
            color: '#4B5563',
            formatter: function (w) {
              return '17%';
            }
          }
        }
      }
    }
  },
  labels: ['Gas', 'Coal', 'Oil', 'Solar', 'Nuclear', 'Wind', 'Hydropower', 'Other renewables', 'Geothermal'],
  responsive: [{
    breakpoint: 480,
    options: {
      chart: {
        width: 280
      },
      plotOptions: {
        pie: {
          donut: {
            size: '65%',
            labels: {
              value: {
                fontSize: '24px'
              },
              total: {
                fontSize: '14px'
              }
            }
          }
        }
      },
      legend: {
        position: 'bottom'
      }
    }
  }]
});
</script>
