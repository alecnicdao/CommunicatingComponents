<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
        <button @click="changeName">Change My Name</button>
        <p>Name: {{ name }}</p>
        <p>User Age: {{ age }}</p>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
                <app-user-detail 
                :username="name"
                :resetFN="resetName"
                :userAge="age" 
                @nameWasReset="name = $event">
                </app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6">
                <app-user-edit
                :userAge="age"
                @ageWasEdited="age = $event">
                </app-user-edit>
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {
        data() {
            return {
                name: 'Alec',
                age: 23
            }
        },
        methods: {
            changeName() {
                this.name = 'Monique'
            },
            resetName() {
                this.name = 'Alec'
            }
        },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        }
    };
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
