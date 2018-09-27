<template>
    <div id="app">
        <header id="header">
            <el-select v-model="value" placeholder="请选择" class="head-nav" popper-class="head-nav-sel">
                <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value">
                </el-option>
            </el-select>
            <div class="gong">
                <span class="bigt">
                    <i class="el-icon-star-on"></i>公告：</span>
                <span>ZB.com关于开放PAX交易区的公告</span>
            </div>
        </header>
        <Home />
    </div>
</template>

<script>
import Home from './components/home.vue'
import './libs/swiper.css'
import $ from 'jquery'
window.$ = $;
var aa = document.getElementById('viewport');
let srreenW = window.screen.width;

aa.setAttribute('content', 'width=device-width, initial-scale=' + srreenW / 1010 + ', maximum-scale=1.0, user-scalable=no');
window.aa = aa;
export default {
    name: 'app',
    data () {
        return {
            options: [
                {
                    value: '选项1',
                    label: 'ZB生态'
                }, {
                    value: '选项2',
                    label: 'ZB合伙人'
                }, {
                    value: '选项3',
                    label: 'EOS投票'
                }, {
                    value: '选项4',
                    label: 'EOS挖矿'
                }, {
                    value: '选项5',
                    label: 'ZBG.COM'
                }
            ],
            value: '选项1'
        }
    },
    components: {
        Home
    }
}
</script>

<style lang="less">
html,
body {
    width: 1010px;
    height: 100%;
    min-height: 100%;
    font-size: 16px;
}
ol,
ul {
    list-style: none;
}
div,
ul,
li,
header,
body {
    margin: 0;
    padding: 0;
}
#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
#header {
    background: #2a333a;
    height: 2.25rem;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .head-nav {
        font-size: 12px;
        min-height: 100%;
        display: flex;
        width: 7rem;
        align-items: center;
        height: 100%;
        input {
            color: rgb(210, 218, 228);
            border: none;
            background: transparent;
        }
    }
    .gong {
        color: #fff;
        font-size: 16px;
        display: flex;
        float: right;
        right: 2rem;
        align-items: center;
        .bigt {
            color: red;
            font-size: 12px;
        }
    }
}
</style>
