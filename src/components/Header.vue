<template>
    <div class="header">
        <div class="back"><svg t="1676804452536" class="back-icon" viewBox="0 0 1024 1024" version="1.1"
                xmlns="http://www.w3.org/2000/svg" p-id="2834" data-spm-anchor-id="a313x.7781069.0.i3">
                <path
                    d="M608 736c-6.4 0-19.2 0-25.6-6.4l-192-192C384 524.8 384 499.2 390.4 486.4l192-192c12.8-12.8 32-12.8 44.8 0s12.8 32 0 44.8L460.8 512l166.4 166.4c12.8 12.8 12.8 32 0 44.8C627.2 736 614.4 736 608 736z"
                    fill="#ffffff" p-id="2835" data-spm-anchor-id="a313x.7781069.0.i4" class="selected"></path>
            </svg>返回</div>
        <span class="title">扫码验证结果</span>
    </div>
</template>

<script setup lang='ts'>
import { ref, reactive } from 'vue'
</script>

<style scoped>
.header {
    height: 50px;
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: var(--main-hd-color);
    align-items: center;
    font-size: 14px;
    z-index: 99;
}

.back-icon {
    height: 28px;
    vertical-align: middle;
}

.back {
    width: 60px;
}

.title {
    flex: 1;
    margin-right: 60px;
}
</style>