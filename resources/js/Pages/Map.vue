<template>
  <app-layout>
    <template #header>Carte</template>
    <div class="mb-4">
        <form @submit.prevent="submit" >
            <input class="h-8 px-4 text-white duration-300 rounded-lg focus:shadow-outline bg-red-300 hover:bg-red-400 transition" type="submit" value="Search"/>
            &emsp;
            <input type="number" aria-label="postalCode" id="postalCode" v-model="form.Code_Postal" placeholder="Code postal : 75001"/>
            <div v-if="$page.errors.Code_Postal"><span class="text-red-500" >&emsp;&emsp;&emsp;&emsp;&emsp;{{ $page.errors.Code_Postal[0] }}</span></div>
        </form>

    </div>
    <br/><br/>
    <map-component></map-component>
  </app-layout>
</template>

<script>
import AppLayout from "../Layouts/AppLayout.vue";
import MapComponent from "./Components/MapComponent";
export default {
    components: {
        AppLayout,
        MapComponent,
    },
    data(){
        return{
            form : {

                Code_Postal: null,
            }

        }
    },
    methods: {
        submit() {

            this.$inertia.visit('/map/event',{
                method: 'get',
                data: this.form,
            })

        }
    },
}
</script>
