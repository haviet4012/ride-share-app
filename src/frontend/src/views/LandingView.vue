<template>
    <div class="pt-16">
        <h1 class="text-3xl font-semibold mb-4">
            Select an option
        </h1>
        <div class="overflow-hidden shadow sm:rounded-sm max-w-sm mx-auto text-left">
            <div class="bg-white px-4 py-5 sm:p-6">
                <div class="flex justify-between">
                    <button 
                    @click="handleStartDriving"
                    class="rounded-md border border-transparent bg-black text-white px-4 py-2 cursor-pointer font-medium hover:opacity-80">
                        Start Driving
                    </button>
                    <button
                    @click="handleFindARide"
                    class="rounded-md border border-transparent bg-black text-white px-4 py-2 cursor-pointer font-medium hover:opacity-80">
                        Find a ride
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router';
import http from '@/helpers/http';



const router = useRouter()
const handleStartDriving = () => {
    http().get('/api/driver')
        .then((response)=> {
            if(response.data.driver){
                router.push({
                    name: 'standby'
                })
            }else{
                router.push({
                    name: 'driver'
                })
            }
        })
    router.push({
        name: 'standby'
    })
}

const handleFindARide = () => {
    router.push({
        name: 'location'
    })
}

</script>

<style>

</style>