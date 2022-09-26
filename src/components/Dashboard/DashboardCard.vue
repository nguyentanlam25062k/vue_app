<template>
    <div class="dashboard-card-item">
        <div class="card-header">
            <div class="card-header-row">
                <div class="card-header-col">
                    <div class="box-outline-blue">物件種別</div>
                    <div class="address">
                        <div class="address-icon">
                            <!-- <span class="icon-pin"></span> -->
                            <span class="material-icons">location_on</span>
                        </div>
                        <div class="address-text">所在地</div>
                    </div>
                    <div class="building-name">建物名</div>
                    <div class="key">
                        <div class="key-icon">
                            <!-- <span class="icon-key"></span> -->
                            <span class="material-icons">key</span>
                        </div>
                        <div class="key-text">
                            <p>鍵取り</p>
                            <p>立ち会い</p>
                            <p>現地対応</p>
                            <p>その他</p>
                        </div>
                    </div>
                    <div class="row-box">
                        <div class="col-box">
                            <div class="box-blue">賃料/価格(最新)</div>
                            <div class="price">9.0万円</div>
                        </div>
                        <div class="col-box">
                            <div class="box-outline-gray">案内予約物件台帳番号</div>
                            <div class="number">0000000000</div>
                        </div>
                    </div>
                </div>
                <div class="card-header-col">
                    <div class="status">
                        <div class="status-text">事前準備タスクの状況</div>
                        <div class="status-list">
                            <div class="status-item">
                                <div class="status-item-header">
                                    <div class="status-item-text">物件情報</div>
                                    <div class="status-item-icon-new">NEW</div>
                                </div>
                                <div class="status-item-body">
                                    <!-- <span class="icon-check"></span> -->
                                    <span class="material-icons">done</span>
                                </div>
                            </div>
                            <div class="status-item">
                                <div class="status-item-header">
                                    <div class="status-item-text">物件情報</div>
                                    <div class="status-item-icon-new">NEW</div>
                                </div>
                                <div class="status-item-body">
                                    <!-- <span class="icon-check"></span> -->
                                    <span class="material-icons">done</span>
                                </div>
                            </div>
                            <div class="status-item">
                                <div class="status-item-header">
                                    <div class="status-item-text">物件情報</div>
                                    <div class="status-item-icon-new">NEW</div>
                                </div>
                                <div class="status-item-body">
                                    <!-- <span class="icon-check"></span> -->
                                    <span class="material-icons">done</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="card-header-row">
                <div class="history">
                    <p>物件変更履歴</p>
                </div>
            </div>
            <div class="card-header-row">
                <div class="link">
                    <p>物件情報（最新）を見る</p>
                </div>
            </div>
        </div>
        <div class="card-body">
            <div class="card-child">
                <div class="card-child-header">
                    <div class="heading">
                        <div class="heading-icon">
                            <span class="material-icons">calendar_month</span>
                            <!-- <span class="icon-date-pick"></span> -->
                        </div>
                        <div class="heading-outline-blue">内見理由</div>
                        <div class="heading-text">
                            <p>内見日</p>
                            <p>内見時間from</p>
                            <p>-</p>
                            <p>内見時間to</p>
                        </div>
                    </div>
                    <div class="notify">
                        <div class="notify-icon">
                            <span class="icon-notice"></span>
                        </div>
                        <div class="notify-text">この物件に対して重複する内見予定が入っています。変更が必要な場合は詳細から変更を行ってください。</div>
                    </div>
                    <div class="notify">
                        <div class="notify-icon">
                            <span class="icon-notice"></span>
                        </div>
                        <div class="notify-text">詳細を確認し、予約対応担当者を割り当ててください。</div>
                    </div>
                </div>
                <div class="card-child-body">
                    <div class="people">
                        <div class="people-item">
                            <div class="people-item-box-blue">予約対応担当者</div>
                            <div class="people-item-text">予約受付会社名</div>
                            <div class="people-item-text">予約対応担当者</div>
                        </div>
                        <div class="people-item">
                            <div class="people-item-box-blue">案内担当者</div>
                            <div class="people-item-text">案内予約会社名</div>
                            <div class="people-item-text">案内担当者</div>
                        </div>
                    </div>
                    <div class="history">
                        <p>物件変更履歴</p>
                    </div>
                    <div class="link">
                        <div class="link-btn">
                            <div class="btn-link v-2 btn-primary">詳細を見る</div>
                            <span class="icon-external"></span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    name: 'DashboardCard',
    data() {
        return {
            checkeds: [1, 2, 3]
        }
    },
}
</script>
<style lang="css" scoped>
</style>