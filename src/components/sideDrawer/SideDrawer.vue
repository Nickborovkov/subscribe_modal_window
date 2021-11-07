<template>
    <div class="sideDrawer"
         :class="{sideDrawerActive: sideMenuOpen}"
    >
        <!--SideMenu template layout-->
        <div class="logoSection">
            <h1 class="logo"><span class="logoSpan">L</span>OGO</h1>
            <div class="buttonGroup">
                <button class="button">EN</button>
                <button class="button">US</button>
            </div>
        </div>
        <div :key="item" v-for="item in 15">
            <div class="item"></div>
        </div>
    </div>

</template>

<script>
    export default {
        props: {
            sideMenuOpen: Boolean
        }
    }
</script>

<style lang="sass" scoped>

    @import "../../assets/variables/variables"

    .sideDrawer
        background-color: $gray1
        width: 250px
        min-height: 100vh
        top: 0
        left: 0
        transition: 1s

    .sideDrawerActive
        left: 0px

    .logoSection
        border-bottom: 1px solid $gray3

    .logo
        font-family: $appFont
        font-weight: bold
        color: $whiteColor
        text-align: center
        padding: 30px 0

    .logoSpan
        color: $purpleColor

    .buttonGroup
        display: flex
        justify-content: center
        padding-bottom: 20px

    .button
        font-family: $appFont
        text-align: center
        font-size: 20px
        width: 100px
        color: $whiteColor
        border: none
        background-color: transparent
        &:first-child
            border-right: 1px solid $gray3

    .item
        width: 70%
        height: 30px
        background-color: $gray3
        margin: 20px auto
        -webkit-border-radius: 8px
        -moz-border-radius: 8px
        border-radius: 8px
        &:hover
            background-color: $gray4

</style>
