<script>
export default {
  data() {
    return {
      friends: [
        {
          id: "Hou",
          name: "Houssam",
          email: "Samsam@yahoo.ca",
        },
      ],
    };
  },
};
</script>

<template>
  <section>
    <h1>Friend List</h1>
    <ul>
      <li v-for="f in friends" :key="f.id">
        <p>Name: {{ f.name }} - Email: {{ f.email }}</p>
      </li>
    </ul>
  </section>
</template>
