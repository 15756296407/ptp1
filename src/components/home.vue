<template>
    <div>
        <div class="banner">
            <div class="banner-bk">
                <div class="nav">
                    <img class="imgg" src="../assets/images/logo2018.png" alt="">
                    <ul class="lists">
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                        <li>
                            <span>币种行情</span>
                        </li>
                    </ul>
                </div>
                <div class="video">
                    <a href="javascript:void(0)">
                        <img src="../assets/images/banner_tech_tilil.png" alt="">
                    </a>
                </div>
                <div class="swiper-container">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-bw4.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-lever.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-mortgage.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-otc.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-paxon.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-quest.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-subaccount.jpg" alt=""></a>
                        </div>
                        <div class="swiper-slide">
                            <a href="javascript:void(0)"><img src="../assets/images/h-sban-zb.jpg" alt=""></a>
                        </div>
                    </div>
                    <!-- 如果需要分页器 -->
                    <div class="swiper-pagination"></div>
                </div>
            </div>
        </div>
        <div class="marketData">
            <div>
                <ul class="checks" @click="checka">
                    <li class="check checkActive" type="zx">
                        <span type="zx">自选区</span>
                    </li>
                    <li class="check" type="qc">
                        <span type="qc">QC区</span>
                    </li>
                    <li class="check" type="zb">
                        <span type="zb">ZB区</span>
                    </li>
                    <li class="check" type="ustd">
                        <span type="ustd">USTD区</span>
                    </li>
                    <li class="check" type="btc">
                        <span type="btc">BTC区</span>
                    </li>
                    <li class="check" type="pax">
                        <span type="pax">PAX区</span>
                    </li>
                    <li class="search">
                        <div>
                            <input type="text" placeholder="搜索交易币种">
                            <i class="el-icon-search"></i>
                        </div>

                    </li>
                </ul>
            </div>
            <div class="eltab">
                <el-table :data="tableData" style="width: 100%" :default-sort="{prop: 'name', order: 'descending'}">
                    <el-table-column prop="name" label="交易对" sortable width="152">
                        <template slot-scope="scope">
                            <i class="el-icon-time"></i>
                            <span style="margin-left: 10px;color:#000;">{{ scope.row.name }}</span>
                            <span style="color:#999">/PAX</span>
                        </template>
                    </el-table-column>
                    <el-table-column prop="nowPrice" label="实时价格" sortable width="124" header-align='right' align="right">
                        <template slot-scope="scope">
                            <div :class="scope.row.priceLv > 0 ? 'up' : 'down'">
                                <span>{{ scope.row.nowPrice }}</span>
                                <i :class="scope.row.priceLv > 0 ? 'el-icon-sort-up' : 'el-icon-sort-down'"></i>
                            </div>
                        </template>
                    </el-table-column>
                    <el-table-column prop="highPrice" label="24H最高价" width="124" header-align='right' align="right">
                    </el-table-column>
                    <el-table-column prop="lowPrice" label="24H最低价" width="124" header-align='right' align="right">
                    </el-table-column>
                    <el-table-column prop="num" label="成交量" sortable width="124" header-align='right' align="right">
                        <template slot-scope="scope">
                            <span>{{ scope.row.num + scope.row.name}}</span>
                        </template>
                    </el-table-column>
                    <el-table-column prop="priceLv" label="24H涨跌幅" sortable width="113" header-align='right' align="right">
                        <template slot-scope="scope">
                            <div :class="scope.row.priceLv > 0 ? 'up' : 'down'">
                                <span>{{ scope.row.priceLv + '%' }}</span>
                            </div>
                        </template>
                    </el-table-column>
                    <el-table-column prop="gg" label="杠杆" sortable width="75" header-align='right'>
                    </el-table-column>
                    <el-table-column prop="Ksell" label="K线交易" width="75" header-align='right'>
                        <template slot-scope="scope">
                            <el-button icon="el-icon-remove-outline"></el-button>
                        </template>
                    </el-table-column>
                    <el-table-column prop="Nsell" label="现货交易">
                        <template slot-scope="scope">
                            <el-button icon="el-icon-circle-plus-outline"></el-button>
                        </template>
                    </el-table-column>
                </el-table>
                <div style="color:red;font-size:12px;padding:15px 0;" v-if="tableData.length < 10">
                    <span>查看更多</span>
                    <i class="el-icon-caret-bottom"></i>
                </div>
            </div>
        </div>
        <ul class="introduce">
            <li>
                <img src="../assets/images/home-n-pic1.png" alt="">
                <h4>现货/杠杆交易</h4>
                <p>多币种支持，高流动性<br>三倍杠杆，高性能撮合交易</p>
            </li>
            <li>
                <img src="../assets/images/home-n-pic2.png" alt="">
                <h4>OTC场外交易</h4>
                <p>支持多种法币交易<br>平台担保、快速安全</p>
            </li>
            <li>
                <img src="../assets/images/home-n-pic3.png" alt="">
                <h4>金融级安全系统</h4>
                <p>多层、多集群系统架构<br>安全稳定运营超过4年</p>
            </li>
            <li>
                <img src="../assets/images/home-n-pic4.png" alt="">
                <h4>专业客户服务</h4>
                <p>24h在线客服，服务数百万用户<br>及时响应用户问题</p>
            </li>
        </ul>
        <div class="bottom">
            <h3>多终端覆盖</h3>
            <h4>支持iOS、Android、Windows、Mac等客户端支持全业务功能</h4>
            <div class="list-ld">
                <div class="list-pic"><img src="../assets/images/home-n-down-pic1.png"></div>
                <div class="download-btn-wrap">
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">IOS 下载</el-button>
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">App Store 下载</el-button>
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">Android 下载</el-button>
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">Google play 下载</el-button>
                </div>
                <div class="list-pic list-pic1"><img src="../assets/images/home-n-down-pic2.png"></div>
                <div class="download-btn-wrap">
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">Mac 点击下载</el-button>
                    <el-button class="download-btn-item" style="visibility:hidden" type="primary" icon="el-icon-warning">App Store 下载</el-button>
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">Win32位</el-button>
                    <el-button class="download-btn-item" type="primary" icon="el-icon-warning">Win64位</el-button>
                </div>
            </div>
            <div class="know-more">
                <span>了解更多 ></span>
                <img style="margin: -21px 0 0 25px;" src="../assets/images/qrcode.png" alt="">
            </div>
        </div>
        <div class="foott">
            <div class="foot1">
                <div class="foot1-col1">
                    <a href="javascript:void(0)"><img src="../assets/images/logo-zb.png" alt=""></a>
                </div>
                <div class="bk-footer-contact">
                    <h5>下载支持</h5>
                    <p class="link">
                        <a href="https://www.zb.cn/i/developer" target="_blank">API文档</a>
                    </p>
                    <p class="link">
                        <a href="https://www.zb.cn/mobile/app" target="_blank">APP下载</a>
                    </p>
                    <p class="link">
                        <a href="https://www.zb.cn/mobile/download" target="_blank">其它下载</a>
                    </p>
                </div>
                <div class="bk-footer-contact">
                    <h5>客户服务</h5>
                    <p class="link">
                        <a href="https://www.zb.cn/i/help" target="_blank">使用教程</a>
                    </p>
                    <p class="link">
                        <a href="https://www.zb.cn/i/faq" target="_blank">常见问题</a>
                    </p>
                    <p class="link">
                        <a href="https://www.zb.cn/i/document" target="_blank">服务协议</a>
                    </p>
                    <p class="link">
                        <a href="https://www.zb.cn/i/rate" target="_blank">交易费率</a>
                    </p>
                </div>
                <div class="bk-footer-contact">
                    <h5>投票上币</h5>
                    <p class="link">
                        <a href="https://vip.zb.cn/vote" target="_blank">我要投票</a>
                    </p>

                    <p class="link isSubUser">
                        <a href="https://vip.zb.cn/activity/zblcr" target="_blank">上币申请</a>
                    </p>

                    <p class="link isSubUser">
                        <a href="https://vip.zb.cn/vote/outifitApply" target="_blank">节点中心</a>
                    </p>
                    <p class="link isSubUser">
                        <a href="https://vip.zb.cn/vote/orgList" target="_blank">节点列表</a>
                    </p>
                </div>
                <div class="bk-footer-contact">
                    <h5>其它</h5>
                    <p class="link">
                        <a href="https://www.zb.cn/i/blog?type=proclamation" target="_blank">官方公告</a>
                    </p>
                    <p class="link isSubUser">
                        <a href="https://vip.zb.cn/u/traderPlan" target="_blank">做市商计划</a>
                    </p>
                    <p class="link isSubUser">
                        <a href="https://vip.zb.cn/u/subaccount" target="_blank">子账号管理</a>
                    </p>
                    <p class="link" id="surveyshow">
                        <a href="https://vip.zb.cn/survey" target="_blank">调查问卷</a>
                    </p>
                </div>
                <div class="bk-footer-contact1">
                    <h5>联系我们</h5>

                    <p class="contlink">服务邮箱：
                        <a href="mail:support@bitkk.com" target="_self">support@zb.cn</a>
                    </p>

                    <p class="contlink">业务邮箱：
                        <a href="mail:info@zb.cn" target="_self">info@zb.cn</a>
                    </p>
                    <p class="contlink">投诉建议：
                        <a href="mail:zbcs@zb.cn" target="_self">zbcs@zb.cn</a>
                    </p>

                </div>
            </div>
            <div class="foot2">
                <b>友情链接</b>
                <a href="https://www.btc123.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/BTC123.png"></a>
                <a href="http://www.bitkan.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/Bitkan.png"></a>
                <a href="http://8btc.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/8btc.png"></a>
                <a href="http://www.etc.tm/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/ETC.png"></a>
                <a href="http://ethfans.org/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/ETHFANS.png"></a>
                <a href="https://www.aicoin.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/AIcoin.png"></a>
                <a href="https://www.botvs.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/BOTVS.png"></a>
                <a href="http://www.jinse.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/JINSE.png"></a>
                <a href="https://www.coldlar.com" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/COLDLAR.png"></a>
                <a href="http://chainfor.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/CHAINFOR.png"></a>
                <a href="http://www.feixiaohao.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/FEIXIAOHAO.png"></a>
                <a href="https://www.kg.com" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/QIANKE.png"></a>
                <a href="https://anybit.io/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/anybitlogo.png"></a>
                <a href="https://www.chainhoo.com" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/CHAINHOO.png"></a>
                <a href="https://www.hyperpay.tech/?lang=zh-cn" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/HPY.png"></a>
                <a href="https://www.coindy.com/" target="_blank"><img src="https://s.zb.cn/statics/img/v3/links/COINDY.png"></a>
            </div>
            <div class="foot3">
                <div style="padding-bottom:20px;">
                    <div class="bk-footer-menu text-left">
                        <p class="footlang pull-right" style="margin-top:-10px; position:absolute; right:0; top:10px;">
                            <a class="btncn" href="javascript:zb.setLan('cn');" title="中文"></a>
                            <a class="btnen" href="javascript:zb.setLan('en');" title="English"></a>
                            <a class="btnar" href="javascript:zb.setLan('ar');" title="العربية"></a>
                            <a class="btnja" href="javascript:zb.setLan('ja');" title="日本語"></a>
                            <a class="btnko" href="javascript:zb.setLan('ko');" title="한국어"></a>
                            <a class="btnth" href="javascript:zb.setLan('th');" title="ภาษาไทย"></a>
                        </p>
                        <div class="copytitle">
                            <span>ZB NETWORK TECHNOLOGY LIMITED</span>
                        </div>

                        <div class="copyright">
                            Copyright © 2018 - ZB.COM All Rights Reserved
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Swiper from '../libs/swiper.js'
export default {
    data () {
        return {
            activeName2: 'first',
            checkActiveName: 'zx',
            tableData: [{
                name: 'BTC',
                nowPrice: 6400,
                highPrice: 6500,
                lowPrice: 6400,
                num: 0.0004,
                priceLv: -1.53,
                gg: '',
                Ksell: '',
                Nsell: '',
            }, {
                name: 'ETH',
                nowPrice: 509,
                highPrice: 510,
                lowPrice: 508,
                num: 0.005,
                priceLv: -0.19,
                gg: '杠',
                Ksell: '',
                Nsell: '',
            }, {
                name: 'BCH',
                nowPrice: 3653.86,
                highPrice: 3800,
                lowPrice: 3042.45,
                num: 11563,
                priceLv: 1.56,
                gg: '',
                Ksell: '',
                Nsell: '',
            }, {
                name: 'LTC',
                nowPrice: 256,
                highPrice: 48662.23,
                lowPrice: 2653,
                num: 0.552,
                priceLv: 18.5,
                gg: '杠',
                Ksell: '',
                Nsell: '',
            }]
        }
    },
    methods: {
        handleClick (tab, event) {
            console.log(tab, event);
        },
        formatter (row, column) {
            return row.address;
        },
        bbjj () {
        },
        checka (event) {
            let type = event.target.getAttribute('type');
            if (type) {
                this.checkActiveName = type;
                if (event.target.tagName === 'SPAN') {
                    $(event.target).parent().addClass('checkActive').siblings().removeClass('checkActive');
                }
            }
        }
    },
    mounted () {
        var swiper = new Swiper('.swiper-container', {
            slidesPerView: 3.2,
            spaceBetween: 20,
            autoplay: true,
            pagination: {
                el: '.swiper-pagination',
                clickable: true
            }
        });
    }
}
</script>


<style lang="less" scoped>
.banner {
    background: url(../assets/images/h-banner-bg.png) repeat 0 0;
    width: 100%;
    height: 600px;
    position: relative;
    .banner-bk {
        width: 100%;
        height: 100%;
        background: url(../assets/images/homebanner-techbk.png) no-repeat center
            center;
        .nav {
            width: 980px;
            height: 80px;
            padding: 43px 15px 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
            .imgg {
                width: 209px;
                height: 47px;
            }
            .lists {
                display: flex;
                align-items: center;
                color: #fff;
                li {
                    padding: 0 10px;
                }
            }
        }
        .video {
            height: 240px;
            img {
                width: 480px;
                margin-top: 10px;
            }
        }
        .swiper-container {
            width: 720px;
            height: 160px;
            margin-top: 60px;
            .swiper-slide {
                width: 214px;
                height: 118px;
                border-radius: 8px;
                overflow: hidden;
                border: 1px solid #bdedff;
            }
            img {
                width: 100%;
                height: 100%;
            }
        }
    }
}
.marketData {
    background-color: #fafafa;
    color: #a7a9b7;
    padding: 15px;
    .checks {
        display: flex;
        font-size: 14px;
        align-items: center;
        border: 1px solid rgb(250, 230, 229);
        border-bottom: none;
        width: 980px;
        margin: auto;
        .check {
            width: 137px;
            padding: 12px 0;
            height: 20px;
            color: #000;
            span {
                display: inline-block;
                width: 100%;
                height: 100%;
            }
        }
        .checkActive {
            background: red;
            color: #fff;
        }
        .search {
            div {
                display: flex;
                align-items: center;
                width: 119px;
                height: 28px;
                input {
                    outline: none;
                    border: none;
                    width: 80px;
                    height: 100%;
                }
                i {
                    width: 20px;
                    height: 14px;
                }
            }
        }
    }
    .eltab {
        border: 1px solid rgb(250, 230, 229);
        width: 980px;
        .el-table {
            font-size: 12px;
            .up {
                color: red;
            }
            .down {
                color: green;
            }
        }
    }
}
.introduce {
    height: 165px;
    padding: 72px 15px;
    background-color: #fafafa;
    display: flex;
    li {
        width: 207.5px;
        padding: 0 18px;
        img {
            height: 46px;
        }
        h4 {
            font-size: 18px;
            color: #000;
        }
        p {
            font-size: 14px;
            color: #a7a9b7;
            line-height: 22px;
        }
    }
}
.bottom {
    background: linear-gradient(to bottom right, #23e4c1, #22b1fe);
    color: #fff;
    text-align: center;
    padding: 72px 0;
    width: 100%;
    height: 333px;
    h3 {
        font-size: 24px;
        margin-top: 20px;
        margin-bottom: 10px;
    }
    h4 {
        margin: 20px 0 60px 0;
        font-size: 12px;
    }
    .list-ld {
        padding: 0 15px;
        display: flex;
        .list-pic {
            width: 110px;
            margin-right: 5px;
            img {
                width: 100%;
            }
        }
        .list-pic1 {
            margin-left: 20px;
        }
        .download-btn-wrap {
            overflow: hidden;
            width: 335px;
            .download-btn-item {
                float: left;
                margin-left: 0;
                width: 150px;
                display: flex;
                align-items: center;
                justify-content: center;
                margin-right: 10px;
                margin-bottom: 10px;
            }
        }
    }
}
.know-more {
    display: flex;
    padding-left: 25px;
}
.foott {
    background-color: #222731;
    .foot1 {
        display: flex;
        height: 225px;
        color: #979ca0;
        box-sizing: border-box;
        border-bottom: 1px solid #37414a;
        padding: 50px 0 0 15px;
        .foot1-col1 {
            width: 215px;
            img {
                width: 105px;
                height: 36px;
            }
        }
        h5 {
            font-size: 16px;
            color: #979ca0;
            margin-top: 0;
            margin-bottom: 20px;
        }
        p {
            margin: 0 0 10px;
            a {
                color: #979ca0;
                text-decoration: none;
                font-size: 12px;
            }
        }
        .bk-footer-contact {
            width: 123px;
        }
        .bk-footer-contact1 {
            text-align: left;
            margin-left: 38px;
            p {
                margin-bottom: 2px;
            }
        }
    }
    .foot2 {
        font-size: 14px;
        padding-top: 30px;
        b {
            font-size: 14px;
            margin-right: 30px;
        }
        a {
            margin-right: 20px;
            cursor: pointer;
            display: inline-block;
            img {
                height: 20px;
            }
        }
    }
    .foot3 {
        padding-bottom: 20px;
        .bk-footer-menu {
            padding-bottom: 20px;
            margin-top: 30px;
            color: #8c98a2;
            position: relative;
            a {
                background: url(../assets/images/guoqibg.png) no-repeat;
                width: 25px;
                height: 17px;
                display: inline-block;
                margin-right: 15px;
                margin-left: 2px;
                border-radius: 3px;
                position: relative;
                top: 4px;
            }
            a.btncn {
                background-position: 0 -3px;
            }
            a.btnen {
                background-position: 0 -54px;
            }
            a.btnar {
                background-position: 0 -318px;
            }
            a.btnja {
                background-position: 0 -349px;
            }
            a.btnko {
                background-position: 0 -408px;
            }
            a.btnth {
                background-position: 0 -377px;
            }
            .copytitle span {
                display: block;
                font-size: 18px;
                font-weight: 400;
                text-align: center;
                color: #fff;
            }
            .copyright {
                color: #63676e;
            }
        }
    }
}
</style>
