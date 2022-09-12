<template>
    <div>
        <div class="dashboard-key v-2">
            <div class="db-key-text">鍵の受け渡し予定</div>
            <ul class="db-key-list">
                <li class="db-key-item">
                    <div class="db-key-item-box-blue">鍵取り</div>
                    <div class="db-key-item-text">あり</div>
                    <div class="db-key-item-icon">
                        <span class="icon-check">+</span>
                    </div>
                </li>
                <li class="db-key-item">
                    <div class="db-key-item-box-blue">鍵取り</div>
                    <div class="db-key-item-text">あり</div>
                    <div class="db-key-item-icon">
                        <span class="icon-check">+</span>
                    </div>
                </li>
                <li class="db-key-item disable">
                    <div class="db-key-item-box-blue">鍵取り</div>
                    <div class="db-key-item-text">あり</div>
                    <div class="db-key-item-icon">
                        <span class="icon-check">+</span>
                    </div>
                </li>
                <li class="db-key-item disable">
                    <div class="db-key-item-box-blue">鍵取り</div>
                    <div class="db-key-item-text">あり</div>
                    <div class="db-key-item-icon">
                        <span class="icon-check">+</span>
                    </div>
                </li>
            </ul>
        </div>
        <div class="dashboard-card v-2">
            <div class="db-card-header">
                <div class="db-card-header-row">
                    <div class="db-card-header-col">
                        <div class="db-box-outline-blue">物件種別</div>
                        <div class="db-address">
                            <div class="db-address-icon">
                                <span class="icon-pin"></span>
                            </div>
                            <div class="db-address-text">所在地</div>
                        </div>
                        <div class="db-building-name">建物名</div>
                        <div class="db-key">
                            <div class="db-key-icon">
                                <span class="icon-key"></span>
                            </div>
                            <div class="db-key-text">
                                <p>鍵取り</p>
                                <p>立ち会い</p>
                                <p>現地対応</p>
                                <p>その他</p>
                            </div>
                        </div>
                        <div class="db-row-box">
                            <div class="db-col-box">
                                <div class="db-box-blue">賃料/価格(最新)</div>
                                <div class="db-price">9.0万円</div>
                            </div>
                            <div class="db-col-box">
                                <div class="db-box-outline-gray">案内予約物件台帳番号</div>
                                <div class="db-number">0000000000</div>
                            </div>
                        </div>
                    </div>
                    <div class="db-card-header-col">
                        <div class="db-status">
                            <div class="db-status-text">事前準備タスクの状況</div>
                            <div class="db-status-list">
                                <div class="db-status-item">
                                    <div class="db-status-item-header">
                                        <div class="db-status-item-text">物件情報</div>
                                        <div class="db-status-item-icon-new">NEW</div>
                                    </div>
                                    <div class="db-status-item-body">
                                        <span class="icon-check"></span>
                                    </div>
                                </div>
                                <div class="db-status-item">
                                    <div class="db-status-item-header">
                                        <div class="db-status-item-text">物件情報</div>
                                        <div class="db-status-item-icon-new">NEW</div>
                                    </div>
                                    <div class="db-status-item-body">
                                        <span class="icon-check"></span>
                                    </div>
                                </div>
                                <div class="db-status-item">
                                    <div class="db-status-item-header">
                                        <div class="db-status-item-text">物件情報</div>
                                        <div class="db-status-item-icon-new">NEW</div>
                                    </div>
                                    <div class="db-status-item-body">
                                        <span class="icon-check"></span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="db-card-header-row">
                    <div class="db-history">
                        <p>物件変更履歴</p>
                    </div>
                </div>
                <div class="db-card-header-row">
                    <div class="db-link">
                        <p>物件情報（最新）を見る</p>
                    </div>
                </div>
            </div>
            <div class="db-card-body">
                <div class="db-card-child">
                    <div class="db-card-child-header">
                        <div class="db-heading">
                            <div class="db-heading-icon">
                                <span class="icon-date-pick"></span>
                            </div>
                            <div class="db-heading-outline-blue">内見理由</div>
                            <div class="db-heading-text">
                                <p>内見日</p>
                                <p>内見時間from</p>
                                <p>-</p>
                                <p>内見時間to</p>
                            </div>
                        </div>
                        <div class="db-notify">
                            <div class="db-notify-icon">
                                <span class="icon-notice"></span>
                            </div>
                            <div class="db-notify-text">この物件に対して重複する内見予定が入っています。変更が必要な場合は詳細から変更を行ってください。</div>
                        </div>
                        <div class="db-notify">
                            <div class="db-notify-icon">
                                <span class="icon-notice"></span>
                            </div>
                            <div class="db-notify-text">詳細を確認し、予約対応担当者を割り当ててください。</div>
                        </div>
                    </div>
                    <div class="db-card-child-body">
                        <div class="db-people">
                            <div class="db-people-item">
                                <div class="db-people-item-box-blue">予約対応担当者</div>
                                <div class="db-people-item-text">予約受付会社名</div>
                                <div class="db-people-item-text">予約対応担当者</div>
                            </div>
                            <div class="db-people-item">
                                <div class="db-people-item-box-blue">案内担当者</div>
                                <div class="db-people-item-text">案内予約会社名</div>
                                <div class="db-people-item-text">案内担当者</div>
                            </div>
                        </div>
                        <div class="db-history">
                            <p>物件変更履歴</p>
                        </div>
                        <div class="db-link">
                            <div class="db-link-btn">
                                <div class="btn-link v-2 btn-primary">詳細を見る</div>
                                <span class="icon-external"></span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="dashboard-calendar v-2">
            <div class="db-calendar-heading">カレンダー 2021年1月10日〜2021年1月30日</div>
            <v-calendar
            :now="today"
            :value="today"
            :start="starDate"
            :end="endDate"
            :events="events"
            :weekday-format="dayFormat"
            color="primary"
            type="custom-weekly"
            >
            </v-calendar>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TabOne',
    props: {
        heading: Number,
        isActive: Boolean,
        onHeadingTabSPClick: Function
    },
    data() {
        return {
            today: '2022-10-10',
            tracked: {
            '2022-10-09': [23, 45, 10],
            '2022-10-08': [10],
            '2022-10-07': [0, 78, 5],
            '2022-10-06': [0, 0, 50],
            '2022-10-05': [0, 10, 23],
            '2022-10-04': [2, 90],
            '2022-10-03': [10, 32],
            '2022-10-02': [80, 10, 10],
            '2022-10-01': [20, 25, 10]
            },
            events: [],
            colors: ['#1867c0', '#fb8c00', '#000000'],
            texts: ['lorem 1', 'lorem 2', 'lorem 3'],
            category: ['Development', 'Meetings', 'Slacking']
        }
    },
    created() {
        this.getEvents();
    },
    computed: {
        starDate() {
            return '2022-10-08';
        },
        endDate() {
            return '2022-10-18';
        },
    },
    methods: {
        dayFormat({ weekday }) {
            const dayMap = {
                0: '日曜',
                1: '月曜',
                2: '火曜',
                3: '水曜',
                4: '木曜',
                5: '金曜',
                6: '土曜',
            }
            return dayMap[weekday];
        },
        getEvents() {
            const {starDate, endDate, colors, texts} = this;
            const events = [];

            function getRandomElement(count) {
                const elements = [];
                for(let i = 0; i < count; i++) {
                    elements.push(texts[Math.floor(Math.random() * 3)]);
                }
                return elements;
            }

            for (let i = new Date(starDate); i <= new Date(endDate); i.setDate(i.getDate() + 1)) {
                events.push({
                    start: new Date(starDate).toISOString().substring(0,10),
                    startTime: new Date(starDate).toISOString().substring(0,10),
                    color: colors[Math.floor(Math.random() * 3)],
                    // name: texts[Math.floor(Math.random() * 3)],
                    name: getRandomElement(Math.floor(Math.random() * 3)),
                })
            }
            console.log(JSON.parse(JSON.stringify(events)));
            this.events = events;
        }
    }
}
</script>

<style lang="css" scoped>
</style>
