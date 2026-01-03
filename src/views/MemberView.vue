<script setup lang="ts">
import Breadcrumb from '../components/shared/Breadcrumb.vue';
import MemberCard from '../components/ui/MemberCard.vue';

</script>

<template>
    <Breadcrumb title="Member" pageName="All Members" />
    <div class="container">
        <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-6 py-20">
            <div v-for="n in 8" :key="n">
                <MemberCard />
            </div>
        </div>
    </div>
</template>