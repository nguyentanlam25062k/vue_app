<template>
    <div class="candidates-checked-all"
        :class="{ 'arrow-down': isArrowDown, 'arrow-up': isArrowUp }"
    >
        <div class="candidates-checked-all-checkbox">
            <label class="candidates-checkbox">
                <input type="checkbox" :checked="isAllChecked" @change="$emit('allCandidateChecked')">
                <span class="checkmark"></span>
            </label>
            <div class="text">すべて選択</div>
        </div>
        <div class="candidates-checked-all-right">
            <div class="text">チェックした物件をまとめて</div>
            <div class="c-btn" 
                :class="{ 'not-allow': isNotAllowGoToBookingViewHouse }"
                @click="$emit('goToBookingViewHouse')"
            >
                <div class="c-btn-text">内見を予約する</div>
                <div class="c-btn-icon">
                    <span class="icon-external"></span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CheckedAll',
        props: {
            isArrowDown: {
                type: Boolean,
                default: false
            },
            isArrowUp: {
                type: Boolean,
                default: false
            },
            isAllChecked: {
                type: Boolean,
                default: false,
            },
            isNotAllowGoToBookingViewHouse: {
                type: Boolean,
                default: true
            }
        },
    }
</script>
