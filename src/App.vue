<template>
  <section>
    <h1>Friend List</h1>
    <ul>
      <friend-contact
        v-for="f in friends"
        :name="f.name"
        :email="f.email"
        :phone="f.phone"
        :key="f.id"
      ></friend-contact>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: "Hou",
          name: "Houssam",
          email: "Samsam@yahoo.ca",
          phone: "22 546 123",
        },
        {
          id: "Sani",
          name: "Yassine",
          email: "Baim@yahoo.gr",
          phone: "22 512 052",
        },
      ],
    };
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
