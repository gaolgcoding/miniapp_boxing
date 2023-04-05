<template>
    <button
        open-type="getPhoneNumber"
        @getphonenumber="getPhoneNumber"
    >用户授权登录</button>
</template>
<script>
export default {
    methods: {
        getPhoneNumber(e) {
            // 用户拒绝授权
            if (e?.detail?.errMsg.includes('fail')) {
                return
            }
        }
    }
}
</script>
<style lang="less" scoped>
    
</style>