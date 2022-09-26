<template>
    <div class="dashboard v-2">
        <DashboardNotify/>
        <DashboardFilter/>
        <DashboardTab/>
        <DashboardCalendar
            :today="today"
            :starDate="starDate"
            :endDate="endDate"
            :events="events"
            :onShowEvent="showEvent"
            :onViewDay="viewDay"
        />
        <ModalCalendar
            :isActiveModal="isActiveModal"
            :event="event"
            :onCloseModal="closeModal"
        />
    </div>
</template>

<script>
    import DashboardCalendar from './DashboardCalendar.vue';
    import DashboardFilter from './DashboardFilter.vue';
    import DashboardNotify from './DashboardNotify.vue';
    import DashboardTab from './DashboardTab.vue';
    import ModalCalendar from './ModalCalendar.vue';

    const convertDatetoTime = (date) => {
        return new Date(date).toISOString().substring(0, 10);
    }

    const getTime = () => {
        let h = Math.ceil(Math.random() * 24);
        let m = Math.ceil(Math.random() * 60);
        h = h < 10 ? '0' + h : h;
        m = m < 10 ? '0' + m : m;
        return h + ':' + m;
    }

    const randomNumber = (max) => {
        return Math.floor(Math.random() * max);
    }

    export default {
        name: 'Dashboard',
        components: {
            DashboardCalendar,
            DashboardFilter,
            DashboardNotify,
            DashboardTab,
            ModalCalendar
        },
        data() {
            return {
                today: "2022-10-10",
                isActiveModal: false,
                event: null,
                events: [],
                colors: ["#1867c0", "#fb8c00", "#000000"],
                texts: ["lorem 1", "lorem 2", "lorem 3"],
                types: ['red', 'green'],
                boleans: [false, true],
                category: ["Development", "Meetings", "Slacking"],
                dateDisables: [
                    "2022-10-10",
                    "2022-10-11",
                    "2022-10-12",
                    "2022-10-13",
                ]
            }
        },
        created() {
            this.getEvents();
        },
        mounted() {
            this.disableDate();
        },
        computed: {
            starDate() {
                return "2022-10-08";
            },
            endDate() {
                return "2022-10-18";
            },
        },
        methods: {
            getEvents() {
                const { starDate, endDate, colors, texts, types, boleans } = this;
                const events = [];
                for (let i = new Date(starDate); i <= new Date(endDate); i.setDate(i.getDate() + 1)) {
                    const numb = randomNumber(4);
                    for (let j = 0; j < numb; j++) {
                        events.push({
                            start: convertDatetoTime(i),
                            startTime: getTime(),
                            endTime: getTime(),
                            title: texts[randomNumber(3)],
                            title2: texts[randomNumber(3)],
                            type: types[randomNumber(2)],
                            isWarning: boleans[randomNumber(2)],
                            color: colors[randomNumber(3)],
                        });
                    }
                }
                // console.log(JSON.parse(JSON.stringify(events)));
                this.events = events;
            },
            showEvent(event) {
                // console.log(event);
                this.openModal();
                this.event = event;
            },
            viewDay(event) {
                // console.log('viewDay', event);
            },
            openModal() {
                this.isActiveModal = true;
            },
            closeModal() {
                this.isActiveModal = false;
            },
            disableDate() {
                const calendarElm = document.querySelector('.v-calendar');
                const dateDisables = this.dateDisables.map(date => date.split("-").pop());
                // console.log(dateDisables);
                const dateElms  = calendarElm.querySelectorAll('.v-btn__content');
                const dateDisableElms = [...dateElms].filter(date => dateDisables.includes(date.textContent));
                const parentDateDisableElms = dateDisableElms.map(e => e.parentElement.parentElement.parentElement)
                // console.log(parentDateDisableElms);

                parentDateDisableElms.forEach(elm => elm.classList.add('disable'));
            }
        },
    }
</script>

<style lang="sass">
    @import './sass/Dashboard.sass'
</style>
