<template>
    <div class="overlay">
        <div class="modal"
             @click=" (e) => {e.stopPropagation()} "
        >

            <!--Overlay section-->
            <div class="bigWhiteOverlay">
                <div class="bigPurpleOverlay"></div>
            </div>

            <div class="imageHolder">
                <img class="image" src="../../assets/images/image_38.png" alt="">
            </div>

            <div class="smallWhiteOverlay">
                <div class="smallPurpleOverlay"></div>
            </div>

            <img class="closeButton" src="../../assets/icons/closeIcon.png" alt="close" @click="toggleModal">

            <!--Text section-->
            <div class="modalInner">
                <h1 class="innerTitle">10%<span class="titleSpan">off</span></h1>
                <h3 class="innerSubtitle">for your first order</h3>
                <div class="innerline"></div>
                <p class="innerParagraph">Subscribe to receive 10% off promo code abs exclusive offers and deals</p>

                <!--Input section-->
                <ModalInput></ModalInput>

            </div>


        </div>
    </div>
</template>

<script>
    import ModalInput from "./modalInput/ModalInput";

    export default {
        props: {
            toggleModal: Function,
        },
        components: {
            ModalInput: ModalInput
        }
    }
</script>

<style lang="sass" scoped>

    @import "../../assets/variables/variables"

    .overlay
        background-color: $modalOverlayColor
        width: 100%
        height: 100%
        position: fixed
        top: 0
        left: 0
        display: flex
        justify-content: center
        align-items: center

    .modal
        width: 864px
        height: 502px
        background-color: $whiteColor
        -webkit-border-radius: 8px
        -moz-border-radius: 8px
        border-radius: 8px
        position: relative
        overflow: hidden

    .imageHolder
        -webkit-border-radius: 8px
        -moz-border-radius: 8px
        border-radius: 8px
        display: flex
        justify-content: flex-end

    .image
        -webkit-border-radius: 8px
        -moz-border-radius: 8px
        border-radius: 8px

    .bigWhiteOverlay
        position: absolute
        width: 1000px
        height: 500px
        background-color: $whiteColor
        z-index: 1
        left: -360px
        transform: rotate(60deg)
        overflow: hidden

    .bigPurpleOverlay
        width: 1000px
        height: 300px
        background-color: $purpleColor
        transform: rotate(15deg)
        position: relative
        top: -338px

    .smallWhiteOverlay
        width: 1000px
        height: 500px
        position: absolute
        transform: rotate(60deg)
        top: 0
        right: -820px
        background-color: $whiteColor
        z-index: 2
        overflow: hidden

    .smallPurpleOverlay
        width: 1000px
        height: 300px
        position: absolute
        transform: rotate(15deg)
        background-color: $purpleColor
        top: 585px

    .closeButton
        z-index: 2
        position: absolute
        top: 3px
        right: 4px
        -webkit-border-radius: 10px
        -moz-border-radius: 10px
        border-radius: 10px
        padding: 5px
        &:hover
            box-shadow: 1px 1px 1px $shadowColor, -1px -1px 1px $shadowColor

    .modalInner
        position: absolute
        z-index: 3
        top: 40px
        left: 32px
        width: 302px

    .innerTitle
        font-family: $appFont
        font-weight: 700
        font-size: 104px
        color: #2F3639

    .titleSpan
        font-size: 24px
        color: $gray1

    .innerSubtitle
        font-family: $appFont
        font-weight: 700
        color: $gray3
        font-size: 24px
        line-height: 24px

    .innerline
        width: 67px
        height: 2px
        background-color: $purpleColor
        margin: 26px 0

    .innerParagraph
        font-family: $appFont
        font-weight: 400
        font-size: 14px
        color: $gray2

</style>
