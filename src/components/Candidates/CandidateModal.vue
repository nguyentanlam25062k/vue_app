<template>
    <div class="candidates-modal active">
        <div class="modal-wrap">
            <div class="modal-header">
                <!-- <span class="icon-close"></span> -->
                <div class="modal-header-icon">x</div>
            </div>
            <div class="modal-body">
                <div class="modal-body-heading">登録内容を変更しました。</div>
                <div class="modal-body-desc">確認が必要な内見予定があります。ダッシュボードから内見予約を確認し、変更・キャンセルを行ってください。</div>
                <div class="modal-body-btn">ダッシュボードに戻る</div>
            </div>
        </div>
    </div>   
</template>

<script>
    export default {
        name: 'CandidateModal',
    }
</script>