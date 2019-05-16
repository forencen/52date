<template>
    <div id="self_box">
        <mt-field label="手机号" placeholder="请输入手机号" type="tel" v-model="user.phone"></mt-field>
        <mt-field label="微信" placeholder="请输入微信号" type="text" v-model="user.wechat"></mt-field>
        <mt-field label="密码" placeholder="请输入密码" type="password" v-model="user.password"></mt-field>
        <mt-field label="确认密码" placeholder="请输入确认密码"
                  type="password" v-model="user.confirmPassword">
        </mt-field>
        <mt-field label="性别" placeholder="请选择"
                  @click.native="clickGender"
                  type="text"
                  v-model="user.gender">
        </mt-field>
        <GenderPicker :isVisible="popupVisible"
                      :gender="user.gender"
                      :slots="genderSlots"
                      @genderChanged="genderChange">
        </GenderPicker>
        <mt-field label="年龄" placeholder="请输入年龄" type="number" v-model="user.age"></mt-field>
        <mt-field label="身高" placeholder="请输入身高" type="number" v-model="user.height"></mt-field>
        <mt-field label="体重" placeholder="请输入体重" type="number" v-model="user.weight"></mt-field>
        <mt-field label="月收入" placeholder="请输入体重" type="number" v-model="user.income"></mt-field>
        <mt-field label="工作地区" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="学历" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="婚姻状态" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="有无小孩" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="职业" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="住房情况" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="买车情况" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="是否吸烟" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="是否喝酒" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="恋爱次数" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
        <mt-field label="有无宠物" placeholder="请选择" type="text" v-model="user.work_address"></mt-field>
    </div>
</template>

<script>
import GenderPicker from '@/components/GenderPicker.vue'

export default {
    name: 'app',
    data: () => {
        return {
            user: {
                phone: null,
                password: null,
                confirmPassword: null,
                gender: 1,
                age: null,
                height: null,
                weight: null,
                income: null,
                work_address: null,
                wechat: null
            },

            username: null,
            popupVisible: false,
            selected: '1',
            genderSlots: [
                {
                    flex: 1,
                    values: [{ name: '男', value: 1 }, { name: '女', value: 2 }],
                    className: 'slot1',
                    valueKey: 'name',
                    textAlign: 'center'
                }
            ],
        };
    },
    components: {
        GenderPicker
    },
    methods: {
        genderChange: function(value) {
            this.user.gender = value
        },
        clickGender: function () {
            this.popupVisible = !this.popupVisible;
        },
        genderTranslation: function (gender) {
            return gender === 1 ? '男' : '女'
        }

    }
}
</script>

<style scoped>

</style>
