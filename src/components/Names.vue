<template>
    <div>
        <ul class="names-container">
            <li
                v-for="item in names"
                v-bind:key="item.name"
            >
                {{item.name}} ({{item.amount}})
            </li>
        </ul>
    </div>
</template>

<script>
    import mockDatabase from "../assets/names.json"

    export default {
        name: 'Names',
        data() {
            return {
                names: mockDatabase.names.sort((item1, item2) => {
                    return (item2.amount - item1.amount)
                })
            }
        }
    }
</script>

<!-- scoped -->
<style scoped>
    .names-container {
        display: flex;
        flex-flow: column nowrap;
    }

    .names-container li {
        list-style: none;
        outline: 1px solid darkmagenta;
        padding: 1em;
        margin: 1em;
    }

    ul {
        padding: 0;
    }
</style>
