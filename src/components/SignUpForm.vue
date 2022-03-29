<template>
      <form @submit.prevent="handleSubmit">
            <h1>Sign up</h1>

            <div>
                  <label for="email">Email : </label>
                  <input id="email" required type="email" v-model="email" />
            </div>

            <div>
                  <label for="password">password : </label>
                  <input id="email" required type="password" v-model="password" />
                  <p class="error" v-if="passwordError">{{ passwordError }}</p>
            </div>

            <div>
                  <label for="role">Role : </label>
                  <select id="role" v-model="role">
                        <option value="Front-End Developer">Front-End Developer</option>
                        <option value="Back-End Developer">back-End Developer</option>
                        <option value="Web-designer">Web Designer</option>
                  </select>
            </div>

            <div class="terms">
                  <input type="checkbox" required v-model="terms" />
                  <label>Accept terms and conditions </label>
            </div>

            <div>
                  <label for="skills">skills</label>
                  <input type="text" v-model="tempSkill" @keyup="addSkill" />
                  <div v-for="skill in skills" :key="skill" class="pill">
                        <span> {{ skill }} </span>
                        <span class="deleteBtn" @click="deleteSkill(skill)">X</span>
                  </div>
            </div>

            <div class="submit">
                  <button>Create an Account</button>
            </div>
      </form>
      <div class="show-information">
            <p>
                  Email : <strong> {{ email }}</strong>
            </p>
            <p>
                  password : <strong> {{ password }}</strong>
            </p>
            <p>
                  Role : <strong> {{ role }}</strong>
            </p>
            <p>
                  terms accepted : <strong> {{ terms }}</strong>
            </p>
      </div>
</template>

<script>
export default {
      data() {
            return {
                  email: "",
                  password: "",
                  role: "Front-End Developer",
                  terms: false,
                  tempSkill: "",
                  skills: [],
                  passwordError: "",
            };
      },
      methods: {
            addSkill(e) {
                  if (e.key === "," && this.tempSkill) {
                        this.tempSkill = this.tempSkill.substring(0, this.tempSkill.length - 1);

                        this.skills.push(this.tempSkill);
                        this.tempSkill = "";

                        console.log(this.skills);
                  }
            },
            deleteSkill(skill) {
                  this.skills = this.skills.filter((item) => {
                        return item !== skill;
                  });
            },
            handleSubmit() {
                  this.passwordError =
                        this.password.trim().length > 5
                              ? ""
                              : "password must be at least 6 chars long ";

                  if (!this.passwordError) {
                        console.log(`Email : ${this.email}`);
                        console.log(`Password : ${this.password}`);
                        console.log(`Role : ${this.role}`);
                        console.log(`terms accepted : ${this.email}`);
                        console.log(`skills : ${this.skills}`);
                  }
            },
      },
};
</script>

<style>
form {
      max-width: 420px;
      margin: 30px auto;
      background-color: #fff;
      text-align: left;
      padding: 40px;
      border-radius: 10px;
      text-transform: capitalize;
      box-shadow: rgba(17, 12, 46, 0.15) 0px 48px 100px 0px;
}
form h1 {
      text-align: center;
}
label {
      color: #aaa;
      display: inline-block;
      margin: 25px 0 15px;
      font-size: 0.7em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
}
input,
select {
      display: block;
      padding: 10px 6px;
      width: 100%;
      box-sizing: border-box;
      border: none;
      border-bottom: 1px solid #ddd;
      color: #555;
}
input[type="checkbox"] {
      display: inline-block;
      width: 16px;
      margin: 0 10px 0 0;
      position: relative;
      top: 5px;
      widows: 25px;
      height: 25px;
}
.show-information {
      text-align: center;
      margin-top: 50px;
}
.pill {
      display: inline-block;
      margin: 20px 10px 0 0;
      padding: 6px 12px;
      background-color: #eee;
      border-radius: 20px;
      font-size: 12px;
      letter-spacing: 1px;
      font-weight: bold;
      color: #777;
}
.deleteBtn {
      padding: 5px 8px;
      background-color: red;
      color: #fff;
      font-weight: bold;
      border-radius: 15px;
      margin: 5px 0 5px 5px;
      cursor: pointer;
}
.show-skills {
      padding: 0 15px;
}
.submit {
      text-align: center;
}
.submit button {
      background-color: #0b6dff;
      color: #fff;
      border-radius: 5px;
      border: 0;
      padding: 10px 20px;
      margin-top: 20px;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.3s;
}
.submit button:hover {
      transition: 0.3s;
      transform: scale(1.2);
}
.error {
      color: #ff0052;
      font-size: 0.8rem;
      font-weight: bold;
      margin-top: 10px;
}
</style>
