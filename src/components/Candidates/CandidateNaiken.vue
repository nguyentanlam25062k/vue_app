<template>
    <div class="candidates-item naiken"
        :class="{ 'has-warning': warning.hasWarning }"
    >
        <div class="candidates-item-warning" v-if="warning.message">この物件は現在予約を受付けていません</div>
        <div class="candidates-item-wrap">
            <div class="candidates-item-left">
                <label class="candidates-checkbox">
                    <input 
                        type="checkbox" 
                        :checked="checkeds.includes(candidate.id)" 
                        :value="candidate.id"
                        @change="$emit('cadidateChecked', candidate.id)"
                    >
                    <span class="checkmark"></span>
                </label>
            </div>
            <div class="candidates-item-right">
                <div class="candidates-item-heading">
                    <div class="reason">
                        <div class="reason-box">内見専用物件</div>
                        <div class="reason-box">{{ candidate.house_classification }}</div>
                    </div>
                    <div class="address">
                        <div class="address-icon">
                            <span class="icon-pin"></span>
                        </div>
                        <div class="address-text">{{ candidate.address }}</div>
                    </div>
                    <div class="house-name">{{ candidate.name }}</div>
                    <div class="company">
                        <div class="company-box">予約受付会社</div>
                        <div class="company-name">予約受付会社名</div>
                    </div>
                </div>
                <div class="candidates-item-body">
                    <div class="wrap">
                        <div class="c-row">
                            <div class="c-col">
                                <div class="house">
                                    <div class="house-number">{{ candidate.block }}={{ candidate.room }}-{{ candidate.lot }}</div>
                                    <div class="house-row">
                                        <div class="house-price">
                                            <div class="house-price-box">賃料/価格(最新)</div>
                                            <div class="house-price-text">{{ candidate.price }}</div>
                                        </div>
                                        <div class="house-preview"
                                            :class="{ 'disable' : !takePicture.isActive }"
                                        >
                                            <div class="house-preview-box">写真撮影内見</div>
                                            <div class="house-preview-text">{{ takePicture.message }}</div>
                                            <div class="house-preview-icon">
                                                <span class="icon-check"></span>
                                            </div>
                                        </div>
                                        <div class="house-id-number">
                                            <div class="house-id-number-box">案内予約物件台帳番号</div>
                                            <div class="house-id-number-text">{{ candidate.address }}</div>
                                        </div>
                                    </div>  
                                    <div class="house-view-time">
                                        <div class="house-view-time-box">内見受付可能期間</div>
                                        <div class="house-view-time-text">yyyy.mmm.dd~yyyy.mmm.dd</div>
                                    </div>
                                    <div class="house-not-view-time">
                                        <div class="house-not-view-time-box">内見不可日</div>
                                        <div class="house-not-view-time-text">yyyy.mm.dd/yyyy.mm.dd/yyyy.mm.dd/yyyy.mm.dd/yyyy.mm.dd/yyyy.mm.dd</div>
                                    </div>
                                </div>
                            </div>
                            <div class="c-col">
                                <div class="setting">
                                    <div class="setting-item">
                                        <div class="setting-item-text">内見受付情報</div>
                                        <div class="setting-item-box">
                                            <span class="icon-check"></span>
                                        </div>
                                    </div>
                                    <div class="setting-item">
                                        <div class="setting-item-text">鍵情報</div>
                                        <div class="setting-item-box"
                                            :class="{ 'disable' : !isActiveIconChecked }"
                                        >
                                            <span class="icon-check"></span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="view-detail">
                            <div class="view-detail-btn">案内候補一覧から削除する</div>
                            <div class="view-detail-link">
                                <a href="#" class="text">詳細を見る</a>
                                <span class="icon-external"></span>
                            </div>
                        </div>
                    </div>
                </div>      
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CandidateNaiken',
        props: {
            candidate: Object,
            checkeds: Array,
        },
        computed: {
            warning() {
                let hasWarning = false, message = '';

                if (this.candidate.deleted_at !== null) {
                    hasWarning = true;
                    message = `この物件は削除されました`;
                }

                if (this.candidate.setting_info.is_appointment == 0) {
                    hasWarning = true;
                    message = `この物件は現在予約を受付けていません`;
                }
            
                return { message, hasWarning };
            },
            takePicture() {
                let isActive = false, message = `不可`;
                
                if (this.candidate.setting_info.is_take_pictures) {
                    isActive = true;
                    message = `可`
                }
                
                return { isActive, message };
            },
            isActiveIconChecked() {
                return this.candidate.is_key_info;
            }
        }
    }
</script>

