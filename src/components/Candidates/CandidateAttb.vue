<template>
    <div class="candidates-item attb"
        :class="{ 'has-warning': hasWarning }"
    >
        <div class="candidates-item-warning" v-if="hasWarning">この物件は現在予約を受付けていません</div>
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
                        <div class="reason-box">ATBB物件</div>
                        <div class="reason-box">{物件種別}</div>
                    </div>
                    <div class="address">
                        <div class="address-icon">
                            <span class="icon-pin"></span>
                        </div>
                        <div class="address-text">{所在地}</div>
                    </div>
                    <div class="house-name">{建物名}</div>
                    <div class="company">
                        <div class="company-box">予約受付会社</div>
                        <div class="company-name">予約受付会社名</div>
                    </div>
                </div>
                <div class="candidates-item-body">
                    <div class="wrap">
                        <div class="house">
                            <div class="house-number">{号棟番号}{区画番号}{部屋番号}</div>
                            <div class="house-row">
                                <div class="house-price">
                                    <div class="house-price-box">賃料/価格(最新)</div>
                                    <div class="house-price-text">9.0万円</div>
                                </div>
                                <div class="house-id-number">
                                    <div class="house-id-number-box">ATBB物件番号</div>
                                    <div class="house-id-number-text">0000000000</div>
                                </div>
                                <div class="house-id-number">
                                    <div class="house-id-number-box">管理番号</div>
                                    <div class="house-id-number-text">0000000000</div>
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
        name: 'CandidateAttb',
        props: {
            candidate: Object,
            checkeds: Array,
            hasWarning: {
                type: Boolean,
                default: false
            },
        }
    }
</script>
