<template>
  <form>
    <input
      type="text"
      placeholder="name"
      v-model="newFriend.name"
      class="input-field"
    />
    <input
      type="text"
      placeholder="email"
      v-model="newFriend.email"
      class="input-field"
    />
    <input
      type="text"
      placeholder="phone"
      v-model="newFriend.phone"
      class="input-field"
    />
    <label for="isFavoriteInput" class="checkbox-label">
      <input
        type="checkbox"
        id="isFavoriteInput"
        v-model="newFriend.isFavorite"
        class="checkbox-input"
      />
      Is Favorite
    </label>
    <button type="submit" @click.prevent="addNewFriend" class="submit-button">
      Add
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newFriend: {
        name: "",
        email: "",
        phone: "",
        isFavorite: false,
      },
    };
  },
  methods: {
    addNewFriend() {
      this.$emit("new-friend", this.newFriend);
      this.newFriend.name = "";
      this.newFriend.email = "";
      this.newFriend.phone = "";
      this.newFriend.isFavorite = false;
    },
  },
};
</script>

<style>
form {
  max-width: 300px;
  margin: 1rem auto;
}

.input-field {
  width: 100%;
  padding: 8px;
  margin-bottom: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.checkbox-label {
  display: block;
  margin-bottom: 16px;
}

.checkbox-input {
  margin-right: 8px;
}

.submit-button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.submit-button:hover {
  background-color: #0056b3;
}
</style>
