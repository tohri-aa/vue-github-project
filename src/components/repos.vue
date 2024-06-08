<script>
    import axios from 'axios'

    export default {
  data() {
    return {
      repos: []
    };
  },
  async created() {
    try {
      const response = await axios.get('https://api.github.com/users/tohri-aa/repos');
      this.repos = response.data;
    } catch (error) {
      console.error(error);
    }
  }
};
</script>

<template>
    <h1>My Repositories</h1>
    <ul>
        <RouterLink to="/" v-for="repo in repos">
            <h3>
                {{ repo.name }}
            </h3>
            <p>{{ repo.description ? repo.description : "no description"}}</p>
        </RouterLink>
    </ul>
</template>
