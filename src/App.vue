<template>
    <div id="app">
        <nav-bar/>
        <main class="main-search">
            <div class="container banner">
                <span class="overlay-text">Vind nu uw ideale woning op Huisvesting Voor Senioren</span>
                <img class="overlay-skyline" src="./assets/silhoutte.png"/>
                <img class="overlay-right" src="./assets/house.png"/>
            </div>
            <div class="container search">
                <label>
                    <input class="form-control"/>
                    {{locaties}}
                </label>
            </div>
        </main>
    </div>
</template>

<script>
  import NavBar from "@/components/NavBar";
  import axios from 'axios';

  export default {
        name: 'App',
        components: {
            NavBar,
        },
        data: function (){
            return {
                locaties: []
            }
        },
        mounted() {
            axios.get('http://127.0.0.1:8000/rest/locatie/zoek', {
                params: {
                    test: 3
                }
            }).then(function (response) {
                this.locaties = response.data;
            })
        }
  }
</script>

<style lang="scss">
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    body {
        margin: 0;
    }

    .main-search {
        padding-top: 1.5rem;
        background: linear-gradient(180deg, #ffe3b8 50%, #ffffff 90%);

        & .container {
            margin: 0 auto;
            max-width: 64.5rem;
            display: flex;
            justify-content: space-between;
        }

        & .banner {
            height: 200px;
            position: relative;
            flex-direction: row;

            & .overlay-text{
                padding: 20px 50px;
                font-size: 35px;
                text-align: left;
                font-weight: lighter;
                font-family: Proxima Nova,sans-serif;
                z-index: 1;
            }

            & .overlay-skyline{
                filter: brightness(0) invert(1);
                position: absolute;
                width: 700px;
                bottom: 10px;
                right: 0px;
            }

            & .overlay-right{
                width: 200px;
                z-index: 1;
            }
        }

        & .search{
            background-color: #ffd384;
            border-radius: 4px;
            min-height: 250px;

            & label{
                width: 100%;
            }

            .form-control {
                display: block;
                width: 100%;
                height: calc(1.5em + 0.75rem + 2px);
                padding: .375rem .75rem;
                font-size: 1rem;
                font-weight: 400;
                line-height: 1.5;
                color: #495057;
                background-color: #fff;
                background-clip: padding-box;
                border: 1px solid #ced4da;
                border-radius: .25rem;
                transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
            }
        }
    }
</style>
