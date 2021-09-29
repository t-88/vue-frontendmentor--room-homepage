<template>
    <div class="About">
        <div class="About__container">
            <img src="@/assets/image-about-dark.jpg" alt="about-dark">
        </div>
        <div class="About__text">
            <h1>About our furniture</h1>
            <p>
                Our multifunctional collection blends design and function to suit your individual taste.
                Make each room unique, or pick a cohesive theme that best express your interests and what
                inspires you. Find the furniture pieces you need, from traditional to contemporary styles
                or anything in between. Product specialists are available to help you create your dream space.
            </p>
        </div>
        <div class="About__container">
            <img src="@/assets/image-about-light.jpg" alt="about-light">
        </div>
    </div>
</template>

<script>
export default {
    name: "",
    setup() {

    },
}
</script>

<style lang="scss" scoped>
    @import "../includeMedia";
    .About {
        display: grid;
        grid-template-columns: 31% auto 31%;
        height: 30%;
        @include media("<=tablet") {
            height: auto;
            grid-template-columns: auto;
        }
        &__container {
            width: 100%;
            height: 100%;
            min-height: 0;
            &:first-child img {
                object-position: 100%;
            }
            img {
                height: 100%;
                width: 100%;
                object-fit: cover;
            }
        }
        &__text {
            padding: 10.5% 8%;
            min-height: 0;

            h1 {
                font-size: clamp(1rem,1.32vw,2rem);
                text-transform: uppercase;
                margin-bottom: 1.667rem;
                @include media("<=tablet") {
                    font-size: clamp(1.5rem, 5vw, 2.5rem);
                }                
            }
            p {    
                font-size: clamp(0.903rem,0.8vw,1.083rem);
                line-height: 1.8;
                color: hsl(0, 0%, 63%);
                @include media("<=tablet") {
                    font-size: clamp(0.9rem, 2vw, 1.5rem);
                }
            }
        }

    }
</style>