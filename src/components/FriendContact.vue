<template>
  <li>
    <p id="name">
      {{ friend.name }}
    </p>
    <button @click="toggleShowDetails">
      {{ !detailsAreVisible ? "Show" : "Hide" }} details
    </button>
    <section v-if="detailsAreVisible">
      <p><span id="email">Email</span>: {{ friend.email }}</p>
      <p><span id="phone">Phone</span>: {{ friend.phone }}</p>
    </section>
  </li>
</template>

<script>
export default {
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: "Hou",
        name: "Houssam Bounasri",
        email: "Samsam@yahoo.ca",
        phone: "22 546 123",
      },
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
