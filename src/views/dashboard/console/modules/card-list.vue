<template>
  <ElRow :gutter="20" class="flex">
    <ElCol v-for="(item, index) in dataList" :key="index" :sm="12" :md="6" :lg="6">
      <div
        class="metric-card art-card relative flex flex-col justify-center h-35 px-5 mb-5 max-sm:mb-4"
      >
        <span class="metric-title">{{ item.des }}</span>
        <ArtCountTo class="metric-value" :target="item.num" :duration="1300" />
        <div class="flex-c mt-1">
          <span class="metric-caption">较上周</span>
          <span
            class="ml-1 text-xs font-semibold"
            :class="[item.change.indexOf('+') === -1 ? 'text-danger' : 'text-success']"
          >
            {{ item.change }}
          </span>
        </div>
        <div
          class="metric-icon absolute top-0 bottom-0 right-5 m-auto size-12.5 rounded-xl flex-cc bg-theme/10"
        >
          <ArtSvgIcon :icon="item.icon" class="text-xl text-theme" />
        </div>
      </div>
    </ElCol>
  </ElRow>
</template>

<script setup lang="ts">
  interface CardDataItem {
    des: string
    icon: string
    startVal: number
    duration: number
    num: number
    change: string
  }

  /**
   * 卡片统计数据列表
   * 展示总访问次数、在线访客数、点击量和新用户等核心数据指标
   */
  const dataList = reactive<CardDataItem[]>([
    {
      des: '总访问次数',
      icon: 'ri:pie-chart-line',
      startVal: 0,
      duration: 1000,
      num: 9120,
      change: '+20%'
    },
    {
      des: '在线访客数',
      icon: 'ri:group-line',
      startVal: 0,
      duration: 1000,
      num: 182,
      change: '+10%'
    },
    {
      des: '点击量',
      icon: 'ri:fire-line',
      startVal: 0,
      duration: 1000,
      num: 9520,
      change: '-12%'
    },
    {
      des: '新用户',
      icon: 'ri:progress-2-line',
      startVal: 0,
      duration: 1000,
      num: 156,
      change: '+30%'
    }
  ])
</script>

<style lang="scss" scoped>
  .metric-card {
    transition:
      border-color 0.18s ease,
      box-shadow 0.18s ease,
      transform 0.18s ease;

    &:hover {
      border-color: color-mix(in srgb, var(--theme-color) 22%, var(--art-card-border)) !important;
      transform: translateY(-1px);
    }
  }

  .metric-title {
    font-size: 13px;
    font-weight: 650;
    color: var(--art-text-secondary);
  }

  .metric-value {
    margin-top: 8px;
    font-size: 28px;
    font-weight: 750;
    font-variant-numeric: tabular-nums;
    line-height: 1.1;
    color: var(--art-text-primary);
  }

  .metric-caption {
    font-size: 12px;
    color: var(--art-text-tertiary);
  }

  .metric-icon {
    color: var(--theme-color);
    background: color-mix(in srgb, var(--theme-color) 11%, transparent);
  }
</style>
