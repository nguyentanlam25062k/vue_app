<template>
    <v-layout wrap>
        <v-flex xs12 class="mb-3">
            <v-sheet height="500">
                <v-calendar ref="calendar" v-model="start" :type="type" :start="start" :end="end" :weekday-format="dayFormat" color="primary">
                </v-calendar>
            </v-sheet>
        </v-flex>
        <v-flex sm4 xs12 class="text-sm-left text-xs-center">
            <v-btn @click="$refs.calendar.prev()">
                <v-icon dark left>
                    keyboard_arrow_left
                </v-icon>
                Prev
            </v-btn>
        </v-flex>
        <v-flex sm4 xs12 class="text-xs-center">
            <v-select v-model="type" :items="typeOptions" label="Type"></v-select>
        </v-flex>
        <v-flex sm4 xs12 class="text-sm-right text-xs-center">
            <v-btn @click="$refs.calendar.next()">
                Next
                <v-icon right dark>
                    keyboard_arrow_right
                </v-icon>
            </v-btn>
        </v-flex>
    </v-layout>
</template>
<script>
export default {
    data: () => ({
        type: 'custom-weekly',
        start: '2019-01-01',
        end: '2019-01-10',
        typeOptions: [
            { text: 'Day', value: 'day' },
            { text: '4 Day', value: '4day' },
            { text: 'Week', value: 'week' },
            { text: 'Month', value: 'month' },
            { text: 'Custom Daily', value: 'custom-daily' },
            { text: 'Custom Weekly', value: 'custom-weekly' }
        ]
    }),
    methods: {
        dayFormat(day) {
            var result = '';
            switch (day.weekday) {
                case 0:
                    result = '日曜';
                    break;
                case 1:
                    result = '月曜';
                    break;
                case 2:
                    result = '火曜';
                    break;
                case 3:
                    result = '水曜';
                    break;
                case 4:
                    result = '木曜';
                    break;
                case 5:
                    result = '金曜';
                    break;
                case 6:
                    result = '土曜';
                    break;
            }
            return result;

        }
    }
}
</script>