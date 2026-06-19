<!-- 工作台页面 -->
<template>
  <div class="console-page">
    <section class="console-head">
      <div>
        <p class="eyebrow">Overview</p>
        <h1>工作台</h1>
        <span>关注核心指标、用户动态和待办事项。</span>
      </div>
      <ElButton type="primary">
        <ArtSvgIcon icon="ri:add-line" />
        新建任务
      </ElButton>
    </section>

    <CardList></CardList>

    <ElRow :gutter="20">
      <ElCol :sm="24" :md="12" :lg="10">
        <ActiveUser />
      </ElCol>
      <ElCol :sm="24" :md="12" :lg="14">
        <SalesOverview />
      </ElCol>
    </ElRow>

    <ElRow :gutter="20">
      <ElCol :sm="24" :md="24" :lg="12">
        <NewUser />
      </ElCol>
      <ElCol :sm="24" :md="12" :lg="6">
        <Dynamic />
      </ElCol>
      <ElCol :sm="24" :md="12" :lg="6">
        <TodoList />
      </ElCol>
    </ElRow>

    <AboutProject />
  </div>
</template>

<script setup lang="ts">
  import CardList from './modules/card-list.vue'
  import ActiveUser from './modules/active-user.vue'
  import SalesOverview from './modules/sales-overview.vue'
  import NewUser from './modules/new-user.vue'
  import Dynamic from './modules/dynamic-stats.vue'
  import TodoList from './modules/todo-list.vue'
  import AboutProject from './modules/about-project.vue'

  defineOptions({ name: 'Console' })
</script>

<style lang="scss" scoped>
  .console-page {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .console-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 4px 2px 2px;

    .eyebrow {
      margin: 0 0 6px;
      font-size: 12px;
      font-weight: 700;
      line-height: 1;
      color: var(--theme-color);
      text-transform: uppercase;
    }

    h1 {
      margin: 0;
      font-size: 26px;
      font-weight: 750;
      line-height: 1.25;
      color: var(--art-text-primary);
      letter-spacing: 0;
    }

    span {
      display: block;
      margin-top: 6px;
      font-size: 14px;
      color: var(--art-text-secondary);
    }

    .el-button {
      gap: 6px;
      font-weight: 650;
    }
  }

  @media (width <= 640px) {
    .console-head {
      flex-direction: column;
      gap: 14px;
      align-items: flex-start;

      .el-button {
        width: 100%;
      }
    }
  }
</style>
