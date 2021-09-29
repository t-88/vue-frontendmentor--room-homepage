<template>
    <a href="#" class="Button" @click="onClick">
        <svg v-if="reverse" class="Button__svg" width="14" height="24" viewBox="0 0 14 24" xmlns="http://www.w3.org/2000/svg"><path d="M13 0L1 12l12 12" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>    
        <svg v-if="!reverse" class="Button__svg" width="14" height="24"  viewBox="0 0 14 24" xmlns="http://www.w3.org/2000/svg"><path d="M1 0l12 12L1 24" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
    </a>
</template>

<script>
export default {
    name: "",
    props: {
        reverse: {default: false}
    },
    setup(props,{emit}) {
        const onClick = (e) => {
            e.preventDefault()
            emit("clickedd", props.reverse === false ? 1 : -1)
        }
        return {
            onClick
        }
    },
}
</script>

<style lang="scss" scoped>
    .Button {
        display: inline-flex;
        align-items: center;
        justify-content: center;

        background: black;
        width: 50%;
        height: 100%;
        &:hover {
            background: hsl(0, 0%, 27%);
        }
        &__svg {
            width: 17%;
        }
    }
</style>