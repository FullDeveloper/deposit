<template>
    <div>
        <headerNav title="退款记录"/>
        <van-tabs v-model="active">
            <van-tab title="全部">

                <div v-for="(item,index) in list" :key="index">
                    <van-cell-group class="order-item" >
                        <van-panel :title="'订单：'+item.ordercode " :status="item.state"  >
                            <div slot="header">
                                <van-cell class="title" :title="'微信号：'+item.ordercode" :value="item.state" :to="'/user/order/info/'+item.orderid"/>
                            </div>
                            <div>
                                <router-link :to="'/user/order/info/'+item.orderid">
                                    <div class="more" >
                                        <div class="item" v-for="(product,i) in item.products" :key="i">
                                            <div >
                                                <img :src="product.imageURL"/>
                                            </div>
                                        </div>
                                    </div>
                                </router-link>
                            </div>
                            <div slot="footer">
                                <span class="total">押金金额：￥50.00</span>
                                <span class="total" style="margin-left: 115px;">日期：2018-01-18 17:15:32</span>
                                <van-button size="small">查看详情</van-button>
                            </div>
                        </van-panel>
                    </van-cell-group>
                </div>
            </van-tab>
            <van-tab title="待审核">内容 2</van-tab>
            <van-tab title="已退款">内容 3</van-tab>
        </van-tabs>
        <navigate />
    </div>
</template>

<script>
    import navigate from '../../../components/footer/navigate.vue'

    export default {
        components: {
            navigate
        },
        data(){
            return{
                active:0,

                list:[
                    {
                        orderid:1,
                        ordercode:'zrb2712',
                        state:'已退款',
                        createTime: '2019-01-18 17:12:34',
                        products:[
                            {
                                imageURL:'https://pop.nosdn.127.net/19e33c9b-6c22-4a4b-96da-1cb7afb32712',
                                title:'BEYOND博洋家纺 床上套件 秋冬保暖纯棉床单被套 双人被罩 磨毛全棉印花床品四件套',
                                price:'499',
                                quantity:2
                            },
                            {
                                imageURL:'https://pop.nosdn.127.net/19e33c9b-6c22-4a4b-96da-1cb7afb32712',
                                title:'BEYOND博洋家纺 床上套件 秋冬保暖纯棉床单被套 双人被罩 磨毛全棉印花床品四件套',
                                price:'499',
                                quantity:1
                            },
                        ]
                    },
                ]
            }
        }
    }
</script>
<style lang="less">

    .order-item{
        margin-bottom: 10px;
        font-size: 12px;
        .title{
            border-bottom: 1px solid #e5e5e5;

            .van-cell__title{
                flex: 2;
            }
            .van-cell__value{
                color: red;
            }
        }


        .van-panel__footer {
            text-align: right;
            border-bottom: 1px solid #e5e5e5;
        }
        .van-button {
            margin-left: 5px;
        }
        .total{
            position: absolute;
            top: 17px;
            left: 15px;
            font-size: 12px;
        }
        .more{
            overflow-x: scroll;white-space: nowrap;    -webkit-overflow-scrolling: touch;    margin: 5px 0 5px 15px; height: 100%;
            .item{
                width: 90px; height:90px; margin-right: 10px;display: inline-block;
                img{
                    width: 100%;
                }
            }
        }
    }
</style>


