<template>
  <main>
    <LoadingLayover v-if="!loaded" />
    <div class="container-lg p-5">
        <div class="grid">

            <div class="grid-col" v-for="(song,i) in filteredSongs" :key="i">
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
    props: {
        filterDataGenre: {
            type: String,
            default: ''
        },
        filterDataAuthor: {
            type: String,
            default: ''
        }
    },
    data() {
        return {
            loaded: false,
            songs: []
        }
    },
    created() {
        axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then(res => {
                // console.log("risposta della api con i data: ", res.data.response);
                this.songs = res.data.response;
            })
            .catch((err) => {
                console.log("Errore: ", err);
            })
            .finally(() => {
                // do un piccolo ritardo per far vedere il caricamento in ogni caso
                setTimeout(() => {
                    this.loaded = true
                },1000)
            });
    },
    computed: {
        realSongs(){
            return this.songs.filter((el) => {
                if(el.author === 'Michael Jacjson') el.author = 'Michael Jackson';
                return true;
            })
        },
        filteredSongs() {
            return this.realSongs.filter((el) => {
                const songGenre = el.genre.toLowerCase();
                const filterGenre = this.filterDataGenre.toLowerCase();
                // console.log(songGenre, filterGenre);
                const songAuthor = el.author.toLowerCase();
                const filterAuthor = this.filterDataAuthor.toLowerCase();
                // console.log(songAuthor, filterAuthor);

                if((songAuthor === filterAuthor || filterAuthor === '') && (songGenre === filterGenre || filterGenre === '')) return true;
                return false;
            })
        }
    },
}

</script>

<style lang="scss" scoped>

    @import '../style/variables.scss';

    main {
        flex-grow: 1;
        background-color: $--dark;
        overflow: auto;

        .grid {
            display: grid;
            grid-template-columns: repeat(1,1fr);
            gap: 2rem;
            align-items: center;
        }
    }

    @media (min-width: $--sm) {
        main {
            .grid {
                grid-template-columns: repeat(2,1fr);
            }
        }
    }

    @media (min-width: $--md) {
        main {
            .grid {
                grid-template-columns: repeat(3,1fr);
            }
        }
    }

    @media (min-width: $--lg) {
        main {
            .grid {
                grid-template-columns: repeat(4,1fr);
            }
        }
    }

    @media (min-width: $--xl) {
        main {
            .grid {
                grid-template-columns: repeat(5,1fr);
            }
        }
    }

</style>