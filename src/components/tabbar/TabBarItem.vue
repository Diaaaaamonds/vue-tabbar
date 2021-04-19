<template>
    <div class="tab-bar-item" @click="itemClick">
        <div v-if="!isActive"><slot name="item-icon"></slot></div>
        <div v-else><slot name="item-icon-active"></slot></div>
        <!-- 动态绑定style 并把style抽到计算属性里-->
        <!-- 插槽动态绑定样式 外边加div -->
        <div :style="activeStyle"><slot name="item-text"></slot></div>
        
    </div>
</template>




<script>

export default {
    name: "TabBarItem",
    //从App里传进来 父传子
    props: {
        path: String,
        //App中给定activeColor的值 再在props里定义类型
        activeColor: {
            type: String,
            default: 'red' //默认红色
        }
    },
    data() {
        return {
            // isActive: true
        }
    },
    computed: {
        isActive() {
            //哪一个对象活跃 $route就是哪个
            // /home -> item1(/home) = true
            // !==-1表示找到
            return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle() {
            return this.isActive ? {color: this.activeColor} : {}
        }
    },
    methods: {
        itemClick() {
            //路径跳转
            this.$router.replace(this.path)
        }
    }
}

</script>




<style scoped>

.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 49px;  /* tabbar高度一般为49px */
  display: block;
}
.tab-bar-item img {
    width: 24px;
    height: 24px;
}

/* .active {
    color: red;
} */

</style>
