<template>
    <div class="about">
        <mt-header title="52Date">
            <mt-button icon="more" slot="right"></mt-button>
        </mt-header>
        <mt-navbar v-model="selected">
            <mt-tab-item id="1">基本资料</mt-tab-item>
            <mt-tab-item id="2">择偶条件</mt-tab-item>
        </mt-navbar>
        <mt-tab-container v-model="selected">
            <mt-tab-container-item id="1">
                <mt-field label="手机号" placeholder="请输入手机号" type="tel" v-model="userInfo.phone"></mt-field>
                <mt-field label="微信" placeholder="请输入微信号" type="text" v-model="userInfo.wechat"></mt-field>
                <mt-field label="密码" placeholder="请输入密码" type="password" v-model="userInfo.password"></mt-field>
                <mt-field label="确认密码" placeholder="请输入确认密码"
                          type="password" v-model="userInfo.confirmPassword">
                </mt-field>
                <mt-field label="性别" placeholder="请选择"
                          @focus.native.capture="genderVisible = true"
                          @blur.native.capture="genderVisible = false"
                          type="text"
                          :value="genderTranslation(userInfo.gender)">
                </mt-field>
                <gender-picker :popupVisible="genderVisible"
                           :select_value="userInfo.gender"
                           @valueChanged="genderChange">
                </gender-picker>
                <mt-field label="年龄" placeholder="请输入年龄" type="number" v-model="userInfo.age"></mt-field>
                <mt-field label="身高" placeholder="请输入身高" type="number" v-model="userInfo.height"></mt-field>
                <mt-field label="体重" placeholder="请输入体重" type="number" v-model="userInfo.weight"></mt-field>
                <mt-field label="月收入" placeholder="请输入体重" type="number" v-model="userInfo.income"></mt-field>
                <mt-field label="工作地区" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="学历" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="婚姻状态"
                          @focus.native.capture="marryVisible = true"
                          @blur.native.capture="marryVisible = false"
                          placeholder="请选择"
                          type="text"
                          :value="trueOrFalseTranslation(userInfo.marry)"></mt-field>
                <true-or-false-picker :popupVisible="marryVisible"
                                      :select_value="userInfo.marry"
                                      @valueChanged="marryChange">
                </true-or-false-picker>
                <mt-field label="有无小孩"
                          @focus.native.capture="childVisible = true"
                          @blur.native.capture="childVisible = false"
                          placeholder="请选择"
                          type="text"
                          :value="trueOrFalseTranslation(userInfo.child)"></mt-field>
                <true-or-false-picker :popupVisible="childVisible"
                                      :select_value="userInfo.child"
                                      @valueChanged="childChange">
                </true-or-false-picker>
                <mt-field label="职业" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="住房情况" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="买车情况" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="是否吸烟" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="是否喝酒" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="恋爱次数" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="有无宠物" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
            </mt-tab-container-item>
            <mt-tab-container-item id="2">
                <mt-field label="性别" placeholder="请选择"
                          @focus.native.capture="genderVisible = true"
                          @blur.native.capture="genderVisible = false"
                          type="text"
                          :value="genderTranslation(userInfo.gender)">
                </mt-field>
                <gender-picker :popupVisible="genderVisible"
                               :select_value="userInfo.gender"
                               @valueChanged="genderChange">
                </gender-picker>
                <mt-field label="年龄" placeholder="请输入年龄" type="number" v-model="userInfo.age"></mt-field>
                <mt-field label="身高" placeholder="请输入身高" type="number" v-model="userInfo.height"></mt-field>
                <mt-field label="体重" placeholder="请输入体重" type="number" v-model="userInfo.weight"></mt-field>
                <mt-field label="月收入" placeholder="请输入体重" type="number" v-model="userInfo.income"></mt-field>
                <mt-field label="工作地区" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="学历" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="婚姻状态" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="有无小孩" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="职业" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="住房情况" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="买车情况" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="是否吸烟" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="是否喝酒" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="恋爱次数" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
                <mt-field label="有无宠物" placeholder="请选择" type="text" v-model="userInfo.work_address"></mt-field>
            </mt-tab-container-item>
        </mt-tab-container>
    </div>
</template>

<script>
import { mapState } from 'vuex';
import GenderPicker from '@/components/GenderPicker.vue'
import TrueOrFalsePicker from '@/components/TrueOrFalsePicker.vue'
// import { SelfInfo } from '@/components/SelfInfo.vue'

export default {
    name: 'about',
    props: {
        msg: String
    },
    components: {
        GenderPicker, TrueOrFalsePicker
    },
    created() {
    },
    data() {
        return {
            userInfo: {
                phone: null,
                password: null,
                confirmPassword: null,
                gender: '男',
                age: null,
                height: null,
                weight: null,
                income: null,
                work_address: null,
                marry: null,
                child: null,
                wechat: null
            },
            userInfoName: null,
            genderVisible: false,
            childVisible: false,
            marryVisible: false,
            selected: '1'
        };
    },
    computed: {
        // vuex modules 中的gettes,state获取方式，modules中要定义namespaced: true
        // ...mapGetters('login',['user','token']),
        ...mapState('login', ['user', 'token'])
    },
    methods: {
        genderChange(value) {
            this.userInfo.gender = value
        },
        marryChange(value) {
            this.userInfo.marry = value
        },
        childChange(value) {
            this.userInfo.child = value
        },
        genderTranslation(gender) {
            return gender === 1 ? '男' : '女'
        },
        trueOrFalseTranslation(v) {
            return v ? '是' : '否'
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
