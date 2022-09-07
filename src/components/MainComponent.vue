<template>
  <main>
    <LoadingLayover v-if="!loaded" />
    <div class="container-lg">
        <div class="row">
            <div class="col-2" v-for="(song,i) in songs" :key="i">

                <CardComponent
                    :poster="song.poster"
                    :title="song.title"
                    :author="song.author"
                    :year="song.year"
                />

            </div>
        </div>

    </div>
  </main>
</template>

<script>
import LoadingLayover from './LoadingLayover.vue';
import axios from 'axios';
import CardComponent from './CardComponent.vue';

export default {
    components: {
    LoadingLayover,
    CardComponent
},
    data() {
        return {
            loaded: false,
            songs: []
        }
    },
    created() {
        // recupero i dati dalla api
        axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then(res => {
                console.log("risposta della api con i data: ", res.data.response);
                // *
                this.songs = res.data.response;
            })
            .catch((err) => {
                console.log("Errore: ", err);
            })
            .finally(() => {
                // do un piccolo ritardo per far vedere il caricamento in ogni caso
                setTimeout(() => {
                    this.loaded = true
                },500)
            });
    },
}

</script>

<style lang="scss" scoped>

    @import '../style/variables.scss';

    main {
        flex-grow: 1;
        background-color: $--dark;
    }

</style>