<template>
    <div id="app"
         class="main-wrapper">
        <textarea v-model="value"></textarea>
        <p class="btn"
           @click="showPicker0">多列</p>
        <p class="btn"
           @click="showPicker1">联级</p>
        <p class="btn"
           @click="showPicker4">区域</p>
        <p class="btn"
           @click="showPicker2">时间(内置)</p>
        <p class="btn"
           @click="showPicker3">日期(内置)</p>
        <awesome-picker ref="picker0"
                        :textTitle="picker0.textTitle"
                        :data="picker0.data"
                        :anchor="picker0.anchor"
                        :interceptor="sets"
                        @confirm="handlePicker0Confirm">
        </awesome-picker>

        <awesome-picker ref="picker1"
                        :textTitle="picker1.textTitle"
                        :data="picker1.data"
                        :anchor="picker1.anchor"
                        @confirm="handlePicker1Confirm">
        </awesome-picker>

        <awesome-picker ref="picker2"
                        :textTitle="picker2.textTitle"
                        :type="picker2.type"
                        :anchor="picker2.anchor"
                        @confirm="handlePicker2Confirm">
        </awesome-picker>

        <awesome-picker ref="picker3"
                        :textTitle="picker3.textTitle"
                        :type="picker3.type"
                        :anchor="picker3.anchor"
                        @confirm="handlePicker3Confirm">
        </awesome-picker>

        <awesome-picker ref="picker4"
                        :textTitle="picker4.textTitle"
                        :data="picker4.data"
                        :anchor="picker4.anchor"
                        @confirm="handlePicker4Confirm">
        </awesome-picker>
    </div>
</template>

<script>
    import areaData from './area.js'

    const data1 = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
    const data2 = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']

    export default {
        name: 'app',
        data() {
            return {
                value: null,
                picker0: {
                    anchor: [],
                    textTitle: '多列选择器',
                    data: [data1, data2]
                },
                picker1: {
                    anchor: [{"index":3,"value":"酒店/旅游"},{"index":2,"value":"后勤"}],
                    textTitle: '联级选择器',
                    data: [
                        {
                            "value": "餐饮行业",
                            "index": 0,
                            "children": [
                                {
                                    "value": "服务员",
                                    "index": 0
                                },
                                {
                                    "value": "传菜员",
                                    "index": 1
                                },
                                {
                                    "value": "学徒",
                                    "index": 2
                                },
                                {
                                    "value": "送餐员",
                                    "index": 3
                                },
                                {
                                    "value": "收银员",
                                    "index": 4
                                },
                                {
                                    "value": "营业员",
                                    "index": 5
                                },
                                {
                                    "value": "店长经理",
                                    "index": 6
                                },
                                {
                                    "value": "领班",
                                    "index": 7
                                },
                                {
                                    "value": "吧台服务员",
                                    "index": 8
                                },
                                {
                                    "value": "后厨",
                                    "index": 9
                                },
                                {
                                    "value": "厨师",
                                    "index": 10
                                },
                                {
                                    "value": "厨师长",
                                    "index": 11
                                },
                                {
                                    "value": "咖啡师",
                                    "index": 12
                                },
                                {
                                    "value": "茶艺师",
                                    "index": 13
                                },
                                {
                                    "value": "烘培师",
                                    "index": 14
                                },
                                {
                                    "value": "储备管理",
                                    "index": 15
                                },
                                {
                                    "value": "保洁",
                                    "index": 16
                                },
                                {
                                    "value": "勤杂工",
                                    "index": 17
                                },
                                {
                                    "value": "洗碗工",
                                    "index": 18
                                },
                                {
                                    "value": "迎宾",
                                    "index": 19
                                },
                                {
                                    "value": "前台",
                                    "index": 20
                                }
                            ]
                        },
                        {
                            "value": "超市/零售",
                            "index": 1,
                            "children": [
                                {
                                    "value": "营业员",
                                    "index": 0
                                },
                                {
                                    "value": "理货员",
                                    "index": 1
                                },
                                {
                                    "value": "店长",
                                    "index": 2
                                },
                                {
                                    "value": "食品加工",
                                    "index": 3
                                },
                                {
                                    "value": "水产专员",
                                    "index": 4
                                },
                                {
                                    "value": "促销员",
                                    "index": 5
                                },
                                {
                                    "value": "值班",
                                    "index": 6
                                },
                                {
                                    "value": "储备管理",
                                    "index": 7
                                }
                            ]
                        },
                        {
                            "value": "服装/珠宝/化妆品",
                            "index": 2,
                            "children": [
                                {
                                    "value": "导购",
                                    "index": 0
                                },
                                {
                                    "value": "收银员",
                                    "index": 1
                                },
                                {
                                    "value": "店长",
                                    "index": 2
                                },
                                {
                                    "value": "理货员",
                                    "index": 3
                                },
                                {
                                    "value": "储备管理",
                                    "index": 4
                                }
                            ]
                        },
                        {
                            "value": "酒店/旅游",
                            "index": 3,
                            "children": [
                                {
                                    "value": "酒店前台",
                                    "index": 0
                                },
                                {
                                    "value": "迎宾",
                                    "index": 1
                                },
                                {
                                    "value": "后勤",
                                    "index": 2
                                },
                                {
                                    "value": "文员",
                                    "index": 3
                                },
                                {
                                    "value": "保安",
                                    "index": 4
                                },
                                {
                                    "value": "保洁",
                                    "index": 5
                                }
                            ]
                        },
                        {
                            "value": "物流/仓储",
                            "index": 4,
                            "children": [
                                {
                                    "value": "快递员",
                                    "index": 0
                                },
                                {
                                    "value": "分拣员",
                                    "index": 1
                                },
                                {
                                    "value": "配送员",
                                    "index": 2
                                },
                                {
                                    "value": "仓库管理",
                                    "index": 3
                                },
                                {
                                    "value": "配货员",
                                    "index": 4
                                },
                                {
                                    "value": "司机",
                                    "index": 5
                                }
                            ]
                        },
                        {
                            "value": "互联网行业",
                            "index": 5,
                            "children": [
                                {
                                    "value": "在线客服",
                                    "index": 0
                                },
                                {
                                    "value": "接听客服",
                                    "index": 1
                                },
                                {
                                    "value": "售前客服",
                                    "index": 2
                                },
                                {
                                    "value": "售后客服",
                                    "index": 3
                                },
                                {
                                    "value": "外呼客服",
                                    "index": 4
                                },
                                {
                                    "value": "销售专员",
                                    "index": 5
                                },
                                {
                                    "value": "运维专员",
                                    "index": 6
                                },
                                {
                                    "value": "BD专员",
                                    "index": 7
                                },
                                {
                                    "value": "前台",
                                    "index": 8
                                },
                                {
                                    "value": "行政",
                                    "index": 9
                                }
                            ]
                        },
                        {
                            "value": "制造业",
                            "index": 6,
                            "children": [
                                {
                                    "value": "质检员",
                                    "index": 0
                                },
                                {
                                    "value": "普工",
                                    "index": 1
                                },
                                {
                                    "value": "分拣员",
                                    "index": 2
                                },
                                {
                                    "value": "技工",
                                    "index": 3
                                }
                            ]
                        },
                        {
                            "value": "其他",
                            "index": 7,
                            "children": [
                                {
                                    "value": "其他",
                                    "index": 0
                                }
                            ]
                        }
                    ]
                },
                picker2: {
                    anchor: [],
                    textTitle: '时间选择器(内置)',
                    type: 'time'
                },
                picker3: {
                    anchor: [],
                    textTitle: '日期选择器(内置)',
                    type: 'date'
                },
                picker4: {
                    anchor: [],
                    textTitle: '区域选择器',
                    data: areaData
                }
            }
        },
        methods: {
            showPicker0() {
                this.$refs.picker0.show()
            },
            handlePicker0Confirm(v) {
                this.picker0.anchor = v
                this.value = v ? JSON.stringify(v) : null
            },

            showPicker1() {
                this.$refs.picker1.show()
            },
            handlePicker1Confirm(v) {
                this.picker1.anchor = v
                this.value = v ? JSON.stringify(v) : null
            },

            sets(val) {
                console.log(val);
                return false;
            },

            showPicker2() {
                this.$refs.picker2.show()
            },
            handlePicker2Confirm(v) {
                this.picker2.anchor = v
                this.value = v ? JSON.stringify(v) : null
            },

            showPicker3() {
                this.$refs.picker3.show()
            },
            handlePicker3Confirm(v) {
                this.picker3.anchor = v
                this.value = v ? JSON.stringify(v) : null
            },

            showPicker4() {
                this.$refs.picker4.show()
            },
            handlePicker4Confirm(v) {
                this.picker4.anchor = v
                this.value = v ? JSON.stringify(v) : null
            }
        }
    }
</script>

<style lang="scss">
    .main-wrapper {
        padding: 12px;
    }

    textarea {
        height: 88px;
        width: 100%;
        margin-bottom: 12px;
        padding: 12px;
        border: 2px solid #35495d;
        border-radius: 4px;
        box-sizing: border-box;
        outline: none;
        color: #35495d;
        font-size: 14px;
        resize: none;
    }

    .btn {
        width: 100%;
        height: 44px;
        margin-bottom: 12px;
        line-height: 44px;
        text-align: center;
        color: #fff;
        background: #42b983;
    }
</style>
