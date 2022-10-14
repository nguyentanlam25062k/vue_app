<template>
    <div class="candidates">
        <div class="candidates-layout">
            <div class="candidates-container">
                <template v-if="candidates.length > 0">
                    <div class="candidates-list">
                        <CheckedAll 
                            :isArrowDown="true"
                            :isCheckedAll="isCheckedAllId"
                        />
                        <template v-for="candidate in candidates">
                            <CandidateAttb 
                                v-if="candidate.is_house_ATBB"
                                :checkeds="checkedIds"
                                :candidate="candidate"
                                @cadidateChecked="cadidateChecked"
                            />
                            <CandidateNaiken 
                                v-else 
                                :checkeds="checkedIds"
                                :candidate="candidate"
                                @cadidateChecked="cadidateChecked"
                            />
                        </template>
                        <CheckedAll 
                            :isArrowUp="true"
                            :isCheckedAll="isCheckedAllId"
                        />
                    </div>
                </template>
                <template v-else>
                    <div>チェックボックス付き物件情報パーツ全5パターン＋まとめて内見予約ボタンのついた吹き出しパーツ</div>
                </template>
                <div class="btn-global" @click="showData">show data</div>
            </div>
        </div>
    </div>
</template>

<script>
    import CandidateAttb from './CandidateAttb.vue';
    import CandidateNaiken from './CandidateNaiken.vue';
    import CheckedAll from './CheckedAll.vue';

    const CANDIDATE_DEFAULT = {
        id: 1,
        house_no: "0000100032",
        block: "1",
        room: "1",
        lot: "1",
        rent_cost: "1200.00",
        price: "13.00",
        construction_year: "1913-01",
        construction_year_japan: null,
        is_japan_construction_year: 0,
        created_at: "2022-08-16T15:10:43.000000Z",
        updated_at: "2022-10-02T22:08:30.000000Z",
        deleted_at: null,
        area_ownership: null,
        area_ownership_type: "internal",
        area_total: null,
        land_area: null,
        land_area_type: "real",
        area_house: 1370,
        position: {
            "lat": null,
            "lng": null
        },
        access: null,
        entry_date: "2022-09-08",
        entry_type: "choose",
        month_type: null,
        status: "empty_house",
        house_delivery_type: "right_away",
        house_delivery_month: null,
        house_delivery_time: null,
        images: null,
        account_id: 1,
        person_in_charge: 2,
        account_id_registered: 1,
        house_struct: "DK",
        room_number: 17,
        flg_info: 0,
        company_info_id: null,
        user_id_registered: 1,
        user_id_updated: 1,
        owner_type: "agent",
        is_disable_by_type: 0,
        house_basic_id: 39,
        is_house_link_ATBB: 0,
        house_id_ATBB: null,
        naiken_house_link_id: "251",
        is_house_booking: 0,
        lat: null,
        lng: null,
        is_house_ATBB: false,
        is_public: true,
        company: {
            id: 1,
            name: "Company 1",
            phone: "0000000000100"
        },
        setting_info: {
            is_appointment: 1,
            is_take_pictures: 0
        },
        period_see_house: {
            start_date: "2022-08-03",
            end_date: "2022-08-18"
        },
        dates_not_see_house: false,
        is_key_info: true
    }

    export default {
        name: 'Candidates',
        components: {
            CandidateAttb,
            CandidateNaiken,
            CheckedAll
        },
        data() {
            return {
                checkedIds: [],
                isCheckedAllId: false,
                candidates: [
                    { ...CANDIDATE_DEFAULT },
                    { ...CANDIDATE_DEFAULT, deleted_at: "2022-08-03" },
                    { ...CANDIDATE_DEFAULT, setting_info: { is_appointment: 1, is_take_pictures: 0 } },
                    { ...CANDIDATE_DEFAULT, setting_info: { is_appointment: 0, is_take_pictures: 0 } },
                    { ...CANDIDATE_DEFAULT, setting_info: { is_appointment: 0, is_take_pictures: 1 } },
                    { ...CANDIDATE_DEFAULT, setting_info: { is_appointment: 0, is_take_pictures: 0 } },
                    { ...CANDIDATE_DEFAULT, is_public: true, is_house_ATBB: true },
                    { ...CANDIDATE_DEFAULT, is_public: false, is_house_ATBB: true },
                    { ...CANDIDATE_DEFAULT, is_key_info: true },
                ]
            }
        },
        created() {
            // this.getCandidates();
        },
        methods: {
            async getCandidates() {
                const { data: { data: candidates } } = await this.$axios.get('/houses/candidates');
                this.candidates = candidates;
            },
            cadidateChecked(id) {
                if(!this.checkedIds.includes(id)) {
                    this.checkedIds.push(id);
                    return;
                }
                this.checkedIds = this.checkedIds.filter(checkedId => checkedId != id);
            },
            showData() {
                console.log(this.checkedIds);
            }
        }
        
    }
</script>

<style lang="sass">
    @import './index.sass'
</style>
