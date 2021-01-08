<template>
    <div>
        <h2>
            Total: {{calculateSum(names.map(item => {
                return item.amount
            }))}}
        </h2>

        <span class="individual-name-amount">
            <label for="individual-name-input">
                Search for a name:
            </label>
            <input
                id="individual-name-input"
                v-model="nameInput"
            />
            <p v-if="getAmount(nameInput)">
                Total of {{nameInput}}:
                {{getAmount(nameInput)}}
            </p>
        </span>

        <span class="sorting-buttons">
            <button @click="sortByName(names)">
                Sort by name
            </button>
            <button @click="sortByAmount(names)">
                Sort by amount
            </button>
        </span>

        <ul class="names-container">
            <li
                v-for="item in names"
                v-bind:key="item.name"
            >
                <span> {{item.name}} </span>
                <span> {{item.amount}} </span>
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
                names: this.sortByAmount(mockDatabase.names),
                nameInput: ""
            }
        },
        methods: {
            sortByName(names) {
                return names.sort((item1, item2) => {
                    if (item1.name < item2.name) {
                        return -1
                    } else if (item1.name > item2.name) {
                        return 1
                    } else {
                        return 0
                    }
                })
            },
            sortByAmount(names) {
                return names.sort((item1, item2) => {
                    return (item2.amount - item1.amount)
                })
            },
            calculateSum(amounts) {
                return amounts.reduce((sum, summand) => {
                    return (sum + summand)
                })
            },
            getAmount(nameInput) {
                const matchedName = this.names.find(item => {
                    return (
                        item.name.toLowerCase()
                        === nameInput.toLowerCase()
                    )
                })
                if (matchedName) {
                    return matchedName.amount
                }
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
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
    }

    .sorting-buttons {
        display: flex;
        justify-content: space-between;
    }

    .sorting-buttons button {
        background-color: cyan;
    }

    ul {
        padding: 0;
    }

    input {
        background-color: violet;
    }
</style>
