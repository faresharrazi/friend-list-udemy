<template>
  <li>
    <p id="name">
      {{ name }}
    </p>
    <button @click="toggleShowDetails">
      {{ !detailsAreVisible ? "Show" : "Hide" }} details
    </button>
    <section v-if="detailsAreVisible">
      <p><span id="email">Email</span>: {{ email }}</p>
      <p><span id="phone">Phone</span>: {{ phone }}</p>
    </section>
  </li>
</template>

<script>
export default {
  // props: ["name", "email", "phone"],
  props: {
    name: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: false,
    },
    phone: {
      type: String,
      required: false,
      default: "911",
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleShowDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
  },
};
</script>

<style scoped>
#name,
#email,
#phone {
  font-weight: 700;
}

#name {
  font-size: larger;
}

li {
  list-style-type: none;
  text-align: center;
  border: 1px solid grey;
  background-color: beige;
  width: 300px;
  margin-bottom: 1rem;
}

button {
  margin-bottom: 1rem;
}
</style>
