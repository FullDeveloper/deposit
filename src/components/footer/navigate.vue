<template>
    <div style="height:50px;">
    <van-tabbar >
        <van-tabbar-item icon="wap-home" to="/DepositPay">押金缴纳</van-tabbar-item>
        <van-tabbar-item icon="wap-nav" to="/DepositRefund" >申请退款</van-tabbar-item>
        <van-tabbar-item icon="cart" to="/DepositRecord" >缴纳记录</van-tabbar-item>
        <van-tabbar-item icon="contact" to="/DepositRefundRecord">退款记录</van-tabbar-item>
        <van-tabbar-item icon="contact" to="/user/index">我的</van-tabbar-item>
    </van-tabbar>
    </div>
</template>

<script>
import { Tabbar, TabbarItem } from "vant";
export default {
    name:'navigate',
    components:{
        [Tabbar.name]: Tabbar,
        [TabbarItem.name]: TabbarItem,
    }
}
</script>

