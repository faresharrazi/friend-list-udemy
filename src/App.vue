<template>
  <section>
    <h1>Friend List</h1>
    <ul>
      <friend-contact
        v-for="f in friends"
        :id="f.id"
        :name="f.name"
        :email="f.email"
        :phone="f.phone"
        :is-favorite="f.isFavorite"
        :key="f.id"
        @toggle-favorite="toggleFavoriteFriend"
      ></friend-contact>
    </ul>
    <button @click="toggleAddNewContact">
      {{ !addNewContact ? "+" : "cancel" }}
    </button>
    <div v-if="addNewContact">
      <input type="text" placeholder="name" v-model="newFriend.name" />
      <input type="text" placeholder="email" v-model="newFriend.email" />
      <input type="text" placeholder="phone" v-model="newFriend.phone" />
      <input
        type="checkbox"
        name="isFavoriteInput"
        id="isFavoriteInput"
        v-model="newFriend.isFavorite"
      />
      <button type="submit" @click.prevent="addNewFriend">Add</button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      addNewContact: false,
      newFriend: {
        name: "",
        email: "",
        phone: "",
        isFavorite: false,
      },
      friends: [
        {
          id: "Hou",
          name: "Houssam Bounasri",
          email: "Samsam@yahoo.ca",
          phone: "22 546 123",
          isFavorite: true,
        },
        {
          id: "Sani",
          name: "Yassine Sghir",
          email: "Baim@yahoo.gr",
          phone: "22 512 052",
          isFavorite: false,
        },
        {
          id: "Lee",
          name: "Ali Fathallah",
          email: "Lee@yahoo.fr",
          phone: "98 216 256",
          isFavorite: false,
        },
      ],
    };
  },
  methods: {
    toggleAddNewContact() {
      this.addNewContact = !this.addNewContact;
    },

    addNewFriend() {
      this.friends.push({
        id: this.newFriend.name,
        name: this.newFriend.name,
        email: this.newFriend.email,
        phone: this.newFriend.phone,
        isFavorite: this.newFriend.isFavorite,
      });
      this.newFriend.name = "";
      this.newFriend.email = "";
      this.newFriend.phone = "";
      this.newFriend.isFavorite = false;
      this.addNewContact = false;
    },

    toggleFavoriteFriend(value) {
      const friendToUpdate = this.friends.find((friend) => friend.id === value);
      if (friendToUpdate) {
        friendToUpdate.isFavorite = !friendToUpdate.isFavorite;
      }
    },
  },
};
</script>

<style scoped>
h1 {
  width: 500px;
  text-align: center;
  border: 2px solid black;
  color: aliceblue;
  background-color: brown;
}
section {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
