<template>
    <div>
        <mt-popup
            v-model="popupVisible"
            popup-transition="popup-fade"
            position="bottom" style="width: 100%;">
            <div style="width: 100%;">
                <mt-picker :slots="slots"  valueKey="name" @change="onValuesChange"></mt-picker>
            </div>
        </mt-popup>
    </div>
</template>

<script>
export default {
    name: 'GenderPicker',
    props: ['select_value', 'popupVisible'],
    data() {
        return {
            slots: [
                {
                    flex: 1,
                    values: [{ name: '男', value: 1 }, { name: '女', value: 2 }],
                    className: 'slot1',
                    valueKey: 'name',
                    textAlign: 'center'
                }
            ]
        }
    },
    methods: {
        onValuesChange: function (picker, values) {
            this.$emit('valueChanged', values[0].value);
        }
    },
    watch: {
        slots: function (v) {
            // console.log('---')
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
