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
            @click="notifyVue('top', 'center')"
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
            @click="notifyVue('top', 'center')"
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
      type: ["", "info", "success", "warning", "danger"],
      notifications: {
        topCenter: false,
      },
    };
  },
  methods: {
    notifyVue(verticalAlign, horizontalAlign) {
      const color = Math.floor(Math.random() * 4 + 1);
      this.$notifications.notify({
        message: `Your request has been recieved. Kindly Monitor the Section on the Right.`,
        icon: "nc-icon nc-notes",
        horizontalAlign: horizontalAlign,
        verticalAlign: verticalAlign,
        type: this.type[color],
      });
    },
  },
};
</script>
<style>
</style>
