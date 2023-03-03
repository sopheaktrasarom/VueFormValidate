<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import { useField, useForm } from "vee-validate";
import type { Ref } from "vue";
import { ref, reactive } from "vue";
interface Text {
  firstname: string;
  lastname: string;
}

const count = ref(0);
const text: Text = reactive({ firstname: "", lastname: "" });
const err = reactive<any>({});
const valid = reactive<any>({});
const info = ref({ name: "Jame", msg: "Hello" });
function addCount() {
  count.value++;
}
function validate() {
  let { firstname, lastname } = text;

  if (firstname.length === 0) {
    err.firstname = "firstname is required";
    valid.firstname = true;
  } else {
    err.firstname = "";
    valid.firstname = false;
  }

  if (lastname.length === 0) {
    err.lastname = "lastname is required";
    valid.lastname = true;
  } else {
    err.lastname = "";
    valid.lastname = false;
  }
}
</script>

<template>
  <form @submit.prevent="validate">
    <div class="fiedeName firstName">
      <input
        type="text"
        v-model="text.firstname"
        class="border border-sky-500"
        placeholder="firstName"
      />
      <Transition>
        <p class="text-red-600" v-if="valid.firstname">
          {{ err.firstname }}
        </p>
      </Transition>
    </div>
    <div class="fiedeName lastName">
      <input
        type="text"
        v-model="text.lastname"
        class="border border-sky-500"
        placeholder="lastName"
      />
      <Transition>
        <p class="text-red-600" v-if="valid.lastname">
          {{ err.lastname }}
        </p>

        
        
      </Transition>
    </div>

    <button>sign in</button>
  </form>
</template>
<style scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
