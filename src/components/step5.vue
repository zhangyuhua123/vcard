<template>
    <div class='fullpage'>
        <img src="../assets/images/Combined Shape.png" alt="tutorabc" class="logo">
        <div class="lunbo">
            <div class="left">
                <swiper :options="swiperOption" ref="mySwiper">
                    <!-- slides -->
                    <swiper-slide>
                        <div class='yao'></div>
                    </swiper-slide>
                    <swiper-slide>
                        <div class='lee'></div>
                    </swiper-slide>
                    <!-- Optional controls -->
                    <div class="swiper-pagination" slot="pagination"></div>
                </swiper>
                <div class="easy-introduct-y" v-if='isyaoming'>
                    <span class="title">无论你是谁，无论你在哪里，只要你相信语言的力量，在tutorabc,你就可以站在世界的舞台， 让世界与你对话。
                    </span>
                    <p class='represent'>
                        <strong>——姚明</strong>品牌代言人</p>
                </div>
                <div class="easy-introduct-l" v-if='isyaoming==0'>
                    <span class="title">语言是最精彩的事物、是最迫切需要的技能。我们要有战胜者的态度，把握机遇，绝境逢生。激活你的英语力，是站上国际舞台的关键力。
                    </span>
                    <p class='represent' style="left:192px">
                        <strong>——李昌钰</strong>华人第一神探</p>
                </div>
            </div>
        </div>
        <div class="right">
            <div class='contact'>
                <span>开卡遇到的问题？</span>
                <br/>
                <strong style="color:#4a4a4a;font-weight:normal">
                    <span>
                        <svg style="width:25px;height:25px" viewBox="0 0 18 18" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <!-- Generator: Sketch 44.1 (41455) - http://www.bohemiancoding.com/sketch -->

                            <title>Page 1</title>
                            <desc>Created with Sketch.</desc>
                            <defs></defs>
                            <g id="Symbols" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                <g id="Nav/1366" transform="translate(-1324.000000, -64.000000)" stroke="#231815">
                                    <path d="M1337.8457,81 C1336.83361,80.6688227 1335.76416,80.4536198 1334.81939,79.9862152 C1330.84357,78.0195179 1327.86524,75.0099573 1325.85215,71.0601565 C1325.35431,70.0834835 1325.01001,69.0439015 1325.00005,67.924778 C1324.99021,66.8242105 1326.40102,65.1082439 1327.49763,65.005734 C1327.88617,64.9695274 1328.42893,65.1063204 1328.68023,65.3726652 C1329.30287,66.0329831 1329.86973,66.7721635 1330.32287,67.5580731 C1330.71696,68.2414727 1330.40592,68.8976042 1329.87946,69.4491891 C1328.97452,70.3968969 1328.92315,70.71246 1329.6707,71.7722951 C1330.87401,73.4786444 1332.3492,74.9274741 1334.0405,76.152615 C1334.23703,76.2950653 1334.46185,76.4002908 1334.67875,76.5126444 C1335.21088,76.7884934 1335.65045,76.7226427 1336.09409,76.2671184 C1337.20971,75.1214057 1337.89085,75.06257 1339.1979,75.9945505 C1339.68262,76.3400973 1340.13837,76.7519474 1340.52352,77.2048693 C1341.00212,77.767882 1341.02362,78.4513947 1340.56968,79.0319449 C1339.88108,79.9126705 1339.23219,80.9030342 1337.89447,80.8496295 C1337.87817,80.899753 1337.86199,80.9498765 1337.8457,81 L1337.8457,81 Z" id="Page-1"></path>
                                </g>
                            </g>
                        </svg>
                    </span>4006-30-30-30
                </strong>
            </div>
            <div class="center" id='jj'>
                <div class="introduce">
                    <h2 style="color:#4a4a4a">启用tutorabc英语学习卡</h2>
                    <h6>简单三步,立即启用!</h6>
                </div>
                <div class="step1" v-if='step1vi'>
                    <div class="serialnumber">
                        <el-steps :active="active" finish-status="success">
                            <el-step title="输入序列号"></el-step>
                            <el-step title="绑定账户"></el-step>
                            <el-step title="成功开卡"></el-step>
                        </el-steps>
                    </div>
                    <h3 style="margin-top:40px;font-weight:normal;color:'#333';padding-left:2px;">卡片序列号</h3>
                    <!-- <el-input v-model="input" placeholder="请输入10位序列号，不区分大小写" ></el-input> -->
                    <el-form :model="ruleForm" :rules="rules" ref="ruleForm">
                        <el-form-item label="" prop="num">
                            <el-input v-model="ruleForm.num" placeholder="请输入8位序列号" @focus="done"></el-input>
                        </el-form-item>
                    </el-form>
                    <button ref='btnStep1' style="margin-top: 30px;" @click="showStep1" :class="ruleForm.num!=0?'el-button':'err-button'" :disabled="disabled1">下一步</button>
                    <div v-if='errmsg' class="err">{{msg}}</div>
                    <loading v-if="loadingState"></loading>
                </div>
                <div class="step2" v-if='step2vi'>
                    <div class="serialnumber">
                        <el-steps :active="active" finish-status="success">
                            <el-step title=" 输入序列号"></el-step>
                            <el-step title="绑定账户"></el-step>
                            <el-step title=" 成功开卡"></el-step>
                        </el-steps>
                    </div>
                    <h3 class="name" style="padding-left:2px;font-weight:normal;color:'#333'">姓名</h3>
                    <el-form :model="input" ref="numberValidateForm" style="position:relative">
                        <!-- <el-form-item label="" prop="name" :rules="[
                                                          { required: true, message: '姓名不能为空'},
                                                         
                                                        ]">
                                <el-input type="name" v-model="input.name" placeholder="请输入您的姓名"  @blur='test1' ></el-input>
                            </el-form-item> -->
                        <el-form-item label="" prop="name">
                            <el-input type="name" v-model="input.name" placeholder="请输入您的姓名" @blur='test1'></el-input>
                        </el-form-item>
                        <div class="el-form-item__error" v-show='plasewhitename'>姓名不能为空</div>
                        <div class="el-form-item__error" v-show='plasewhitename1'>请输入中文或英文字符</div>
                    </el-form>
                    <h3 style="margin-top:25px;padding-left:2px;font-weight:normal;color:'#333'">手机号码</h3>
                    <div style="position:relative">
                        <el-form :model="ruleForm" :rules="rules" ref="ruleForm">
                            <el-form-item label="" prop="tel" id='tel'>
                                <el-input v-model="ruleForm.tel" placeholder="请输入11位手机号码" @blur='test'></el-input>
                            </el-form-item>
                            <div class="el-form-item__error" v-show='plasewhitetell'>请输入11位手机号</div>
                            <div class="el-form-item__error" v-show='plasewhitetell0'>手机号不能为空</div>
                        </el-form>
                    </div>
                    <h3 style="margin-top:25px;padding-left:2px;font-weight:normal;color:'#333'">验证码</h3>
                    <div style="position:relative">
                        <el-form :model="ruleForm" :rules="rules" ref="ruleForm">
                            <el-form-item label="" prop="yzm" id='yzm'>
                                <el-input v-model="ruleForm.yzm" placeholder="请输入您收到的短信验证码" @focus="done"></el-input>
                            </el-form-item>
                        </el-form>
                        <button class="yanzheng" @click="yanzheng" style='border:none' :disabled='isdisableyzm'>{{fetchCodemsg}}</button>
                        <div v-if='errmsg' class="err">{{msg}}</div>
                    </div>
                    <input type="checkbox" class="check" v-model="checked">我已经阅读并同意接受
                    <a href='https://www.tutorabc.com.cn/Home/Privacy' target="_Blank" style="color:red">《隐私条款》</a>与
                    <a href='https://www.tutorabc.com.cn/Home/Security' target="_Blank" style="color:red">《服务条款》</a>
                    <button @click="showStep2" :disabled="disabled2" :class="input.name === '' || ruleForm.tel === '' || ruleForm.yzm === ''||checked==''?'err-button':'el-button btn'">下一步</button>
                     <loading v-if="loadingState">11111</loading>
                     
                </div>

                <div class="step3" v-if='step3vi'>
                    <div class="serialnumber">
                        <el-steps :active="active" finish-status="success">
                            <el-step title="输入序列号"></el-step>
                            <el-step title="绑定账户"></el-step>
                            <el-step title="成功开卡"></el-step>
                        </el-steps>
                    </div>
                    <div class="share">
                        <div class="share-logo"></div>
                        <span>{{ProductName}}</span>
                        <h2 id='num'>{{Classes}}
                            <strong style="font-size:24px">节</strong>
                        </h2>
                        <p>有效期: 即日起至{{ExpireDate}}</p>
                    </div>
                    <span class='success'>开卡成功，恭喜您获得,登录tutorabc会员中心上课吧！</span>
                    <el-button class="btn" @click='showStep3'>立即上课</el-button>
                     <loading v-if="loadingState"></loading>
                </div>

            </div>
        </div>
    </div>
</template>
<style>
@import "../assets/css/step2.css";
@import "../assets/css/step1.1.css";
@import "../assets/css/step3.1.css";
</style>
<script>
export default {
    data() {
        return {
              Classes:'',
            ProductName:'',
            ExpireDate:'',
            loadingState: 0,
            plasewhitetell0: 0,
            plasewhitetell: 0,
            plasewhitename: 0,
            plasewhitename1: 0,
            step1vi: 1,
            step2vi: 0,
            step3vi: 0,
            isyaoming: 1,
            swiperOption: {
                loop: true,
                autoplay: 3000,
                setWrapperSize: true,
                autoHeight: true,
                errmsg: 0,
                pagination: '.swiper-pagination',
                debugger: true,
                onSlideChangeEnd: swiper => {
                    //console.log('onSlideChangeEnd', swiper.realIndex);
                    if (swiper.realIndex == '1') {
                        this.isyaoming = 0;
                    } else if (swiper.realIndex == '0') {
                        this.isyaoming = 1;
                    }
                }
            },
            checked: '',
            msg: '',
            input: '',
            isdisableyzm: false,
            active: 0,
            errmsg: 0,
            input: {
                name: ''
            },
            fetchCodemsg: '点击发送验证码',
            ruleForm: {
                tel: '',
                yzm: '',
                num: ''
            },
            rules: {
                num: [
                    { required: true, message: '卡券不能为空', trigger: 'blur' },
                    // { min: 11,max: 11, message: '请输入11位号码', trigger: 'blur' }
                ],
                // tel: [
                //     { required: true, message: '手机号不能为空', trigger: 'blur' },
                //     { min: 11, max: 11, message: '请输入正确11位手机号', trigger: 'blur', }
                // ],
                yzm: [
                    { required: true, message: '请输入6位的验证码', trigger: 'blur', }
                ]
            },
        }
    },
    created: function () {
       // this.active++;
       
       
    },
    computed: {
        disabled1: function() {
            //conosle.log(this.ruleForm.num);
            return this.ruleForm.num == '' ? 'disabled' : false;
        },
        disabled2: function() {
            console.log(this.checked)
            if (this.input.name === '' || this.ruleForm.tel === '' || this.ruleForm.yzm === '' || this.checked == '') {
                return 'disabled'
            } else {
                return false;
            }
        },
        disabled1: function() {
            //conosle.log(this.ruleForm.num);
            return this.ruleForm.num == '' ? 'disabled' : false;
        }
    },
    methods: {
        test() {

            if ((/^1[3,4,5,7,8]{1}[0-9]{9}$/).test(this.ruleForm.tel)) {
                this.plasewhitetell0 = 0;
                this.plasewhitetell = 0
            } else if (this.ruleForm.tel == '') {
                this.plasewhitetell0 = 1;
                this.plasewhitetell = 0;
            } else {
                this.plasewhitetell = 1;
                this.plasewhitetell0 = 0;
            }
        },
        test1() {
            if (this.input.name == '') {
                this.plasewhitename = 1;
                this.plasewhitename1 = 0;
            } else if ((/^[A-Za-z]{1,10}$|^[A-Za-z]{1,10}(?:·[A-Za-z]{1,10})+$|^[\u4E00-\u9FA5]{1,15}$|^[\u4E00-\u9FA5]{1,15}(?:·[\u4E00-\u9FA5]{1,15})+$/).test(this.input.name)) {
                // this.plasewhitename=1;
                this.plasewhitename1 = 0;
                this.plasewhitename = 0;
            } else {
                this.plasewhitename1 = 1;
                this.plasewhitename = 0;
            }
        },
        done() {
            this.errmsg = 0;
        },
        showStep1: function() {
            var that = this;
            //alert(1);
            console.log(this.step1vi);
            this.loadingState = 1;
            //"http://172.16.233.55:5002/json/reply/CheckCardUseStateRequest"  getcordUrl
            //debugger;
            this.$http.jsonp(getcordUrl,
                {
                    params: {
                        "ActivateCode": this.ruleForm.num,
                        "Token": "C9E6438E-46FA-4F05-8252-903F06885104",
                        "ClientIp": "192.168.87.124"
                    }
                }).then((res) => {
                    this.loadingState = 0;
                    var res1 = JSON.parse(res.bodyText);
                    // console.log('ActiveCode: ', this.ruleForm.num)
                    //console.log(res1);     
                    if (res1.Code != '1') {
                        this.msg = res1.ErrMsg;
                        that.errmsg = 1;
                        console.log(that.$refs.btnStep1);
                        // that.$refs.btnStep1.attributes();
                        // setTimeout("" , 3000); 
                    } else if (res1.Code == '1') {
                        this.active++;
                        this.step2vi = 1;
                        this.step1vi = 0;
                        //if(this.active++ > 2)this.active =0;
                    }
                }).catch((res) => { res.status })
        },
        showStep2: function() {
            this.loadingState = 1;
            var that = this;
            //http://172.16.233.55:5002/json/reply/ActivateCardRequest
            this.$http.jsonp(getActivateCard, {
                params: {
                    "CName":this.input.name,
                    "ActivateCode":this.ruleForm.num,
                    "Mobile":this.ruleForm.tel,
                    "VerifyCode":this.ruleForm.yzm,
                    "Token":"C9E6438E-46FA-4F05-8252-903F06885104",
                    "ClientIp":"192.168.87.124"

                },
            }).then((res) => {
                this.loadingState = 0;
                var res1 = JSON.parse(res.bodyText);
                console.log(res1);
                console.log(res1.Data.ProductName);
                this.ProductName = res1.Data.CardName;
                this.ExpireDate = res1.Data.ExpireDate;
                this.Classes =res1.Data.Classes;
                if (res1.Code == '1') {
                    this.step2vi = 0;
                    this.step3vi = 1;
                    this.active++;
                    this.active++;
                } else if (res1.Code != "1") {
                    this.msg = res1.ErrMsg;
                    this.errmsg = 1;
                    // alert(res1.ErrMsg);
                }
            })
        },
        yanzheng: function() {
            if (this.ruleForm.tel == '') {
                // this.isdisableyzm=true;
                alert('请输入手机号码');
                return;
            }
            console.log('验证码已发送,请注意查收');
            //console.log(1)
            let sec = 60;
            var that = this;
            for (let i = 0; i <= 60; i++) {
                window.setTimeout(function() {
                    if (sec != 0) {
                        that.fetchCodemsg = sec + 's后';
                        sec--;
                        that.isdisableyzm = true;
                    } else {
                        that.fetchCodemsg = '点击发送验证码';
                        that.isdisableyzm = false;
                    }
                }, 1000 * i)
            }
            //http://172.16.233.55:5002/json/reply/SendSmsVerifyCodeRequest
            this.$http.jsonp(getvalidation,
                {
                    params: {
                        "Mobile": this.ruleForm.tel,
                        "Token": "C9E6438E-46FA-4F05-8252-903F06885104",
                        "ActivateCode": this.ruleForm.num,
                        "ClientIp": "192.168.87.124"
                    }
                }).then((res) => {
                }).catch((res) => { res.status })
        },
        showStep3() {
            //alert(1);
             this.loadingState = 1;
            window.location.href = 'https://www.tutorabc.com.cn/';
        }
    }
}
var getcordUrl = "";
var getvalidation = '';
var getActivateCard = '';
if (window.location.href.indexOf("stage") > -1) {
    getcordUrl = 'http://openapi.mls.Weitutorstage.com/vmdopenservice/json/reply/CheckCardUseStateRequest';
    getvalidation = 'http://openapi.mls.Weitutorstage.com/vmdopenservice/json/reply/SendSmsVerifyCodeRequest';
    getActivateCard = 'http://openapi.mls.Weitutorstage.com/vmdopenservice/json/reply/ActivateCardRequest';
} else if (window.location.host.indexOf("pre") > -1) {
    getcordUrl = 'http://openapi.mls.Weitutorpre.com/vmdopenservice/json/reply/CheckCardUseStateRequest';
    getvalidation = 'http://openapi.mls.Weitutorpre.com/vmdopenservice/json/reply/SendSmsVerifyCodeRequest';
    getActivateCard = 'http://openapi.mls.Weitutorpre.com/vmdopenservice/json/reply/ActivateCardRequest';
} else if (window.location.host.indexOf("127") > -1) {
    getcordUrl = 'http://172.16.233.55:5002/json/reply/CheckCardUseStateRequest';
    getvalidation = 'http://172.16.233.55:5002/json/reply/SendSmsVerifyCodeRequest';
    getActivateCard = 'http://172.16.233.55:5002/json/reply/ActivateCardRequest';
} else  {
     getcordUrl = 'https://openapi-mls.tutorabc.com.cn/vmdopenservice/json/reply/CheckCardUseStateRequest';
    getvalidation = 'https://openapi-mls.tutorabc.com.cn/vmdopenservice/json/reply/SendSmsVerifyCodeRequest';
    getActivateCard = 'https://openapi-mls.tutorabc.com.cn/vmdopenservice/json/reply/ActivateCardRequest';

}
//http://172.16.233.55:5002
</script>
