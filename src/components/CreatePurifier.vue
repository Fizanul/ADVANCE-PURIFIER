<template>
  <div class="hello">
    <div v-if="!redirectToInAdvance">
      <h1>{{ msg }}</h1>
      <label>Size of Purifier:</label>
      <input type="number" v-model="sizeOfPurifier" id="sizeOfPurifier" required />
      <br />
      <br />
      <label>Quantity of Water in Purifier :</label>
      <input type="number" v-model="sizeOfWater" id="waterSizeInPurifier" required />
      <br />
      <br />
      <button @click="CreateNewPurifier()">Submit</button>
    </div>
    <InAdvancePurifier
      v-if="redirectToInAdvance"
      :forRefillTheWater="this.forRefillTheWater"
      :sizeOfWater="this.sizeOfWater"
      :sizeOfPurifier="this.sizeOfPurifier"
    />
  </div>
</template>

<script>
import InAdvancePurifier from "./InAdvancePurifier.vue";

export default {
  name: "CreatePurifier",
  components: {
    InAdvancePurifier
  },
  data: function() {
    return {
      redirectToInAdvance: false,
      sizeOfPurifier: "",
      sizeOfWater: "",
      forRefillTheWater: ""
    };
  },
  props: {
    msg: String
  },
  methods: {
    CreateNewPurifier() {
      this.forRefillTheWater = this.sizeOfWater;
      if (Number(this.sizeOfPurifier) > 12 || Number(this.sizeOfWater) > 12) {
        alert(
          "Please enter 12 or lower than 12 because limit of our Purifier is 12"
        );
      } else if (
        Number(this.sizeOfPurifier) <= 0 ||
        Number(this.sizeOfWater) <= 0
      ) {
        alert("Please enter proper value");
      } else if (Number(this.sizeOfPurifier) < Number(this.sizeOfWater)) {
        alert("Please enter less or equal to the size of purifier");
      } else {
        this.redirectToInAdvance = true;
      }
    }
  }
};
</script>
