<template>
  <svg :class="`svg-icon ${className}`" aria-hidden="true" :style="style">
    <use :xlink:href="`#icon-${type}`"/>
  </svg>
</template>

<script>
const requireAll = (requireContext) => {
  requireContext.keys().map(requireContext)
}

// import all svg
const req = require.context('@/assets/svg', true, /\.svg$/)
requireAll(req)

/**
 * @module components/Icon
 * @author 杜伟坡 <dovapour@qq.com>
 * @desc 自定义图标
 * @example <Icon type="js" :size="14"></Icon>
 * @vue-prop {String} type 名称
 * @vue-prop {String} [color] 颜色
 * @vue-prop {Number} [size=14] 尺寸
 * @vue-prop {String} [className] css类
 */

export default {
  name: 'Icon',
  props: {
    type: {
      type: String,
      required: true
    },
    color: {
      type: String,
      default: '#5c6b77'
    },
    size: {
      type: Number,
      default: 14
    },
    className: {
      type: String,
      default: ''
    }
  },
  computed: {
    style() {
      return {
        fill: 'currentColor',
        overflow: 'hidden',
        width: '1em',
        height: '1em',
        verticalAlign: 'middle',
        fontSize: `${this.size}px`,
        color: this.color
      }
    }
  }
}
</script>
