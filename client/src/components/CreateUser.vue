<template>
<div>
    <h1>Create Watch</h1>
    <form v-on:submit.prevent = "createUser">
        
        <p>ยี่ห้อ: <input type="text" v-model="user.lastname"></p>
        <p>รุ่นนาฬิกา: <input type="text" v-model="user.email"></p>
        <p>ราคา: <input type="text" v-model="user.password"></p>
        <p><button type="submit">create user</button></p>
    </form>
    <hr>
    <div>
        
        <p>ยี่ห้อ: {{user.lastname}}</p>
        <p>รุ่นนาฬิกา: {{user.email}}</p>
        <p>ราคา: {{user.password}}</p>
    </div>
</div>
</template>
<script>
import UsersService from '@/services/UsersService'

export default {
    data(){
        return{
            user:{
                name: '',
                lastname: '',
                email: '',
                password: '',
                status: 'active'
            }
        }
    },
    methods:{
        async createUser(){
            try{
                await UsersService.post(this.user)
                this.$router.push({
                    name: 'users'
                })
            }catch(error){
                console.log(error)
            }
        }
    }    
}
</script>
<style scoped>


</style>