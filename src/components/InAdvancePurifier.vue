<template>
  <div>
    <h1>Welcome to Your Advance Purifier</h1>
    <p>In my advance purifier when we click on the glass button the glass will be filled up by the water and the same process is for the bottle.</p>
    <label>Size of Purifier :</label>
    <span id="displaySizeOfPurifier">{{ sizeOfPurifier }}</span>
    <br />
    <br />
    <label>Quantity of Water in Purifier :</label>
    <span id="displaySizeOfWater" v-if="!refillTheWater">{{ sizeOfWater }}</span>
    <span id="displaySizeOfWater" v-if="refillTheWater">{{ forRefillTheWater }}</span>
    <br />
    <br />
    <button @click="glassButtonClicked()">Glass</button>
    <button @click="bottleButtonClicked()">Bottle</button>
    <button @click="normalButtonClicked()">Normal</button>
    <button @click="refillButtonClicked()">Refill Water</button>
  </div>
</template>

<script>
export default {
  name: "InAdvancePurifier",
  data: function() {
    return {
      fillGlass: '',
      fillbottle: '',
      normalWaterSize: '',
      fillNormalWater: '',
      refillTheWater: false
    };
  },
  props: {
    sizeOfPurifier: String,
    sizeOfWater: String,
    forRefillTheWater: String
  },
  methods: {
    glassButtonClicked() {
      if (this.sizeOfWater < 0.35) {
        alert(
          "Please refill the size of water because you don't have that much water"
        );
      } else {
        this.fillGlass = this.sizeOfWater - 0.35;
        this.sizeOfWater = this.fillGlass;
      }
      this.refillWater();
    },
    bottleButtonClicked() {
      if (this.sizeOfWater < 1.5) {
        alert(
          "Please refill the size of water because you don't have enough water"
        );
      } else {
        this.fillbottle = this.sizeOfWater - 1.5;
        this.sizeOfWater = this.fillbottle;
      }
      this.refillWater();
    },
    normalButtonClicked() {
      this.normalWaterSize = Number(prompt("Please enter quantity of water"));
      if (
        Number.isNaN(this.normalWaterSize) != true &&
        typeof this.normalWaterSize === "number"
      ) {
        if (Number(this.sizeOfWater) < this.normalWaterSize) {
          alert(
            "Please enter the value of water less or equal to the size of water"
          );
        } else {
          this.fillNormalWater =
            Number(this.sizeOfWater) - this.normalWaterSize;
          this.sizeOfWater = this.fillNormalWater;
        }
        this.refillWater();
      } else {
        alert("Please enter number only");
      }
    },
    refillButtonClicked() {
      let directRefillConfirmation = confirm(
        "Are you sure you want to refill the quantity of water."
      );
      if (directRefillConfirmation === true) {
        this.refillTheWater = true;
        this.sizeOfWater = this.forRefillTheWater;
        this.refillTheWater = false;
      } else {
        return false;
      }
    },
    refillWater() {
      if (Number(this.sizeOfWater) <= 1.5) {
        let refillConfirmation = confirm(
          "Your water size is very low Please refill water"
        );
        if (refillConfirmation === true) {
          this.refillTheWater = true;
          this.sizeOfWater = this.forRefillTheWater;
        } else {
          return false;
        }
      }
    }
  }
};
</script>
