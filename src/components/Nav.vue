<template>
    <nav class="Nav">
        <div ref="elem_humbergar" class="Nav__humbergar" @click="mobile_ShowNavOptions">
             <span class="Nav__humbergar__child"/>
             <span class="Nav__humbergar__child"/>
             <span class="Nav__humbergar__child"/>
             <div ref="elem_humbergar_menu" class="Nav__humbergar__menu" />
        </div>

        <img class="Nav__logo Nav__logo" src="../assets/logo.svg" alt="logo">
        <ul ref="elem_nav_list" class="Nav__list">
            <li class="Nav__list__item">home</li>
            <li class="Nav__list__item">shop</li>
            <li class="Nav__list__item">about</li>
            <li class="Nav__list__item">contact</li>
        </ul>
    </nav>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
    name: "Nav",
    setup() {
        const elem_humbergar = ref(null)
        const elem_humbergar_menu = ref(null)
        const elem_nav_list = ref(null)
        const mobile_ShowNavOptions = () => {
            const elem_humbergar_children = document.querySelectorAll(".Nav__humbergar__child")
            if(elem_humbergar.value.classList.contains("Nav__humbergar--open")) { //close menu
                elem_humbergar.value.classList.remove("Nav__humbergar--open")
                elem_humbergar_menu.value.classList.remove("Nav__humbergar__menu--visible")
                elem_nav_list.value.classList.remove("Nav__list--mobile")
                elem_humbergar_children.forEach( element => {
                    element.classList.remove("Nav__humbergar__child--animate")
                })
                document.querySelector("html").style.overflow = "auto"
            } else { //open menu
                elem_humbergar.value.classList.add("Nav__humbergar--open")
                elem_humbergar_menu.value.classList.add("Nav__humbergar__menu--visible")
                elem_nav_list.value.classList.add("Nav__list--mobile")
                elem_humbergar_children.forEach( element => {
                    element.classList.add("Nav__humbergar__child--animate")
                })
                document.querySelector("html").style.overflow = "hidden"
            }
        }
        return {
            elem_humbergar,
            elem_humbergar_menu,
            elem_nav_list,
            mobile_ShowNavOptions
        }
    },
}
</script>

<style lang="scss" scoped>
    @import "../includeMedia";
    .only-desktop {
        @include media("<=tablet") { display: none !important; } 
    }
    .only-mobile {
        @include media(">tablet") { display: none !important; } 
    }

    .Nav {
        color: white;
        position: absolute;
        width: 100%;
        z-index: 2;
        @include media(">tablet") {
            padding: 5.33rem 0 0 5.33rem;
        }
        @include media("<=tablet") {
            display: flex;
            gap: calc(50% - 4rem);
            padding: 4rem 0 0 2rem;
                        
        }
        &__logo {
            width: 5.333rem;
            height: min-content;
            @include media(">tablet") {
                margin-right: 4.75rem;
            }
        }
        &__list {
            display: inline-block;
            &__item {
                position: relative;
                display: inline-block;
                cursor: pointer;
                height: fit-content;
                &:not(:last-child) {
                    margin-right: 2.833rem;
                }
                @include media(">tablet") {
                    &::after {
                        content: "";
                        background: white;
                        position: absolute;
                        top: 200%; left: 50%;
                        transform: translateX(-50%);
                        width: 48%;
                        height: 0.167rem;  
                        opacity: 0;
                        transition: opacity 200ms ease-in-out;
                    }
                    &:hover::after{
                        opacity: 1;
                    } 
                }
            }
            @include media("<=tablet") {
                visibility: hidden;
                opacity: 0;
                &--mobile {
                    display: flex;
                    width: 50%;
                    min-width: 220px;
                    justify-content: space-between;

                    transition: opacity 200ms ease-in-out;
                    position: absolute;
                    visibility: visible;
                    opacity: 1;
                    left: 25%;
                    color: black;
                    font-weight: 700;
                    font-size: clamp(1.08rem,3vw,1.333rem);
                    .Nav__list__item {
                        margin: 0
                    }       
                }
            } 
        }
        &__humbergar {
            @extend .only-mobile;   
            &__child {
                background: white;
                display: block;
                width: 1.833rem;
                height: 0.167rem;
                transition: all 200ms ease-in-out;
                &:not(:last-child) {
                    margin-bottom: 0.333rem;
                }  
                &--animate {
                    position: relative;
                    z-index: 1;
                    background: hsl(0, 0%, 63%);
                    &:first-child {
                        transform: translate(0px,6px) rotate(45deg);
                    }
                    &:nth-child(3n) {
                        transform: translate(0px,-6px) rotate(-45deg);
                    }
                    &:nth-child(2n) {
                        opacity: 0;
                    }   
                }
            }  
            &__menu {
                visibility: hidden;
                position: absolute;
                background: white;
                top: 0;
                left: 0;
                opacity: 0;
                width: 100%;
                height: 14vw;
                min-height: 100px;
                transition: all 200ms ease-in-out;
                box-shadow: #00000080 0 0px 0 1000px;

                &--visible {
                    visibility: visible;
                    opacity: 1;
                }
            }
  
        }

    } 
</style>