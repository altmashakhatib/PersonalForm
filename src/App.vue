<template>
 <button @click="selectComp('PersonalForm')">Form</button>
 <button @click="selectComp('PersonalDetails')">Details</button>



 <component :is="select">

 </component>
</template>

<script>
import PersonalDetails from './components/PersonalDetails.vue';
import PersonalForm from './components/PersonalForm.vue';
export default{
components:{
  PersonalForm,
  PersonalDetails
},
data(){
  return{
    details:[],
    select:''
  }
  

  
},
provide(){
  return{
    details:this.details,
    addDetails:this.addDetails

  }
},
methods:{
  selectComp(comp){
    this.select=comp

  },
  addDetails(firstname,lastname,gender,dob,country,region,city,pin,email,phone){
    const data ={
      firstname:firstname,
      lastname:lastname,
      gender:gender,
      dob:dob,
      country:country,
      region:region,
      city:city,
      pin:pin,
      email:email,
      phone:phone
    }
    this.details.push(data)

  }
}
}

</script>
<style scoped>
button{
  cursor: pointer;
  width: 200px;
  height: 50px;
  margin: 10px;
  border: 2px solid black;
  border-radius: 5px;
  background-color: rgb(114, 114, 220);
  color: white;
  text-align: center;
  text-transform: capitalize;
  font-family: sans-serif;
  font-size: medium;
}



</style>