<template>
  <header><h1>Personal Form</h1></header>
  <form v-if="submit" @submit.prevent="submitData">
    <div class="demo" :class="{ invalid: userfirstname === 'invalid' }">
      <label for="firstname">First Name:</label>
      <input
        type="text"
        name="firstname"
        id="firstname"
        v-model.trim="firstname"
        @blur="validFirstname"
      />
      <p v-if="userfirstname === 'invalid'">Please enter information</p>
    </div>
    <div>
      <label for="lastname">Last Name:</label>
      <input type="text" name="lastname" id="lastname" v-model="lastname" />
    </div>
    <div>
      <label for="gender">Gender:</label>
      <input type="radio" name="male" id="male" value="male" v-model="gender" />
      <label for="male">Male</label>
      <input
        type="radio"
        name="male"
        id="female"
        value="female"
        v-model="gender"
      />
      <label for="female">Female</label>
    </div>
    <div>
      <label for="dob">DOB:</label>
      <input type="date" name="dob" id="dob" v-model="dob" />
    </div>
    <div>
      <label for="address">Address:</label>

      <select name="country" id="country" v-model="country">
        <option value="ind">IND</option>
        <option value="pak">PAK</option>
        <option value="usa">USA</option>
        <option value="ch">CH</option>
      </select>
      <select name="region" id="region" v-model="region">
        <option value="region">Region</option>
        <option value="UP">U.P</option>
        <option value="mp">M.P</option>
        <option value="mh">M.H</option>
        <option value="ka">K.A</option>
        <option value="ta">T.A</option>
      </select>
      <input
        type="text"
        name="address"
        id="address"
        placeholder="city"
        v-model="city"
      />

      <input
        type="number"
        name="address"
        id="address"
        placeholder="Pin"
        v-model="pin"
      />
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" name="email" id="email" v-model="email" />
    </div>
    <div>
      <label for="phone">Phone</label>
      <input type="number" name="phone" id="phone" v-model="phone" />
    </div>
    <div>
      <button>Submit</button>
    </div>
  </form>
  <div v-if="message" class="message">
    <p>Sucesfully Submited !</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firstname: "",
      lastname: "",
      gender: "",
      dob: "",
      country: "",
      region: "",
      city: "",
      pin: "",
      email: "",
      phone: "",
      userfirstname: "panding",
      userlastname: "pandings",
      submit:true,
      message:false
    };
  },
  inject: ["addDetails"],
  methods: {
    submitData() {
        
      if (
        this.firstname === "" ||
        this.lastname === "" ||
        this.gender === "" ||
        this.email === ""
      ) {
        alert("Fill All Details Properly");
      } else {
        this.submit=false
        this.message=true

        this.addDetails(
          this.firstname,
          this.lastname,
          this.gender,
          this.dob,
          this.country,
          this.region,
          this.city,
          this.pin,
          this.email,
          this.phone
        );
      }
    },
    validFirstname() {
      if (this.firstname === "") {
        this.userfirstname = "invalid";
      } else {
        this.userfirstname = "valid";
      }
    },
    validLastname() {
      if (this.lastname === "") {
        this.userlastname = "invalid";
      } else {
        this.userlastname = "valid";
      }
    },
  },
};
</script>

<style scoped>
/* Style for the form */
body {
  font-family: Arial, sans-serif;
}

form {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
}

/* Style for the header */
header {
  text-align: center;
  margin-bottom: 20px;
}

header h1 {
  font-size: 24px;
  margin: 0;
}

/* Style for form labels */
label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style for input fields */
input,
select {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

/* Style for invalid input */
.demo.invalid input {
  border-color: red;
}

/* Style for validation message */
.demo.invalid p {
  color: red;
  margin-top: -10px;
  margin-bottom: 10px;
}

/* Style for radio buttons and labels */

/* Style for submit button */
button {
  padding: 10px 20px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

button:hover {
  background-color: #2980b9;
}
p {
  color: red;
  text-align: center;
}
.demo.invalid input {
  border: 1px solid red;
}
.message p{
   color: green;
   text-align: center;
   text-transform: capitalize;
   font-family: sans-serif;
   font-size: large;

}

</style>
