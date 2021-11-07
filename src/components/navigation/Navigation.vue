<template>
    <nav class="navigation">

        <!--Open sideMenu-->
        <button class="sideMenuButton"
                @click="toggleSideMenu"
        >
            {{sideMenuOpen ? '🠔' : '🠖'}}
        </button>

        <div class="buttonGroup">
            <!--Open modal window-->
            <button class="button"
                    @click="toggleModal"
            >
                Open modal</button>

            <!--Clear local storage-->
            <button class="button"
                    @click="clearLocalStorage"
            >
                Clear emails
            </button>
        </div>


    </nav>
</template>

<script>
    export default {
        props: {
            toggleSideMenu: Function,
            sideMenuOpen: Boolean,
            toggleModal: Function,
        },
        methods: {
            clearLocalStorage() {
                localStorage.clear()
            }
        }
    }
</script>

<style lang="sass" scoped>

    @import "../../assets/variables/variables"

    .navigation
        width: 100%
        height: 40px
        box-shadow: 2px 2px 2px $shadowColor
        display: flex
        padding: 20px 0
        justify-content: space-between

    .buttonGroup
        margin-right: 200px

    .button
        border: 2px solid $purpleColor
        width: 150px
        height: 40px
        background-color: $whiteColor
        font-family: $appFont
        font-weight: 700
        -webkit-border-radius: 35px
        -moz-border-radius: 35px
        border-radius: 35px
        margin: 0 20px
        transition: .3s
        &:hover
            color: $whiteColor
            background-color: $purpleColor

    .sideMenuButton
        height: 40px
        width: 40px
        background-color: $whiteColor
        -webkit-border-radius: 50%
        -moz-border-radius: 50%
        border-radius: 50%
        border: 2px solid $gray4
        color: $purpleColor
        font-size: 30px
        line-height: 40px
        margin: 0 20px
        &:hover
            background-color: $purpleColor
            color: $whiteColor
            border: 2px solid $purpleColor
            transition: .3s

</style>
