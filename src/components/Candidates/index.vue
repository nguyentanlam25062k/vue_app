<template>
    <div class="candidates">
        <div class="candidates-layout">
            <div class="candidates-container">
                <template v-if="candidates.length > 0">
                    <div class="candidates-list">
                        <CheckedAll 
                            :isArrowDown="true"
                            :isAllChecked="isAllChecked"
                            :isNotAllowGoToBookingViewHouse="isNotAllowGoToBookingViewHouse"
                            @allCandidateChecked="allCandidateChecked"
                            @goToBookingViewHouse="goToBookingViewHouse"
                        />
                        <template v-for="candidate in candidates">
                            <CandidateAttb 
                                v-if="candidate.is_house_ATBB"
                                :checkeds="checkeds"
                                :candidate="candidate"
                                @cadidateChecked="cadidateChecked"
                            />
                            <CandidateNaiken 
                                v-else 
                                :checkeds="checkeds"
                                :candidate="candidate"
                                @cadidateChecked="cadidateChecked"
                            />
                        </template>
                        <CheckedAll 
                            :isArrowUp="true"
                            :isAllChecked="isAllChecked"
                            :isNotAllowGoToBookingViewHouse="isNotAllowGoToBookingViewHouse"
                            @allCandidateChecked="allCandidateChecked"
                            @goToBookingViewHouse="goToBookingViewHouse"
                        />
                        <CandidateModal/>
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
    import CandidateModal from './CandidateModal.vue';

    const CANDIDATE_DEFAULT = {
        id: 1,
        house_no: "",
        block: "",
        room: "",
        lot: "",
        rent_cost: "",
        price: "",
        construction_year: "",
        construction_year_japan: null,
        is_japan_construction_year: 0,
        created_at: "",
        updated_at: "",
        deleted_at: null,
        area_ownership: null,
        area_ownership_type: "",
        area_total: null,
        land_area: null,
        land_area_type: "",
        area_house: 1370,
        position: {
            "lat": null,
            "lng": null
        },
        access: null,
        entry_date: "",
        entry_type: "",
        month_type: null,
        status: "",
        house_delivery_type: "",
        house_delivery_month: null,
        house_delivery_time: null,
        images: null,
        account_id: 1,
        person_in_charge: 2,
        account_id_registered: 1,
        house_struct: "",
        room_number: 17,
        flg_info: 0,
        company_info_id: null,
        user_id_registered: 1,
        user_id_updated: 1,
        owner_type: "",
        is_disable_by_type: 0,
        house_basic_id: 39,
        is_house_link_ATBB: 0,
        house_id_ATBB: null,
        naiken_house_link_id: "",
        is_house_booking: 0,
        lat: null,
        lng: null,
        is_house_ATBB: false,
        is_public: true,
        company: {
            id: 1,
            name: "",
            phone: ""
        },
        setting_info: {
            is_appointment: 1,
            is_take_pictures: 0
        },
        period_see_house: {
            start_date: "",
            end_date: ""
        },
        dates_not_see_house: false,
        is_key_info: true
    }

    export default {
        name: 'Candidates',
        components: {
            CandidateAttb,
            CandidateNaiken,
            CheckedAll,
            CandidateModal
        },
            data() {
            return {
                checkeds: [],
                isAllChecked: false,
                candidates: [
                    { ...CANDIDATE_DEFAULT },
                    { ...CANDIDATE_DEFAULT, id: 2, deleted_at: "2022-08-03" },
                    { ...CANDIDATE_DEFAULT, id: 3, setting_info: { is_appointment: 1, is_take_pictures: 0 } },
                    { ...CANDIDATE_DEFAULT, id: 4, setting_info: { is_appointment: 0, is_take_pictures: 0 } },
                    { ...CANDIDATE_DEFAULT, id: 5, setting_info: { is_appointment: 0, is_take_pictures: 1 } },
                    { ...CANDIDATE_DEFAULT, id: 6, setting_info: { is_appointment: 0, is_take_pictures: 0 } },
                    { ...CANDIDATE_DEFAULT, id: 7, is_public: true, is_house_ATBB: true },
                    { ...CANDIDATE_DEFAULT, id: 8, is_public: false, is_house_ATBB: true },
                    { ...CANDIDATE_DEFAULT, id: 9, is_key_info: false },
                ]
            }
        },
        created() {
            // this.getCandidates();
        },
        computed: {
            isNotAllowGoToBookingViewHouse() {
                return !this.checkeds.length;
            }
        },
        methods: {
            getCandidatesApi() {
                return this.$axios.get(`/houses/candidates`);
            },
            deleteCandidateApi(id) {
                return this.$axios.delete(`/houses/${id}/candidates`);
            },
            redirectToHouse(id) {
                const route = this.$router.resolve(`/admin/broker/house/booking/${id}`);
                window.open(route.href, '_blank');
            },
            redirectToManyHouse(ids) {
                const route = this.$router.resolve(`/admin/broker/houses/booking/${ids.join(',')}`);
                window.open(route.href, '_blank');
            },
            async getCandidates() {
                const { data: { data: candidates } } = await this.getCandidatesApi();
                this.candidates = candidates;
            },
            cadidateChecked(id) {
                if(!this.checkeds.includes(id)) {
                    this.checkeds.push(id);
                    return;
                }
                this.checkeds = this.checkeds.filter(checkedId => checkedId != id);
            },
            allCandidateChecked() {
                if (this.isAllChecked) {
                    this.isAllChecked = false;
                    this.checkeds = [];
                    return;
                };

                const candidateValid = (candidate) => {
                    // candidate valid attb
                    if (candidate.is_house_ATBB && candidate.is_public) return false;

                    // candidate valid naiken
                    if (candidate.deleted_at !== null || candidate.setting_info.is_appointment == 0) return false;
                    
                    return true;
                }

                const candidateId = (candidate) => candidate.id;

                this.isAllChecked = true;
                this.checkeds = this.candidates.filter(candidateValid).map(candidateId);
            },
            goToBookingViewHouse() {
                if (this.isNotAllowGoToBookingViewHouse) return;

                this.checkeds.length > 1 ? this.redirectToManyHouse(this.checkeds) : this.redirectToHouse(this.checkeds[0]);
            },
            showData() {
                console.log(this.checkeds);
            }
        }
        
    }
</script>

<style lang="sass">
    @import './index.sass'
</style>
