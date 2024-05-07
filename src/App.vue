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
        @delete-friend="deleteFriend"
      ></friend-contact>
    </ul>
    <button @click="toggleAddNewContact">
      {{ !addNewContact ? "+" : "cancel" }}
    </button>
    <new-friend v-if="addNewContact" @new-friend="addNewFriend"></new-friend>
  </section>
</template>

<script>
export default {
  data() {
    return {
      addNewContact: false,
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

    addNewFriend(friendObj) {
      this.friends.push({
        id: friendObj.name,
        name: friendObj.name,
        email: friendObj.email,
        phone: friendObj.phone,
        isFavorite: friendObj.isFavorite,
      });
      this.addNewContact = false;
    },

    toggleFavoriteFriend(fiendId) {
      const friendToUpdate = this.friends.find(
        (friend) => friend.id === fiendId
      );
      if (friendToUpdate) {
        friendToUpdate.isFavorite = !friendToUpdate.isFavorite;
      }
    },

    deleteFriend(friendId) {
      const index = this.friends.findIndex((friend) => friend.id === friendId);
      if (index !== -1) {
        this.friends.splice(index, 1);
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
