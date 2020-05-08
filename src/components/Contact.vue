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
    <div class="row--button">
      <input class="button" type="reset" value="Clear" />
      <input class="button" type="submit" value="Send" />
    </div>

    <transition v-on:enter="enter" v-on:leave="leave">
      <div class="modal success" v-if="success" @click="success = false">
        <i class="far fa-smile"></i>
        <h4>Message sent!</h4>
        <p>Click me to close</p>
      </div>
    </transition>

    <div class="modal fail" v-if="fail" @click="fail = false">
      <i class="far fa-frown"></i>
      <h4>Something went wrong...</h4>
      <p>Click me to close</p>
    </div>
  </form>
</template>

<script>
import emailjs from 'emailjs-com';
import gsap from 'gsap';

export default {
  data() {
    return {
      success: false,
      fail: false,
    };
  },

  methods: {
    enter(el, done) {
      gsap.fromTo(
        el,
        { scale: 0 },
        { scale: 1, duration: 0.5, ease: 'back.out(1.7)', onComplete: done }
      );
    },

    leave(el, done) {
      gsap.fromTo(
        el,
        { scale: 1 },
        { scale: 0, duration: 0.5, ease: 'back.in(1.7)', onComplete: done }
      );
    },

    sayHello() {
      console.log('hello');
    },

    sendEmail: function(e) {
      emailjs
        .sendForm(
          'gmail',
          'template_9o9Wvvjt',
          e.target,
          'user_GPJS6w6VSmdqBtVMHlT8g'
        )
        .then(
          (result) => {
            this.success = true;
            console.log('SUCCESS!', result.status, result.text);
          },
          (error) => {
            this.fail = true;
            console.log('FAILED...', error);
          }
        );
    },
  },
};
</script>

<style lang="scss" scoped>
.modal {
  position: absolute;
  background: $rad-gradient;
  width: 25rem;
  height: 25rem;
  border-radius: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  color: var(----text-primary);

  .fa-smile,
  .fa-frown {
    font-size: 6rem;
    color: var(--text-secondary);
  }

  p {
    font-family: $futura;
    font-weight: 100;
    color: var(--text-secondary);
  }
}

.contact-form {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 80vw;
  height: 60vh;
  margin-bottom: 5rem;

  .form-style {
    border: 1px solid var(--text-primary);
    background-color: var(--bg--primary);
    color: var(--text-primary);
    font-size: 1.5rem;
    font-family: $futura;
    padding: 0.3em;
    resize: none;
    width: 70%;
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
  width: 100%;
  align-items: center;
  justify-content: space-between;
  margin: 1em 0;

  &--button {
    align-self: flex-end;
  }
}
</style>
