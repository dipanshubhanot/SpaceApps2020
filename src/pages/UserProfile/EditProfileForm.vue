<template>
  <div>
    <card>
      <h3 slot="header" class="card-title">Ask for Support</h3>
      <form>
        <div class="row">
          <div class="col-md-7">
            <base-input
              type="text"
              label="Name"
              :disabled="false"
              placeholder="Fire Buster"
            >
            </base-input>
          </div>
          <div class="col-md-4">
            <base-input
              type="text"
              label="Contact Number"
              placeholder="+61 4xx xxx xxx"
            >
            </base-input>
          </div>
        </div>

        <div class="text-center">
          <button
            type="submit"
            class="btn btn-danger btn-fill float-right"
            @click.prevent="updateProfile"
          >
            Send Request for a Volunteer
          </button>
        </div>
        <div class="clearfix"></div>
      </form>
    </card>
    <card>
      <h3 slot="header" class="card-title">Offer to Volunteer</h3>
      <form>
        <div class="row">
          <div class="col-md-7">
            <base-input
              type="text"
              label="Name"
              :disabled="false"
              placeholder="Fire Buster"
            >
            </base-input>
          </div>
          <div class="col-md-4">
            <base-input
              type="text"
              label="Contact Number"
              placeholder="+61 4xx xxx xxx"
            >
            </base-input>
          </div>
        </div>

        <div class="text-center">
          <button
            type="submit"
            class="btn btn-warning btn-fill float-right"
            @click.prevent="updateProfile"
          >
            Volunteer as Tribute
          </button>
        </div>
        <div class="clearfix"></div>
      </form>
    </card>
  </div>
</template>
<script>
import Card from "src/components/Cards/Card.vue";

export default {
  components: {
    Card,
  },
  data() {
    return {
      user: {
        company: "Light dashboard",
        username: "michael23",
        email: "",
        firstName: "Mike",
        lastName: "Andrew",
        address: "Melbourne, Australia",
        city: "melbourne",
        country: "Australia",
        postalCode: "",
        aboutMe: `Lamborghini Mercy, Your chick she so thirsty, I'm in that two seat Lambo.`,
      },
    };
  },
  methods: {
    updateProfile() {
      alert("Your data: " + JSON.stringify(this.user));
    },
  },
};
</script>
<style>
</style>
