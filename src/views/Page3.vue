<script>
import PATHS from "../Routes/paths";
export default {
  data() {
    return { submitData: null };
  },
  methods: {
    onBack() {
      window.location.pathname = PATHS.PAGE_2;
    },
    onBuy() {
      window.location.pathname = PATHS.PAGE_1;
      localStorage.removeItem("submitData");
    },
  },
  mounted() {
    const submitDataString = localStorage.getItem("submitData");
    if (!submitDataString) {
      window.location.pathname = PATHS.PAGE_2;
    } else {
      const submitData = JSON.parse(submitDataString);
      this.submitData = submitData;
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="content">
      <h1 class="bold">Hello There!</h1>
      <h3 class="bold">{{ submitData?.name }}</h3>
      <p>Name: {{ submitData?.name }}</p>
      <p>Age: {{ submitData?.age }}</p>
      <p>Where do you live: {{ submitData?.country.name }}</p>
      <p>Package: {{ submitData?.Package.name }}</p>
      <p>
        Premium: {{ submitData?.premium }}{{ submitData?.country.currency }}
      </p>
      <div class="actions">
        <button class="button back-button" @click="onBack">Back</button>
        <button class="button next-button" @click="onBuy">Buy</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  padding-top: 15vh;
  display: flex;
  justify-content: center;
}
.content {
  width: 80%;
  max-width: 800px;
  min-width: 280px;
  background-color: #eee;
  text-align: center;
  padding: 100px 20px;
}
.bold {
  font-weight: bold;
  margin-bottom: 20px;
}
p {
  margin-bottom: 20px;
}
.actions {
  margin-top: 50px;
}
.button {
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
