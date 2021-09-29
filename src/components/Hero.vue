<template>
    <div class="Hero">
        <div class="Hero__container">
            <img :class="`Hero__container__img Hero__container__img--desktop Hero__container__img--desktop--${index}`" :src="require(`../assets/desktop-image-hero-${index}.jpg`)" alt="desktop-image-hero">
            <img :class="`Hero__container__img Hero__container__img--mobile Hero__container__img--mobile--${index}`" :src="require(`../assets/mobile-image-hero-${index}.jpg`)" alt="mobile-image-hero">
            <div class="Hero__container__actions">
                <Button :reverse="true" @clickedd="onClick" />
                <Button @clickedd="onClick"/>
            </div>
        </div>
        <div class="Hero__text">
            <h1>{{ text[index - 1].title }}</h1>
            <p>{{ text[index - 1].detailes }}</p>
            <a href="#" class="Hero__text__button" >
                Shop now
                <svg class="Hero__text__button__arrow" width="40" height="12" viewBox="0 0 40 12" xmlns="http://www.w3.org/2000/svg"><path d="M34.05 0l5.481 5.527h.008v.008L40 6l-.461.465v.063l-.062-.001L34.049 12l-.662-.668 4.765-4.805H0v-1h38.206l-4.82-4.86L34.05 0z" fill="#000" fill-rule="nonzero"/></svg>
           </a>
        </div>
    </div>
</template>

<script>
import { ref } from '@vue/runtime-core'
import Button from "./ui/Button.vue"
export default {
    name: "Hero",
    components: {
        Button
    },
    props: {
    },
    setup() {
        const text = [
            {title:"Discover innovative ways to decorate",detailes:"We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love."},
            {title:"We are available all across the globe",detailes:"With stores all over the world, it's easy for you to find furniture for your home or place of business. Locally, we’re in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today."},
            {title:"Manufactured with the best materials",detailes:"Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office."},
        ]
        const index = ref(1)
        const onClick = (data) => {
            index.value += data
            index.value = index.value > 3 ? 1 : index.value
            index.value = index.value < 1 ? 3 : index.value
        }
        return { 
            index,
            text,
            onClick,
        }
    },
}
</script>

<style lang="scss" scoped>
    @import "../includeMedia";
    .Hero {
        background: white;
        display: flex;
        align-items: center;
        position: relative;
        gap: 3.5%;
        width: 100%;
        height: 70%;
        @include media("<=tablet") {
            flex-direction: column;
            gap: 9.5vw;
            height: fit-content;
            margin-bottom: 8%;
        }
        &__container {
            width: 60%;
            height: 100%;
            align-self: self-end;
            position: relative;
            @include media("<=tablet") {
                width: 100%;
                height: 100%;
                max-height: 460px;
            }
            &__img {
                width: 100%; 
                display: block;
                object-fit: cover;
                
                &--desktop {
                    height: 100%;
                    &--1 { object-position: 14%; }
                    &--2 { object-position: 21%; }
                    &--3 { object-position: 55%; }
                    @include media("<=425px") {
                        display: none;
                    }
                }
                &--mobile {
                    height: 100%;
                    &--1 { object-position: 25%; }
                    &--2 { object-position: 95%; }
                    &--3 { object-position: 35%; }                    
                    @include media(">425px") { 
                        display: none;
                    }
                }                
            }
            &__actions {
                position: absolute;
                left: 100%; bottom: 0;
                width: 9vw;
                height: 4.5vw;
                @include media("<=tablet") {
                    left: auto; 
                    right: 0; bottom: 0;
                    width: #{"max(70px,15vw)"};
                    height: #{"max(35px,7.82vw)"};
                }
            }
        }
        &__text {
            width: clamp(240px,30%,450px);
            @include media("<=tablet") {
                width: #{"max(270px,60%)"};
                text-align: start;
            }
            h1 {
                font-size: clamp(1.85rem,2.5vw,3.333rem);
                @include media("<=tablet") {
                    font-size: clamp(1.9rem, 5vw, 3rem);
                }
            }
            p {
                font-size: clamp(0.9rem,1vw,1.0833rem);
                color: hsl(0, 0%, 63%);
                line-height: 1.8;
                @include media("<=tablet") {
                    font-size: clamp(0.9rem,2vw,1.5rem);
                }
            }
            &__button {
                color:hsl(0, 0%, 27%);
                font-size: clamp(.8rem,1vw,1rem);
                text-transform: uppercase;
                letter-spacing: clamp(.7rem,1vw,1rem);
                @include media("<=tablet") {
                    font-size: clamp(9px,2vw,1rem);
                    letter-spacing: clamp(9px,2vw,1rem);
                }
                &__arrow {
                    width: 2.2vw;
                    height: #{"max(0.5rem,0.659vw)"};
                    @include media("<=tablet") {
                        width: 4.5vw; 
                        height: #{"max(9px,1.5vw)"};
                    }
                }
                &:hover {
                    color: hsl(0, 0%, 63%);
                    .Hero__text__button__arrow path {
                        fill: hsl(0, 0%, 63%);
                    }
                }
            }
            :not(:last-child) {
                margin-bottom: 9%;
            }
        }
    }
</style>
