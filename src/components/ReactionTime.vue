<template>
    <div>
        <div className="bg-[#000]">
            <div className="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
                <h1 className="mb-11 text-4xl md:text-4xl font-extrabold text-slate-50 flex flex-col items-center">Stream
                    your favourite music here</h1>
                <h2 className="mb-3 text-3xl md:text-3xl font-extrabold text-slate-50 flex flex-col items-center">Play</h2>
                <h2 className="mb-12 text-2xl md:text-2xl font-extrabold text-blue-700 flex flex-col items-center">Playlist
                </h2>

                <div className="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
                    <div className="group" v-for="music in playlist" v-bind:key="music.id">
                        <div className=" rounded overflow-hidden shadow-lg">
                            <div className="relative h-64">
                                <img className="absolute w-full h-full object-cover" :src="music.cover" alt="" />
                                <div
                                    className="absolute inset-0 flex items-center justify-center transition-all hover:scale-105">
                                    <svg xmlns:dc="http://purl.org/dc/elements/1.1/"
                                        xmlns:cc="http://creativecommons.org/ns#"
                                        xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
                                        xmlns:svg="http://www.w3.org/2000/svg" xmlns="http://www.w3.org/2000/svg"
                                        id="play-icon" version="1.1" height="50" width="50" viewBox="0 0 1200 1200">
                                        <path
                                            d="M 600,1200 C 268.65,1200 0,931.35 0,600 0,268.65 268.65,0 600,0 c 331.35,0 600,268.65 600,600 0,331.35 -268.65,600 -600,600 z M 450,300.45 450,899.55 900,600 450,300.45 z"
                                            id="path16995" />
                                    </svg>
                                </div>

                            </div>
                        </div>
                        <div class="flex gap-3">
                            <h3 className="mt-4 text-md text-slate-50">{{ music.title }}</h3>
                            <!-- <h3 className="mt-4 text-md text-slate-50">{{ music.files.artist }}</h3> -->
                        </div>
                        <h3 className="mt-4 text-md text-slate-50">{{ music.artist }}</h3>
                        <!-- <audio :src="music.audio" controls loop></audio> -->
                    </div>
                    <p v-if="error" class="text-red-600">{{ errorMessage }}</p>
                </div>

            </div>

        </div>

        <div className="bg-[#000]">
            <div className="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
                <h2 className="mb-3 text-3xl md:text-3xl font-extrabold text-slate-50 flex flex-col items-center">Play</h2>
                <h2 className="mb-12 text-2xl md:text-2xl font-extrabold text-blue-700 flex flex-col items-center">New Music
                </h2>

                <div className="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
                    <div className="group" v-for="music in newMusic" v-bind:key="music.id">
                        <div className=" rounded overflow-hidden shadow-lg">
                            <div className="relative h-64">
                                <img className="absolute w-full h-full object-cover" :src="music.cover" alt="" />
                                <div
                                    className="absolute inset-0 flex items-center justify-center transition-all hover:scale-105">
                                    <svg xmlns:dc="http://purl.org/dc/elements/1.1/"
                                        xmlns:cc="http://creativecommons.org/ns#"
                                        xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
                                        xmlns:svg="http://www.w3.org/2000/svg" xmlns="http://www.w3.org/2000/svg"
                                        id="play-icon" version="1.1" height="50" width="50" viewBox="0 0 1200 1200">
                                        <path
                                            d="M 600,1200 C 268.65,1200 0,931.35 0,600 0,268.65 268.65,0 600,0 c 331.35,0 600,268.65 600,600 0,331.35 -268.65,600 -600,600 z M 450,300.45 450,899.55 900,600 450,300.45 z"
                                            id="path16995" />
                                    </svg>
                                </div>

                            </div>
                        </div>
                        <div class="flex gap-3">
                            <h3 className="mt-4 text-md text-slate-50">{{ music.title }}</h3>
                            <h3 className="mt-4 text-md text-slate-50">{{ music.duration }}</h3>
                        </div>
                        <h3 className="mt-4 text-md text-slate-50">{{ music.artist }}</h3>
                        <audio :src="music.audio" controls loop></audio>

                    </div>
                </div>

                <p v-if="error" class="text-red-600">{{ errorMessage }}</p>

            </div>

        </div>

        <div className="bg-[#000]">
            <div className="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8">
                <h2 className="mb-3 text-3xl md:text-3xl font-extrabold text-slate-50 flex flex-col items-center">Play</h2>
                <h2 className="mb-12 text-2xl md:text-2xl font-extrabold text-blue-700 flex flex-col items-center">Popular
                    Music
                </h2>

                <div className="grid grid-cols-1 gap-y-10 gap-x-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8">
                    <div className="group" v-for="music in popularMusic" :key="music.id">
                        <div className=" rounded overflow-hidden shadow-lg">
                            <div className="relative h-64">
                                <img className="absolute w-full h-full object-cover" :src="music.cover" alt="" />
                                <div
                                    className="absolute inset-0 flex items-center justify-center transition-all hover:scale-105">
                                    <svg xmlns:dc="http://purl.org/dc/elements/1.1/"
                                        xmlns:cc="http://creativecommons.org/ns#"
                                        xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
                                        xmlns:svg="http://www.w3.org/2000/svg" xmlns="http://www.w3.org/2000/svg"
                                        id="play-icon" version="1.1" height="50" width="50" viewBox="0 0 1200 1200">
                                        <path
                                            d="M 600,1200 C 268.65,1200 0,931.35 0,600 0,268.65 268.65,0 600,0 c 331.35,0 600,268.65 600,600 0,331.35 -268.65,600 -600,600 z M 450,300.45 450,899.55 900,600 450,300.45 z"
                                            id="path16995" />
                                    </svg>
                                </div>

                            </div>
                        </div>
                        <div class="flex gap-3">
                            <h3 className="mt-4 text-md text-slate-50">{{ music.title }}</h3>
                            <h3 className="mt-4 text-md text-slate-50">{{ music.duration }}</h3>
                        </div>
                        <h3 className="mt-4 text-md text-slate-50">{{ music.artist }}</h3>
                        <audio :src="music.audio" controls loop></audio>
                    </div>
                </div>


                <p v-if="error" class="text-red-600">{{ errorMessage }}</p>

            </div>

        </div>

    </div>
</template>

<script>
import axios from "axios";

export default {
    data() {
        return {
            playlist: [],
            newMusic: [],
            popularMusic: [],
            error: false,
            errorMessage: '',
        }
    },
    mounted() {
        this.getPlaylist();
        this.getMusics();
        this.getPopularMusics();
    },
    methods: {
        getPlaylist() {
            let url = "https://musica-api.up.railway.app/playlist";
            axios.get(url).then((res) => {
                // Store only the first 4 items from the API data
                this.playlist = res.data.slice(0, 4);
            }).catch((error) => {
                // Handle error and display error message
                this.error = true;
                this.errorMessage = "Failed to fetch playlist data. Please try again later.";
                console.error(error);
            });
        },
        getMusics() {
            let url = "https://musica-api.up.railway.app/new";
            axios.get(url).then((res) => {
                this.newMusic = res.data.slice(0, 8);
            }).catch((error) => {
                // Handle error and display error message
                this.error = true;
                this.errorMessage = "Failed to fetch playlist data. Please try again later.";
                console.error(error);
            });
        },
        getPopularMusics() {
            let url = "https://musica-api.up.railway.app/popular";
            axios.get(url).then((res) => {
                this.popularMusic = res.data.slice(0, 8);
            }).catch((error) => {
                // Handle error and display error message
                this.error = true;
                this.errorMessage = "Failed to fetch playlist data. Please try again later.";
                console.error(error);
            });
        },
    }
}
</script>