<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<!-- eslint-disable vuejs-accessibility/label-has-for -->
<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label>Email</label>
      <input type="email" v-model="email" required>
      <label>Password</label>
      <input type="password" v-model="password" required>
      <div v-if="passwordError" class="error">{{ passwordError }}</div>

      <label>Role:</label>
      <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="tester">Tester</option>
      </select>
      <div class="terms">
        <input type="checkbox" v-model="terms">
        <label>Accept terms and conditions</label>
      </div>
      <label>--------------------------------------</label>
      <div>
        <input type="checkbox" value="Jonh" v-model="names">
        <label>Jond</label>
      </div>
      <div>
        <input type="checkbox" value="Max" v-model="names">
        <label>Max</label>
      </div>
      <label>--------------------------------------</label>
      <div>
        <label>Skills</label>
        <input type="text" v-model="tempSkill" @keyup.enter="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
          <span @click="deleteSkill(skill) ">{{ skill }}</span>
        </div>
      </div>
      <div class="submit">
        <button type="submit">Submit</button>
      </div>
    </form>
    <!-- <p>email is: {{ email }}</p>
    <p>password is: {{ password }}</p>
    <p>role is: {{ role }}</p>
    <p>terms is: {{ terms }}</p>
    <p>names are: {{ names }}</p> -->
  </div>
</template>

<script>
export default {
  name: 'FormInput',
  data() {
    return {
      email: '',
      password: '',
      role: 'tester',
      terms: false,
      names: [],
      tempSkill: '',
      skills: [],
      passwordError: '',
    };
  },
  methods: {
    addSkill(e) {
      console.log(e);
      if (this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = '';
      }
    },
    deleteSkill(data) {
      console.log(data);
      this.skills = this.skills.filter((item) => item !== data);
    },
    handleSubmit() {
      this.passwordError = this.password.length > 3 ? '' : 'Password is invalid';
      if (this.passwordError === '') {
        console.log('form was submited');
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  input[type='checkbox']{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
  .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit {
    text-align: center;
}

.error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
}
</style>
