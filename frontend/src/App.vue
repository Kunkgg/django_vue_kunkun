<script setup></script>

<template>
  <h1>Kun Kun</h1>
  <p>
    {{ message }}
  </p>
</template>
<script>
export default {
  data() {
    return {
      message: "empty",
    };
  },
  created() {
    this.fetchMessage();
  },
  methods: {
    fetchMessage() {
      fetch("/api/kunkun/")
        .then((response) => response.json())
        .then((data) => {
          this.message = data.message;
        })
        .catch((error) => {
          console.error("Error fetching message:", error);
        });
    },
  },
};
</script>

<style scoped></style>
