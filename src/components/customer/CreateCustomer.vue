<template lang="">
  <div>
    <div class="col-md-12 form-wrapper">
      <h2>Create Customer</h2>
      <form id="create-post-form" @submit.prevent="createCustomer">
        <div class="form-group col-md-12">
          <input
            type="text"
            id="first_name"
            v-model="first_name"
            name="title"
            class="form-control"
            placeholder="Enter first name"
          />
        </div>
        <div class="form-group col-md-12">
          <input
            type="text"
            id="last_name"
            v-model="last_name"
            name="title"
            class="form-control"
            placeholder="Enter last name"
          />
        </div>
        <div class="form-group col-md-12">
          <input
            type="text"
            id="email"
            v-model="email"
            name="title"
            class="form-control"
            placeholder="Enter email"
          />
        </div>
        <div class="form-group col-md-12">
          <input
            type="text"
            id="phone"
            v-model="phone"
            name="title"
            class="form-control"
            placeholder="Enter phone number"
          />
        </div>
        <div class="form-group col-md-12">
          <input
            type="text"
            id="address"
            v-model="address"
            name="title"
            class="form-control"
            placeholder="Enter address"
          />
        </div>
        <div class="form-group col-md-12">
          <input
            type="text"
            id="description"
            v-model="description"
            name="description"
            class="form-control"
            placeholder="Enter description"
          />
        </div>
        <div class="form-group col-md-4 pull-right">
          <button class="btn btn-success" type="submit">Create Customer</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
import { server } from "../../helper";
import router from "../../router/index";

export default {
    data() {
    return {
      first_name: "",
      last_name: "",
      email: "",
      phone: "",
      address: "",
      description: "",
    };
  },
  methods: {
    createCustomer() {
      let createData = {
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        phone: this.phone,
        address: this.address,
        description: this.description,
      };
      this.__submitToServer(createData);
    },
    __submitToServer(data) {
      axios
        .post(`${server.baseUrl}/customer/create`, data)
        .then(router.push({ name: "home" }));
    },
  },
};
</script>
<style lang=""></style>
