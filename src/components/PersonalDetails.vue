<template>
  <header><h1>Personal Details</h1></header>
  <div v-for="data in details" :key="data.firstname">
    <h4>First Name : {{data.firstname}}</h4>
    <h4>Last Name : {{data.lastname}}</h4>
    <p>Gender : {{data.gender}}</p>
    <p>Country : {{data.country}}</p>
    <p>Region : {{data.region}}</p>
    <p>City : {{data.city}}</p>
    <p>Pin : {{data.pin}}</p>
    <p>Email :{{data.email}}</p>
    <p>Phone : {{data.phone}}</p>
  </div>
</template>

<script>
export default {
  inject: ["details"],
};
</script>
<style scoped>
/* Style for the header */
header {
  text-align: center;
  margin-bottom: 20px;
}

header h1 {
  font-size: 24px;
  margin: 0;
}

/* Style for individual data blocks */
div {
  border: 1px solid #ccc;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 5px;
  background-color: #f9f9f9;
  text-align: center;
  line-height: 40px;
}

/* Style for data labels and values */
h4, p {
  margin: 0;
}

h4 {
  font-weight: bold;
  margin-bottom: 5px;
}

/* Style for the whole template */
body {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

/* Add some margin to the bottom of the page */
body::after {
  content: "";
  display: block;
  height: 20px;
}



</style>
