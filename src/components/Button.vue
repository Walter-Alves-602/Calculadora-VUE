<template>
    <button class="button"
        @click="$emit('active', label)"
        :class="{double, triple, operation}">
        {{ label }}
    </button>
</template>

<script>
export default {
    props: {
        label:{},
        operation: {type: Boolean},
        double: {type: Boolean},
        triple: {type: Boolean}
    }
}
</script>

<style>
:root{
    --bg-Button: #f0f0f0;
    --border-Button: solid 1px #888;
}

.button{
    font-family:'Source Sans Pro', sans-serif;
    font-size: 1.4em;
    background-color: var(--bg-Button);
    border: none;
    border-right: var(--border-Button);
    border-bottom: var(--border-Button);
    outline: none;
    margin: 2px;
    border-radius: 5px;
    box-shadow: 2px 2px 3px #00000050;
}

.button:active{
    background-color: #51221C;
}

.button.double{
    grid-column: span 2;
}

.button.triple{
    grid-column: span 3;
}

.button.operation{
    background-color: #844A0F;
    color: #fff;
}
.button.operation:active{
  background-color: #844A0Fcc;  
}
</style>