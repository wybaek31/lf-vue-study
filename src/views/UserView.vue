<template>
  <div class="user-container">
    <div>
      <i class="fas fa-user-circle"></i>
    </div>
    <div class="user-description">
      {{userInfo.id}}
    </div>
  </div>
</template>

<script>
import { fetchUser } from '../api/index.js';

export default {
  data() { 
    return {
      userId: "",
      userInfo: {}
    }
  },
  created() {
    this.userId = this.$route.params.id;
    this.getUserInfo(this.userId);
  },
  methods: {
    getUserInfo(userId) {
      return new Promise((resolve, reject) => {
        fetchUser(userId)
          .then(response => {
            this.userInfo = response.data;
            resolve();
          })
          .catch(error => {
            reject(error);
          });
      });
    },
  }
}
</script>

<style scoped>
.user-container {
  display: flex;
  align-items: center;
}
.fa-user-circle {
  font-size: 2.5rem;
}
.user-description {
  padding-left: 8px;
}
.time {
  font-size: 0.7rem;
  color: #828282;
}
</style>
