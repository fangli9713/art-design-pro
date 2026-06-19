<!-- 按钮组件 -->
<template>
  <button
    type="button"
    class="art-icon-button size-8.5 inline-flex flex-cc c-p text-g-600 dark:text-g-800 text-xl rounded tad-300 hover:bg-hover-color"
    :aria-label="ariaLabel || icon"
    :class="{ 'rounded-full': circle }"
  >
    <ArtSvgIcon :icon="icon"></ArtSvgIcon>
    <slot></slot>
  </button>
</template>

<script lang="ts" setup>
  defineOptions({ name: 'ArtIconButton' })

  interface Props {
    /** 图标名称 */
    icon: string
    /** 圆角按钮 */
    circle?: boolean
    /** 无文本图标按钮的可访问名称 */
    ariaLabel?: string
  }

  withDefaults(defineProps<Props>(), {})
</script>

<style lang="scss" scoped>
  .art-icon-button {
    padding: 0;
    appearance: none;
    background: transparent;
    border: 0;

    &:focus-visible {
      outline: 2px solid var(--art-focus-ring);
      outline-offset: 2px;
    }
  }
</style>
