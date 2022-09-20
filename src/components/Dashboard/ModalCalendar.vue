<template>
    <div class="dashboard-modal-calendar v-2"
        :class="{ active: isActiveModal }"
    >
        <div class="modal-wrap">
            <div class="modal-header">
                <div class="modal-header-back">
                    <v-icon>arrow_back_ios</v-icon>
                    <!-- <span class="icon-arrow-left"></span> -->
                </div>
                <div class="modal-header-close"
                    @click="onCloseModal"
                >
                    <v-icon>cancel</v-icon>
                    <!-- <span class="icon-close-cl-ol">close</span> -->
                </div>
            </div>
            <div class="modal-body">
                <div class="modal-body-tab">
                    <ul class="modal-body-tab-heading">
                        <li v-for="{ index, content, heading } in tabs"
                            :class="{ active: index === currentTab}"
                            @click="handleTabHeadingClick(index)"
                        >
                            {{ heading }}
                        </li>
                    </ul>
                    <div class="modal-body-tab-content"
                        v-for="{ index, contents } in tabs"
                        :class="{ active: index === currentTab }"
                    >
                        <div class="row"
                            v-for="{ k, v } in contents"
                        >
                            <div class="key">{{ k }}</div>
                            <div class="value">{{ v }}</div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <a href="#">詳細を見る</a>            
            </div>  
        </div>  
    </div>
</template>

<script>
    export default {
        name: 'ModalCalendar',
        props: {
            isActiveModal: Boolean,
            onCloseModal: Function,
        },
        data() {
            return {
                currentTab: 1,
                tabs: [
                    { 
                        index: 1, 
                        heading: '概要',
                        contents: [
                            { k: "key 1", v: "value 1" },
                            { k: "key 2", v: "value 2" },
                            { k: "key 3", v: "value 3" },
                            { k: "key 4", v: "value 4" },
                            { k: "key 1", v: "value 1" },
                            { k: "key 2", v: "value 2" },
                            { k: "key 3", v: "value 3" },
                            { k: "key 4", v: "value 4" },
                            { k: "key 1", v: "value 1" },
                            { k: "key 2", v: "value 2" },
                            { k: "key 3", v: "value 3" },
                            { k: "key 4", v: "value 4" },
                            { k: "key 1", v: "value 1" },
                            { k: "key 2", v: "value 2" },
                            { k: "key 3", v: "value 3" },
                            { k: "key 4", v: "value 4" },
                        ]
                    },
                    { 
                        index: 2, 
                        heading: '鍵取り',
                        contents: [
                            { k: "key 2", v: "value 2" },
                            { k: "key 3", v: "value 3" },
                            { k: "key 4", v: "value 4" },
                            { k: "key 5", v: "value 5" },
                        ]
                    },
                    { 
                        index: 3, 
                        heading: 'お客様案内',
                        contents: [
                            { k: "key 3", v: "value 3" },
                            { k: "key 4", v: "value 4" },
                            { k: "key 5", v: "value 5" },
                            { k: "key 6", v: "value 6" },
                        ]
                    },
                ]
            }
        },
        methods: {
            handleTabHeadingClick(index) {
                this.currentTab = index;
            },
        }


    }
</script>

<style lang="scss" scoped>

</style>