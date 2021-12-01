<template>
  <div class="form-wrapper">
    <transition name="message">
      <span v-show="success" class="success">Form successfully submitted.</span>
    </transition>
    <div class="form">
      <div class="input-container">
        <p>
          <input
            type="text"
            placeholder="Your sweet name"
            v-model="state.name"
          />
          <span v-if="v$.name.$error">
            {{ v$.name.required.$message }}
          </span>
        </p>
        <p>
          <input
            type="text"
            placeholder="Your mail address"
            v-model="state.contact.email"
          />
          <span v-if="v$.contact.email.$error">
            {{ v$.contact.email.email.$message }}
          </span>
        </p>
        <p>
          <input
            type="text"
            placeholder="About your message"
            v-model="state.message"
          />
          <span v-if="v$.message.$error">
            {{ v$.message.minLength.$message }}
          </span>
        </p>
      </div>
      <div class="button-container">
        <button @click="submitForm">
          Send<i class="fas fa-arrow-right"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, computed, ref } from "vue";
import useVuelidate from "@vuelidate/core";
import { required, email, minLength } from "@vuelidate/validators";
export default {
  setup() {
    const success = ref(false);
    const state = reactive({
      name: "",
      message: "",
      contact: {
        email: "",
      },
    });
    const rules = computed(() => {
      return {
        name: { required },
        message: { required, minLength: minLength(20) },
        contact: {
          email: { required, email },
        },
      };
    });

    const v$ = useVuelidate(rules, state);

    return { state, v$, success };
  },

  methods: {
    submitForm() {
      this.v$.$validate();
      if (!this.v$.$error) {
        this.success = true;
        setTimeout(() => {
          this.success = false;
        }, 3000);
      } else {
        return;
      }
      this.state = {
        name: "",
        message: "",
        contact: {
          email: "",
        },
      };

      //reset validation flags
      this.v$.$reset();
    },
  },
};
</script>

<style lang="scss">
.form-wrapper {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 40px;

  .message-enter-active {
    transition: all 0.4s ease-out;
  }

  .message-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
  }

  .message-enter-from,
  .message-leave-to {
    transform: translateY(-100%);
    opacity: 0;
  }

  .success {
    position: absolute;
    top: -35px;
    display: flex;
    align-items: center;
    height: 30px;
    background-color: green;
    color: white;
    padding: 10px;
  }
}
.form {
  display: flex;
  justify-content: center;
  max-width: 50%;
  @media (max-width: 750px) {
    max-width: 100%;
  }
  margin: 0 auto;

  .input-container {
    display: flex;
    flex-shrink: 2;
    justify-content: space-between;
    flex-wrap: wrap;

    p {
      display: flex;
      flex-direction: column;
      min-height: 100px;
      margin-bottom: 10px;
      @media (max-width: 450px) {
        font-size: 14px;
      }
      input {
        &:focus {
          padding-bottom: 5px;
          border-bottom: solid 2px #a9ffa9;
        }
      }

      span {
        color: red;
        font-size: 12px;
      }
    }
  }
  .button-container {
    display: flex;
    align-items: flex-end;
    width: 100%;
    max-width: 100px;
    button {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100px;
      width: 100%;
      color: #fff;
      margin-top: 100px;
      background-color: green;

      &:hover {
        opacity: 0.8;
      }

      @media (max-width: 450px) {
        margin-top: 50px;
        height: 100px;
      }

      i {
        margin-top: 10px;
      }
    }
  }
}
</style>
