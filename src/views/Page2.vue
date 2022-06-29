<script>
import PATHS from "../Routes/paths";
export default {
  data() {
    return {
      name: "",
      age: null,
      country: null,
      Package: 4,
      countries: [
        { id: 1, name: "Hong Kong", currency: "HKD", rate: 1 },
        { id: 2, name: "USA", currency: "USD", rate: 2 },
        { id: 3, name: "Australia", currency: "AUD", rate: 3 },
      ],
      Packages: [
        { id: 4, name: "Standard", feeRate: 0 },
        { id: 5, name: "Safe", feeRate: 0.5 },
        { id: 6, name: "Super Safe", feeRate: 0.75 },
      ],
    };
  },
  methods: {
    onSubmit() {
      if (this.age > 100) window.location.pathname = PATHS.PAGE_2_ERROR;
      else {
        const formData = {
          name: this.name,
          age: this.age,
          country: this.selectedCountry,
          Package: this.selectedPackage,
          premium: this.premium,
        };
        localStorage.setItem("submitData", JSON.stringify(formData));
        window.location.pathname = PATHS.PAGE_3;
      }
    },
    onBack() {
      window.location.pathname = PATHS.PAGE_1;
    },
  },
  computed: {
    selectedCountry() {
      return (
        this.countries.find((item) => item.id === this.country) || { rate: 0 }
      );
    },
    selectedPackage() {
      return (
        this.Packages.find((item) => item.id === this.Package) || {
          feeRate: -1,
        }
      );
    },
    standardValue() {
      return 10 * this.age * this.selectedCountry.rate;
    },
    premium() {
      return this.standardValue * (1 + this.selectedPackage.feeRate);
    },
  },
  mounted() {
    const submitDataString = localStorage.getItem("submitData");
    if (submitDataString) {
      const submitData = JSON.parse(submitDataString);
      this.name = submitData.name;
      this.age = submitData.age;
      this.country = submitData.country.id;
      this.Package = submitData.Package.id;
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="content">
      <h1 class="header">Tell us about yourself</h1>
      <form class="form" @submit.prevent="onSubmit">
        <div class="form-group">
          <label for="name">Name</label>
          <input
            id="name"
            type="text"
            v-model="name"
            placeholder="Add text"
            required
          />
        </div>
        <div class="form-group">
          <label for="age">Age</label>
          <input
            id="age"
            type="number"
            v-model="age"
            placeholder="Add number"
            required
          />
        </div>
        <div class="form-group">
          <label for="country">Where do you live?</label>
          <select id="country" v-model="country" required>
            <option
              v-for="country in countries"
              :value="country.id"
              :key="country.id"
            >
              {{ country.name }}
            </option>
          </select>
        </div>
        <div
          class="form-group radio-group"
          v-for="_package in Packages"
          :key="_package.id"
        >
          <input
            type="radio"
            :id="_package.id"
            :value="_package.id"
            v-model="Package"
          />
          <label for="_package.id" v-if="_package.id === 4 || !premium">{{
            _package.name
          }}</label>
          <label for="_package.id" v-else
            >{{ _package.name }} (+{{ standardValue * _package.feeRate
            }}{{ selectedCountry.currency }},
            {{ _package.feeRate * 100 }}%)</label
          >
        </div>
        <h2 class="premium">
          <span class="header premium-text"> Your premium is: </span>
          <span class="header"
            >{{ premium }}{{ selectedCountry.currency }}</span
          >
        </h2>
        <div class="actions">
          <button class="button back-button" @click="onBack">Back</button>
          <button class="button next-button" type="submit">Next</button>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container {
  padding: 10vh 0;
  display: flex;
  justify-content: center;
}

.form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-group {
  margin-bottom: 15px;
}
.form-group:not(.radio-group) {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.form-group.radio-group {
  text-align: left;
  width: 250px;
}

:not(.radio-group) > input,
select {
  height: 40px;
  width: 250px;
}

input[type="radio"] {
  margin-right: 5px;
}

label {
  margin-bottom: 5px;
}

.content {
  width: 80%;
  max-width: 800px;
  min-width: 280px;
  background-color: #eee;
  text-align: center;
  padding: 100px 20px;
}
.header {
  font-weight: bold;
  margin-bottom: 20px;
}
.premium {
  margin: 50px 0;
}
.premium-text {
  margin-right: 30px;
}
.button {
  margin-top: 25px;
  width: 100px;
  border-radius: 6px;
  margin: 0 8px;
}
.next-button {
  padding: 10px 0;
  background-color: #000;
  color: #fff;
  border-width: 0;
}
.back-button {
  padding: 8px 0;
  background-color: #fff;
  border-width: 1;
  color: #000;
}
</style>
