<template>
  <li>
    <p id="name">
      {{ name }} <span>{{ isFavorite ? "(Favorite)" : "" }}</span>
    </p>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleShowDetails">
      {{ !detailsAreVisible ? "Show" : "Hide" }} details
    </button>
    <section v-if="detailsAreVisible">
      <p><span id="email">Email</span>: {{ email }}</p>
      <p><span id="phone">Phone</span>: {{ phone }}</p>
      <button class="delete-friend" @click="deleteFriend">Delete</button>
    </section>
  </li>
</template>

<script>
export default {
  // props: ["name", "email", "phone"],
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
      validator: function (value) {
        return value != "";
      },
    },
    email: {
      type: String,
      required: false,
    },
    phone: {
      type: String,
      required: false,
      default: "911",
      validator: function (value) {
        const numericRegex = /^[0-9]+$/;
        return numericRegex.test(value);
      },
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: ["toggle-favorite", "delete-friend"],
  // emits: {
  //   "toggle-favorite": function (id) {
  //     if (id) {
  //       return true;
  //     } else {
  //       console.warn("ID IS MISSING");
  //       return false;
  //     }
  //   },
  // },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleShowDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },

    deleteFriend() {
      this.$emit("delete-friend", this.id);
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

.delete-friend {
  padding: 8px 16px;
  background-color: #dc3545; /* Red color */
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.delete-friend:hover {
  background-color: #c82333; /* Darker red color on hover */
}
</style>
