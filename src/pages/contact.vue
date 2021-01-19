<template>
  <Layout>
    <div class="container">
      <div class="contact-header">
        <h1 class="contact-title">Say hi!</h1>
        <p>
          Leave me a note with any questions you might have, I'll get back to you as soon
          as possible.
        </p>
      </div>
      <form name="contact" class="contact-form">
        <div class="sender-info">
          <div>
            <label for="name" class="label">Your name</label
            ><input v-model="form.name" type="text" name="name" />
          </div>
          <div>
            <label for="email" class="label">Your email</label
            ><input v-model="form.email" type="email" name="email" />
          </div>
        </div>
        <div class="message">
          <label for="message" class="label">Message</label
          ><textarea v-model="form.message" name="message"></textarea>
        </div>
        <button class="button" @click.prevent="submit">Submit form</button>
      </form>
    </div>
  </Layout>
</template>
<script>
import axios from 'axios'
export default {
  name: "contact",
  data(){
      return {
          form:{
              name:'',
              email:'',
              message:''
          }
      }
  },
  methods:{
      async submit(){
          try {
            const { data } = await axios({
                url:'http://localhost:1337/contacts',
                method:"POST",
                data:this.form
            });
            alert('提交成功');
            this.form = {
              name:'',
              email:'',
              message:''
            }
          } catch (error) {
            alert('提交失败，请稍后重试');
          }
            
      }
  }
};
</script>
<style>
.contact-header {
    padding: 2rem 0 4rem;
}
.contact-title {
    font-size: 4rem;
    margin: 0 0 4rem;
    padding: 0;
}
.sender-info {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 2rem;
}
.sender-info>div {
    flex: 1;
    margin-right: 4rem;
}
input, textarea {
    background: transparent;
    border: 1px solid var(--color-base-1);
    outline: none;
    border-radius: .3rem;
    padding: .8rem 1rem;
    color: inherit;
    font-size: 1rem;
    width: 100%;
}
.label {
    display: block;
    font-weight: 700;
    margin-bottom: .5rem;
}
.button {
    color: var(--color-base);
    background: var(--color-contrast);
    outline: none;
    border: 0;
    font-size: .8rem;
    padding: .8rem 1.6rem;
    border-radius: .3rem;
    margin-top: 2rem;
    cursor: pointer;
    transition: opacity .25s ease;
    font-weight: 500;
    letter-spacing: .035em;
}
</style>
