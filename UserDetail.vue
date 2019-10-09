<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ username }}</p>
        <p>User Age: {{ userAge }}</p>
        <p>Switch Name: {{ switchName() }}</p>
        <button @click="resetName">Reset Name</button>
        <button @click="resetFN()">Reset Name (Parent)</button>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

// User props for Parent => Child Communication
export default {
    props: {
        username: {
            type: String,
            default: 'Emma'
            // Number
            // Bool
            // Function
            // Object
            // Array
        },
        resetFN: Function,
        userAge: Number
    },
    methods: {
        switchName() {
            return this.username
            .split("")
            .reverse()
            .join("")
        },
    	resetName() {
      	this.username = 'Alec'
        this.$emit('nameWasReset', this.username)
    	}
	},
	created() {
		eventBus.$on('ageWasEdited', (age) => {
			this.userAge = age
		})
	}
};
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
