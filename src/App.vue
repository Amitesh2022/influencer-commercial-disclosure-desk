<script setup lang="ts">
import { onMounted } from 'vue'
import { storeToRefs } from 'pinia'
import { RouterLink, RouterView } from 'vue-router'
import { useDeliveryStore } from './store'
const store = useDeliveryStore()
const { approvedShare, offers, urgent } = storeToRefs(store)
onMounted(store.load)
</script>

<template><div class="shell"><aside><div class="brand">CreatorFairEU<span>DISCLOSURES</span></div><nav><RouterLink to="/">Campaign reviews</RouterLink><RouterLink to="/insights">Disclosure guidance</RouterLink></nav><div class="health"><i /> Java disclosure service connected</div></aside><main><header><div><span class="eyebrow">Make paid creator content clear, comparable and accountable across digital channels</span><h1>Influencer Commercial Disclosure Desk</h1></div><button @click="store.addOffer">Add campaign review</button></header><section class="summary"><article><small>Reviews approved</small><strong>{{ approvedShare }}%</strong><div class="bar"><span :style="{ width: `${approvedShare}%` }" /></div></article><article><small>Campaigns tracked</small><strong>{{ offers.length }}</strong><p>Shared enforcement view</p></article><article><small>High-risk disclosures</small><strong>{{ urgent }}</strong><p>Needs attention</p></article></section><RouterView /></main></div></template>
