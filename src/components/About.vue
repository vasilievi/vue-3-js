<template>
  <div class="card m-3 shadow p-3">
    <h1 class="title" :style="titleStyle">{{ title }}</h1>
    <form class="row g-3 needs-validation" novalidate>
      <div class="col-md-4">
        <label for="validationCustom01" class="form-label">First name</label>
        <input
          id="firstname"
          type="text"
          class="form-control"
          value="Mark"
          required
        />
        <div class="valid-feedback">Looks good!</div>
      </div>
      <div class="col-md-4">
        <label for="validationCustom02" class="form-label">Last name</label>
        <input
          v-model="lastname"
          id="lastname"
          type="text"
          class="form-control"
          required
        />
        <div class="valid-feedback">Looks good!</div>
      </div>
      <div class="col-md-4">
        <label for="validationCustomUsername" class="form-label"
          >Username</label
        >
        <div class="input-group has-validation">
          <span class="input-group-text" id="inputGroupPrepend">@</span>
          <input
            type="text"
            class="form-control"
            id="validationCustomUsername"
            aria-describedby="inputGroupPrepend"
            required
          />
          <div class="invalid-feedback">Please choose a username.</div>
        </div>
      </div>
      <div class="col-md-6">
        <label for="validationCustom03" class="form-label">City</label>
        <input
          type="text"
          class="form-control"
          id="validationCustom03"
          required
        />
        <div class="invalid-feedback">Please provide a valid city.</div>
      </div>
      <div class="col-md-3">
        <label for="validationCustom04" class="form-label">State</label>
        <select class="form-select" id="validationCustom04" required>
          <option selected disabled value="">Choose...</option>
          <option>...</option>
        </select>
        <div class="invalid-feedback">Please select a valid state.</div>
      </div>
      <div class="col-md-3">
        <label for="validationCustom05" class="form-label">Zip</label>
        <input
          type="text"
          class="form-control"
          id="validationCustom05"
          required
        />
        <div class="invalid-feedback">Please provide a valid zip.</div>
      </div>
      <div class="col-12">
        <div class="form-check">
          <input
            class="form-check-input"
            type="checkbox"
            value=""
            id="invalidCheck"
            required
          />
          <label class="form-check-label" for="invalidCheck">
            Agree to terms and conditions
          </label>
          <div class="invalid-feedback">You must agree before submitting.</div>
        </div>
      </div>
      <div class="col-12">
        <button
          @click="submit"
          class="btn btn-primary"
          type="button"
          id="buttonSubmit"
        >
          Submit form
        </button>
      </div>
    </form>
  </div>

  <div class="card m-3 shadow p-3">
    <h1 id="title">Names</h1>
    <div v-for="(item, index) in names" :key="index">
      <div class="col-md-4">
        <label for="validationCustom02" class="form-label">{{'Фамилия' + item.lastname }}</label>
        <input
          v-model="item.lastname"
          id="lastname"
          type="text"
          class="form-control"
          required
        />
        <div class="valid-feedback">Looks good!</div>
      </div>
    </div>
  </div>

  <pre>
    {{ names }}
  </pre>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup() {
    const title = ref("Marry Chistmas!!!");
    const titleStyle = ref();
    const lastname = ref("Петров");
    const names = ref([]);

    const submit = () => {
      title.value = "Happy new year!!!";
      titleStyle.value = "color:blue";
      names.value.push({
        lastname: lastname.value
        });
    };

    // v-on = @
    // v-bind = :
    // v-model
    // v-for
    // ---
    // onMount
    // props
    // watch
    // computed

    return {
      title,
      titleStyle,
      submit,
      lastname,
      names,
    };
  },
};
</script>

<style>
.title {
  color: red;
}
</style>