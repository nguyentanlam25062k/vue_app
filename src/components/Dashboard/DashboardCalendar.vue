<template>
    <div class="dashboard-calendar">
        <div class="heading">カレンダー 2021年1月10日〜2021年1月30日</div>
        <v-calendar
            :now="today"
            :value="today"
            :start="starDate"
            :end="endDate"
            :events="events"
            :event-height="null"
            :event-color="colorFormat"
            :weekday-format="weekdayFormat"
            @click:event="onShowEvent"
            @click:day="onViewDay"
            type="custom-weekly"
        >
            <template v-slot:day-label="{ day }">
                <div class="btn-date"
                    :class="{ 'has-notify': showDayLabel(day) }"
                >
                    <div class="btn-date-notify">
                        <v-icon>info</v-icon>
                        <!-- <span class="icon-notice"></span> -->
                    </div>
                    <div class="btn-date-numb">{{ day }}</div>
                </div>
            </template>
            <template v-slot:event="{ event: { startTime, endTime, title, title2, isWarning, type } }">
                <div class="appointment"
                    :class="type"
                >
                    <div class="appointment-btn">
                        <div class="appointment-btn-span">受付</div>
                        <div class="appointment-btn-text">{{ title }}</div>
                    </div>
                    <div class="appointment-content"
                        :class="{ 'has-notify' : isWarning }"
                    >
                        <div class="appointment-content-icon">
                            <v-icon>info</v-icon>
                            <!-- <span class="icon-notice"></span> -->
                        </div>
                        <div class="appointment-content-link">
                            <div class="text">
                                <span>{{ startTime }}</span>
                                <span>-</span>
                                <span>{{ endTime }}</span>
                            </div>
                            <div class="text">{{ title }}</div>
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
            return {
                dayLabels: [3, 4, 5, 6]
            }
        },
        methods: {
            colorFormat(e) {
                return e.color;
            },
            dayFormat({ day }) {
                return day;
            },
            weekdayFormat({ weekday }) {
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
            showDayLabel(day) {
                return this.dayLabels.includes(day);
            }
        }
    }
</script>
<style lang="css" scoped>
</style>