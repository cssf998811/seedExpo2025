<template>
  <div class="bg-gray-50 py-12 sm:py-16">
    <div class="mx-auto max-w-2xl px-6 lg:max-w-7xl lg:px-8">
      <!-- <h2 class="text-center text-base/7 font-semibold text-indigo-600">Deploy faster</h2> -->
      <p
        class="mx-auto mt-2 max-w-4xl text-center text-4xl font-semibold tracking-tight text-balance text-gray-950 leading-tight sm:text-5xl"
      >
        <!-- https://www.iea.org/reports/global-energy-review-2025/co2-emissions#abstract -->
        Global Energy Review 2025
      </p>
      <div class="mt-10 grid gap-4 sm:mt-16 lg:grid-cols-1 lg:grid-rows-1">
        <div class="relative lg:row-span-2">
          <div class="absolute inset-px rounded-lg bg-white lg:rounded-l-4xl" />
          <div
            class="relative flex h-full flex-col overflow-hidden rounded-[calc(var(--radius-lg)+1px)] lg:rounded-l-[calc(2rem+1px)]"
          >
            <div class="px-8 pt-4 pb-2 sm:px-10 sm:pt-10 sm:pb-0">
              <p class="mt-2 w-full text-sm text-gray-600 max-lg:text-center">
                圖表顯示了全球能源相關的二氧化碳排放量變化。值得注意的是 2020年因 COVID-19疫情導致的短暫下降，以及隨後經濟復甦帶來的迅速反彈，排放量再創新高。這突顯了全球在能源轉型與氣候目標上所面臨的嚴峻挑戰。
              </p>
              <p class="mt-4 text-xs text-gray-500 max-lg:text-center">資料來源: IEA. Licence: CC BY 4.0</p>
            </div>
            <div class="px-8 pt-4 pb-2 sm:px-10 sm:pt-10 sm:pb-0">
              <p class="mt-2 w-full text-sm text-gray-600 max-lg:text-center">
                The chart shows the dramatic changes in global energy-related emissions. It is worth noting that emissions hit a new high in 2020 after a brief recovery due to the COVID-19 pandemic and the subsequent sharp rebound brought about by economic recovery. This highlights the severe challenges facing global energy transition and climate goals.
              </p>
              <p class="mt-4 text-xs text-gray-500 max-lg:text-center">Source: IEA. Licence: CC BY 4.0</p>
            </div>
            <div
              class="@container relative min-h-120 w-full px-7 mt-4 grow max-lg:mx-auto max-lg:max-w-sm"
            >
              <div id="chart">
                <apex-chart
                  type="line"
                  height="350"
                  :options="chartOptions"
                  :series="series"
                ></apex-chart>
              </div>
            </div>
          </div>
          <div
            class="pointer-events-none absolute inset-px rounded-lg shadow-sm outline outline-black/5 lg:rounded-l-4xl"
          />
        </div>
        <div class="relative lg:row-span-2">
          <div
            class="absolute inset-px rounded-lg bg-white max-lg:rounded-b-4xl lg:rounded-r-4xl"
          />
          <div
            class="relative flex h-full flex-col overflow-hidden rounded-[calc(var(--radius-lg)+1px)] max-lg:rounded-b-[calc(2rem+1px)] lg:rounded-r-[calc(2rem+1px)]"
          >
            <div class="px-8 pt-8 pb-3 sm:px-10 sm:pt-10 sm:pb-0">
              <p class="mt-2 text-xl font-medium tracking-tight text-gray-950 max-lg:text-center">
                為什麼氣候會變得越來越不正常？
              </p>
              <p class="mt-2 max-w-4xl text-sm/7 text-gray-6 text-gray-600 max-lg:text-center">
                一個簡單的問題，背後是複雜的氣候科學。全球暖化、極端天氣、海平面上升...這一切都源於人類活動對地球系統的深刻影響。
              </p>
              <p class="mt-2 text-xl font-medium tracking-tight text-gray-950 max-lg:text-center">
                Why is the climate becoming increasingly abnormal?
              </p>
              <p class="mt-2 max-w-4xl text-sm/7 text-gray-6 text-gray-600 max-lg:text-center">
                A simple question, behind it is complex climate science. Global warming, extreme weather, sea level rise... all of this comes from human activities。
              </p>
            </div>
            <div class="relative flex min-h-80 w-full grow items-center justify-center">
              <p class="select-none text-[12rem] font-bold text-gray-400">?</p>
            </div>
          </div>
          <div
            class="pointer-events-none absolute inset-px rounded-lg shadow-sm outline outline-black/5 max-lg:rounded-b-4xl lg:rounded-r-4xl"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const series = ref([
  {
    name: 'Gt CO₂',
    data: [
      24.6, 24.9, 25.3, 26.4, 27.7, 28.7, 29.7, 30.9, 31.1, 30.7, 32.6, 33.6, 34.0, 34.7, 34.8,
      34.7, 34.8, 35.4, 36.3, 36.3, 34.5, 36.4, 36.8, 37.3, 37.6,
    ],
  },
])

const chartOptions = ref({
  chart: {
    type: 'line',
    zoom: {
      enabled: false,
    },
  },
  dataLabels: {
    enabled: false,
  },
  stroke: {
    curve: 'straight',
  },
  title: {
    text: 'Global CO2 emissions from energy combustion and industrial processes and their annual change, 2000-2024',
    align: 'left',
  },
  grid: {
    row: {
      colors: ['#f3f3f3', 'transparent'],
      opacity: 0.5,
    },
  },
  xaxis: {
    categories: [
      '2000',
      '2001',
      '2002',
      '2003',
      '2004',
      '2005',
      '2006',
      '2007',
      '2008',
      '2009',
      '2010',
      '2011',
      '2012',
      '2013',
      '2014',
      '2015',
      '2016',
      '2017',
      '2018',
      '2019',
      '2020',
      '2021',
      '2022',
      '2023',
      '2024',
    ],
  },
})
</script>
