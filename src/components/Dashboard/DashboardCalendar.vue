<template>
    <div class="dashboard-calendar v-2">
        <div class="db-calendar-heading">カレンダー 2021年1月10日〜2021年1月30日</div>
        <v-calendar
            :now="today"
            :value="today"
            :start="starDate"
            :end="endDate"
            :events="events"
            :event-height="null"
            :event-color="colorFormat"
            :weekday-format="dayFormat"
            @click:event="onShowEvent"
            @click:day="onViewDay"
            type="custom-weekly"
        >
            <template v-slot:event="{ event: { startTime, endTime, title, title2, isWarning, type } }">
                <div class="db-appointment"
                    :class="type"
                >
                    <div class="db-appointment-btn">
                        <div class="db-appointment-btn-span">受付</div>
                        <div class="db-appointment-btn-text">{{ title }}</div>
                    </div>
                    <div class="db-appointment-content"
                        :class="{ 'has-notify' : isWarning }"
                    >
                        <div class="db-appointment-content-icon">
                            <v-icon>info</v-icon>
                            <!-- <span class="icon-notice"></span> -->
                        </div>
                        <div class="db-appointment-content-link">
                            <div class="db-text">{{ startTime }}-{{ endTime }}</div>
                            <div class="db-text">{{ title }}</div>
                        </div>
                    </div>
                </div>
            </template>
        </v-calendar>
    </div>
</template>
<script>
    export default {
        name: 'DashboardCalendar',
        props: {
            today: String,
            starDate: String,
            endDate: String,
            events: Array,
            onShowEvent: Function,
            onViewDay: Function
        },
        data() {
            return {}
        },
        methods: {
            colorFormat(e) {
                return e.color;
            },
            dayFormat({ weekday }) {
                const dayMap = {
                    0: "日曜",
                    1: "月曜",
                    2: "火曜",
                    3: "水曜",
                    4: "木曜",
                    5: "金曜",
                    6: "土曜",
                };
                return dayMap[weekday];
            },
        }
    }
</script>
<style lang="css" scoped>
</style>