<template>
    <div>
        <header class="app-header">
            <div class="container">
                <a class="logo" rel="home" href="/">
                    <img alt="Vue logo" src="../assets/logo.png">
                </a>
            </div>
        </header>
    </div>
</template>

<script>
    export default {
        name: "NavBar"
    }
</script>

<style lang="scss" scoped>
    .app-header{
        flex-shrink: 0;
        position: relative;
        color: #fff;
        background-color: #ffd384;
        box-shadow: 0 0.25rem 0.25rem rgba(0,0,0,.25);

        & .container{
            position: relative;
            padding: 0 1rem;
            margin: 0 auto;
            max-width: 64.5rem;

            display: flex;
            justify-content: space-between;
        }

        & .logo {
            margin: 8px 0;

            & img{
                height: 36px;
                width: 101px;
            }
        }
    }
</style>