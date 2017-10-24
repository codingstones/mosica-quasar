<template>
  <div class="layout-padding row justify-center">
    <q-toolbar color="primary">
      <q-toolbar-title>
        MOSICA
      </q-toolbar-title>
      <q-btn flat @click="openInfo">Info</q-btn>
    </q-toolbar>

    <div style="width: 100%">
      <LoadSpinner :isLoading="isLoading"/>
      <div class="day" v-for="day in gigsByDay" v-if="!isLoading">
        <Day :day="day" :onClick="goTo"/>
      </div>
    </div>
  </div>
</template>

<script>
  import { mapState } from 'vuex'
//  import * as mosicaCore from 'mosica-core'
  import { MosicaRouter } from '../../services/MosicaRouter'
  import { fakeGigsByDay } from '../../__mocks__/gigs-sample'
//  const gigService = new mosicaCore.GigService(HttpClient(fetchJsonp), new mosicaCore.Matcher())

  export default {
    data () {
      return {
        gigsByDay: [],
        isLoading: false,
        mosicaRouter: null
      }
    },
    async created() {
      this.isLoading = true
      this.gigsByDay = fakeGigsByDay
      this.isLoading = false
      this.mosicaRouter = new MosicaRouter(this.$router)
    },
    methods: {
      goTo(gig) {
        this.mosicaRouter.navigateToGig(gig.id)
      },
      openInfo() {
        console.log('Opening info')
        this.$router.push('gig')
      }
    },
    computed: {
      ...mapState(['gigs'])
    }
  }
</script>

<style>
</style>
