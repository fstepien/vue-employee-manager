<template>
    <div id='newemployee'>
    
        <h3>New Employee</h3>
        <div class="row">
            <form @submit.prevent="saveEmployee" class="col s12">
                <div class="row">
                    <div class="input-filed col s12">
                        <input type="text" v-model="employee_id" required>
                        <lable>Employee ID#</lable>
                    </div>
                </div>
                <div class="row">
                    <div class="input-filed col s12">
                        <input type="text" v-model="name" required>
                        <lable>Name</lable>
                    </div>
                </div>
                <div class="row">
                    <div class="input-filed col s12">
                        <input type="text" v-model="dept" required>
                        <lable>Department</lable>
                    </div>
                </div>
                <div class="row">
                    <div class="input-filed col s12">
                        <input type="text" v-model="position" required>
                        <lable>Position</lable>
                    </div>
                </div>
                <button type="submit" class="btn">Submit</button>
                <router-link to="/" class="btn grey">Cancel</router-link>
            </form>
        </div>
    </div>
</template>
<script>
import db from './firebaseInit'
export default {
   name: 'newemployee',
   data () {
       return {
           employee_id: null, 
           name: null, 
           dept: nbull, 
           position: null
       }
   },
   methods: {
       saveEmployee() {
           db.collection('employees').add({
               employee_id: this.employee_id,
               name: this.name, 
               dept: this.dept,
               position: this.position
           })
           .then(docRef => this.$router.push('/')
           )
           .catch(err => console.log(err))
       }
   }
}
</script>
