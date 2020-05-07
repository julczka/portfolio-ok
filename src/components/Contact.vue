<template>
  <form class="contact-form" @submit.prevent="sendEmail">
    <div class="row">
      <label>Name</label>
      <input
        class="form-style"
        type="text"
        name="from_name"
        placeholder="Rick Sanchez"
      />
    </div>
    <div class="row">
      <label>Email</label>
      <input
        class="form-style"
        type="email"
        name="reply_to"
        placeholder="hireme@pleasedo.com"
      />
    </div>
    <div class="row">
      <label>Message</label>
      <textarea
        class="form-style"
        rows="8"
        name="message_html"
        placeholder="Hello!"
      ></textarea>
    </div>
    <div class="row">
      <input class="button" type="reset" value="Clear" />
      <input class="button" type="submit" value="Send" />
    </div>
  </form>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  methods: {
    sendEmail: (e) => {
      emailjs
        .sendForm(
          'gmail',
          'template_9o9Wvvjt',
          e.target,
          'user_GPJS6w6VSmdqBtVMHlT8g'
        )
        .then(
          (result) => {
            console.log('SUCCESS!', result.status, result.text);
          },
          (error) => {
            console.log('FAILED...', error);
          }
        );
    },
  },
};
</script>

<style lang="scss" scoped>
.contact-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 60vw;
  height: 60vh;

  .form-style {
    border: 1px solid var(--text-primary);
    background-color: var(--bg--primary);
    color: var(--text-primary);
    font-size: 1.5rem;
    font-family: $futura;
    padding: 0.3em;
    resize: none;
  }

  .form-style::placeholder {
    color: var(--text-secondary);
    opacity: 0.5;
    font-weight: 100;
    font-style: italic;
  }

  label {
    font-size: 1.5rem;
    font-family: $futura;
    color: var(--text-secondary);
  }

  textarea {
    height: 6em;
  }

  .button {
    margin-top: 1em;
  }
}

.row {
  display: flex;
  width: 50%;
  align-items: center;
  justify-content: space-between;
  margin: 1em 0;
}
</style>
