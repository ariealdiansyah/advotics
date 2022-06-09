<template>
  <q-page class="q-px-lg bg-white">
    <div class="q-pa-lg">
      <div class="row text-title-menu items-center">
        <div class="col-6">
          <span class="q-mx-md text-weight-bold">Dashboard </span>
        </div>
        <div class="col-6 text-right">
          <q-btn-dropdown
            v-model="menu"
            class="text-black"
            color="white"
            icon="calendar_month"
            :label="getLabel"
          >
            <div class="row no-wrap q-pa-md">
              <div class="column">
                <q-btn
                  flat
                  color="black"
                  label="Yesterday"
                  align="left"
                  @click="getYesterday()"
                />
                <q-btn
                  flat
                  color="black"
                  label="Last 7 Days"
                  align="left"
                  @click="getLastWeeks()"
                />
                <q-btn
                  flat
                  color="black"
                  label="Last 30 Days"
                  align="left"
                  @click="getLastMonth()"
                />
                <q-btn
                  flat
                  color="black"
                  label="This Month"
                  align="left"
                  @click="getThisMonth()"
                />
                <q-btn unelevated color="positive" label="Apply" @click="apply()" />
              </div>

              <q-separator vertical inset class="q-mx-lg" />

              <div class="column items-center">
                <q-date v-model="date" :range="isRange" minimal :options="optionsFn" />
              </div>
            </div>
          </q-btn-dropdown>
        </div>
      </div>
      <div class="row items-center bg-positive q-pa-sm q-mt-xl text-white">
        <div class="col-6">
          <span class="q-mx-md text-title-menu text-weight-bold text-white">
            Market Insight
          </span>
        </div>
        <div class="col-6 text-right">
          <q-icon name="tips_and_updates" />
          <span class="q-mx-sm">Click For Help</span>
        </div>
      </div>
      <div class="row q-pt-lg">
        <div class="col-lg-3 col-md-6 col-sm-6 col-xs-12">
          <q-card class="my-card" flat bordered>
            <q-card-section>
              <div class="row d-flex wrap">
                <div class="col-10">
                  <span class="text-grey text-h5">Sales Turnover</span>
                </div>
                <div class="col text-right">
                  <q-icon name="more_vert" />
                </div>
              </div>
              <div class="row d-flex wrap q-mt-md items-center">
                <div class="col-10">
                  <div class="row">
                    <span class="text-black text-title-menu text-weight-bold">
                      Rp 3,600,000
                    </span>
                  </div>
                  <div class="row">
                    <q-icon name="south" color="negative" />
                    <span class="text-negative text-h-6 q-mr-xs"> 13.8 % </span>
                    <span class="text-grey text-h-6">last period in products sold </span>
                  </div>
                </div>
                <div class="col">
                  <img src="~assets/Sales.svg" style="width: 50px; height: 50px" />
                </div>
              </div>
            </q-card-section>
          </q-card>
        </div>
      </div>
      <div class="row q-pt-lg">
        <div class="col-lg-6 col-md-6 col-sm-12">
          <Chart />
        </div>
        <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12 q-pr-sm q-pt-lg">
          <q-card class="my-card" flat bordered>
            <q-card-section>
              <div class="row d-flex wrap">
                <div class="col-10">
                  <span class="text-grey text-h5">Best Selling SKU</span>
                </div>
                <div class="col text-right">
                  <q-icon name="more_vert" />
                </div>
              </div>
              <div
                class="row d-flex wrap q-mt-md items-center q-mb-sm"
                v-for="i in 5"
                :key="i"
              >
                <div class="col-3 q-mr-sm">
                  <img src="~assets/Product.png" style="width: 80px; height: 90px" />
                </div>
                <div class="col q-pl-sm">
                  <div class="row">
                    <div class="col-12">
                      <span class="text-black text-desc-menu text-weight-bold">
                        Nama Product
                      </span>
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-4">
                      <span class="text-grey">Rp 3000</span>
                    </div>
                    <div class="col-8 text-right">
                      <span class="text-grey">Jumlah terjual 9</span>
                    </div>
                  </div>
                </div>
              </div>
            </q-card-section>
          </q-card>
        </div>
        <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12 q-pr-sm q-pt-lg">
          <q-card class="my-card" flat bordered>
            <q-card-section>
              <div class="row d-flex wrap">
                <div class="col-10">
                  <span class="text-grey text-h5">Top Competitor SKU</span>
                </div>
                <div class="col text-right">
                  <q-icon name="more_vert" />
                </div>
              </div>
              <div
                class="row d-flex wrap q-mt-md items-center q-mb-sm"
                v-for="i in 5"
                :key="i"
              >
                <div class="col-3 q-mr-sm">
                  <img src="~assets/Product.png" style="width: 85px; height: 90px" />
                </div>
                <div class="col q-pl-sm">
                  <div class="row">
                    <div class="col-12">
                      <span class="text-black text-desc-menu text-weight-bold">
                        Nama Product
                      </span>
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-4">
                      <span class="text-grey">Rp 3000</span>
                    </div>
                    <div class="col-8 text-right">
                      <span class="text-grey">Jumlah terjual 9</span>
                    </div>
                  </div>
                </div>
              </div>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import Chart from 'src/pages/Index.vue';

import { mapGetters } from 'vuex';
export default {
  name: 'IndexPage',
  components: {
    Chart,
  },
  data() {
    return {
      isRange: true,
      periodFrom: '',
      periodTo: '',
      menu: false,
      date: '',
    };
  },
  created() {
    this.$store.commit(
      'app/setDate',
      this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() - 1,
          0
        )
      )
    );
  },
  computed: {
    ...mapGetters('app', {
      datee: 'getDate',
    }),
    model: {
      set(val) {
        this.$store.commit('app/setDate', this.formatDate(new Date(val)));
      },
      get() {
        return this.datee;
      },
    },
    getLabel() {
      if (this.periodFrom === '' || this.periodTo === '') {
        this.applyDates(this.model);
      }
      return `Period ${this.periodFrom} - ${this.periodTo}`;
    },
    max() {
      return this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() - 1,
          0
        )
      );
    },
  },
  methods: {
    optionsFn(date) {
      return (
        date <=
        this.formatDate(
          new Date(
            new Date().getFullYear(),
            new Date().getMonth(),
            new Date().getDate() - 1,
            0
          )
        )
      );
    },
    formatDate(date) {
      let tgl;
      let bln;
      var [month, dates, year] = date.toLocaleDateString().split('/');
      if (dates < 10) {
        tgl = `0${dates}`;
      } else {
        tgl = dates;
      }
      if (month < 10) {
        bln = `0${month}`;
      } else {
        tgl = month;
      }
      return `${year}/${bln}/${tgl}`;
    },
    getYesterday() {
      this.isRange = false;
      const a = this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() - 1,
          0
        )
      );
      this.date = a;
    },
    getLastWeeks() {
      this.isRange = true;
      const from = this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() - 7,
          0
        )
      );
      const to = this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() - 1,
          0
        )
      );
      this.date = { from: from, to: to };
    },
    getLastMonth() {
      this.isRange = true;
      const from = this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth() - 1,
          new Date().getDate(),
          0
        )
      );
      const to = this.formatDate(
        new Date(
          new Date().getFullYear(),
          new Date().getMonth(),
          new Date().getDate() - 1,
          0
        )
      );
      this.date = { from: from, to: to };
    },
    getThisMonth() {
      this.isRange = true;
      const from = this.formatDate(
        new Date(new Date().getFullYear(), new Date().getMonth(), 1)
      );
      const to = this.formatDate(
        new Date(new Date().getFullYear(), new Date().getMonth() + 1, 0)
      );
      this.date = { from: from, to: to };
    },
    applyDates(val) {
      Date.prototype.getMonthName = function () {
        const monthNames = [
          'Januari',
          'Februari',
          'Maret',
          'April',
          'Mei',
          'Juni',
          'Juli',
          'Agustus',
          'September',
          'Oktober',
          'November',
          'Desember',
        ];
        return monthNames[this.getMonth()];
      };

      Date.prototype.getDayName = function () {
        const dayNames = ['Minggu', 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu'];
        return dayNames[this.getDay()];
      };

      const fromdata = typeof val === 'object' ? val.from : val;
      const todata = typeof val === 'object' ? val.to : val;

      const fromdate = new Date(fromdata);
      const todate = new Date(todata);

      this.periodFrom = `${fromdate.getDayName()}, ${fromdate.getDate()} ${fromdate.getMonthName()} ${fromdate.getFullYear()}`;
      this.periodTo = `${todate.getDayName()}, ${todate.getDate()} ${todate.getMonthName()} ${todate.getFullYear()}`;
    },
    apply() {
      this.menu = false;
      this.applyDates(this.date);
    },
  },
};
</script>
