<script setup>
    import AboutImg from '../../assets/images/home/about-img.png'  
    import ButtonText from '../ui/ButtonText.vue';
</script>

<template>
    <div class="about-section py-20">
        <div class="container">
            <div class="grid grid-cols-6 md:grid-cols-12 gap-6">
                <div class="col-span-6">
                    <div>
                        <img src="../../assets/images/home/about-img.png" alt="">
                    </div>
                </div>
                <div class="col-span-6">
                    <div class="space-y-4 md:space-y-20">
                        <h1 class="font-bold mt-0 md:mt-24">About Our Alumni Association</h1>
                        <p class="text-justify">The Dhaka University Shahidullah Hall Alumni Association is a body that connects former students of Dr. Muhammad Shahidullah Hall, one of the residential halls of the University of Dhaka. These associations play a crucial role in fostering relationships among alumni, providing networking opportunities, and supporting the university and its current students.</p>
                        <div class="flex justify-between items-end">
                            <h1 class="text-outline text-outline-thin font-poppins">EST. 1960</h1>
                            <ButtonText label="Read More" :icon="ArrowRight" iconSize="16" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>