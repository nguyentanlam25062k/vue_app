<template>
    <div>
        <div class="dashboard-uncompleted-card-item-pc">
            <div class="card-heading">
                <div class="card-heading-item">ユーザー名</div>
                <div class="card-heading-item">携帯電話番号</div>
                <div class="card-heading-item">メールアドレス</div>
                <div class="card-heading-item">権限</div>
                <div class="card-heading-item">権限</div>
            </div>
            <div class="card-body">
                <div class="card-body-list" v-for="num in [1, 2, 3, 4, 5]">
                    <div class="card-body-item">田中 はじめ</div>
                    <div class="card-body-item">000000000</div>
                    <div class="card-body-item">tanaka@hogehoge.com</div>
                    <div class="card-body-item">一般利用者</div>
                    <div class="card-body-item">
                        <div class="card-body-item-link">詳細を見る</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="dashboard-uncompleted-card-item">
            <div class="card-header">
                <div class="card-header-time">yyyy.mm.ddHh:mm-hh:mm</div>
                <div class="card-header-box">{内見理由}</div>
            </div>
            <div class="card-body">
                <div class="card-body-item">
                    <div class="card-body-item-key">建物名</div>
                    <div class="card-body-item-value">品川レジデンス901号室</div>
                </div>
                <div class="card-body-item">
                    <div class="card-body-item-key">案内予約会社</div>
                    <div class="card-body-item-value">株式会社△△不動産　吉田 鋼太郎</div>
                </div>
                <div class="card-body-item">
                    <div class="card-body-item-key">予約対応担当者</div>
                    <div class="card-body-item-value">田中 太郎</div>
                </div>
            </div>
            <div class="card-footer">
                <div class="card-footer-btn btn-sm v-2 btn-primary">内見完了する（強制）</div>
            </div>
        </div>
    </div>
</template>
<script>

export default {
    name: 'DashboardUncompletedCard',
    data() {
        return {}
    },
}
</script>
<style lang="css" scoped>

</style>