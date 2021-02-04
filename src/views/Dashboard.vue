<template>
  <v-container>
    <h1 class="text-center m-3">Dashboard</h1>
    <v-row>
      <v-col cols="12" md="4" lg="4" v-for="sale in sales" :key="`${sale.title}`">
        <v-card class=" mb-4" >
        <SalesGraph  :sale="sale" />
        </v-card>
      </v-col>
    </v-row>

    <v-row>
      <v-col
        cols="6" md="6" lg="3"
        v-for="statistic in statistics"
        :key="`${statistic.title}`"
      >
        <StatisticCard
          :statistic="statistic"
        />
      </v-col>
    </v-row>
  <!-- Same Statistique  -->
        <v-row>
      <v-col
        cols="6" md="6" lg="3"
        v-for="statistic in statistics"
        :key="`${statistic.title}`"
      >
        <StatisticCard
          :statistic="statistic"
        />
      </v-col>
    </v-row>
  <!-- Same Statistique  -->
        <v-row>
      <v-col
        cols="6" md="6" lg="3"
        v-for="statistic in statistics"
        :key="`${statistic.title}`"
      >
        <StatisticCard
          :statistic="statistic"
        />
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" md="8">
        <EmployeesTable :employees="employees" @select-employee="setEmployee" />
      </v-col>
      <v-col cols="12" md="4">
        <EventTimeline :timeline="timeline" />
      </v-col>
    </v-row>
    
    <!-- Same Employees -->
    <v-row v-intersect="LoadMoreContent">
      <v-col cols="12" md="8">
        <EmployeesTable :employees="employees" @select-employee="setEmployee" />
      </v-col>
      <v-col cols="12" md="4">
        <EventTimeline :timeline="timeline" />
      </v-col>
    </v-row>

    <v-sheet
        v-if="ShowNewContent"
        id="moreContent"
        :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
        class="pa-3 mt-4"
        >
        <v-skeleton-loader
          class="mx-auto"
          max-width="100%"
          type="card"
        ></v-skeleton-loader>
    </v-sheet>

    <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp">
      You have selected {{ selectedEmployee.name }},
      {{ selectedEmployee.title }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </v-container>
</template>

<script>
import EmployeesTable from '../components/EmployeesTable'
import EventTimeline from '../components/EventTimeline'
import SalesGraph from '../components/SalesGraph'
import StatisticCard from '../components/StatisticCard'

import employeesData from '../data/employees.json'
import timelineData from '../data/timeline.json'
import salesData from '../data/sales.json'
import statisticsData from '../data/statistics.json'

export default {
  name: 'DashboardPage',
  components: {
    EmployeesTable,
    EventTimeline,
    SalesGraph,
    StatisticCard
  },
  data() {
    return {
      theme: {
        default: { isDark: false },
      },
      ShowNewContent:false,
      employees: employeesData,
      loadNewContent: false,
      sales: salesData,
      selectedEmployee: {
        name: '',
        title: ''
      },
      snackbar: false,
      statistics: statisticsData,
      timeline: timelineData
    }
  },
  methods: {
    setEmployee(event) {
      this.snackbar = true
      this.selectedEmployee.name = event.name
      this.selectedEmployee.title = event.title
    },
    LoadMoreContent(entries) {
      console.log(entries[0].isIntersecting);
      this.ShowNewContent = entries[0].isIntersecting;
    }
  }
}
</script>
