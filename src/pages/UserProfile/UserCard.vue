<template>
  <card class="card-user" :style="{ backgroundImage: 'url(https://images.unsplash.com/photo-1548424190-a2c9ac440def?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2134&q=80)', backgroundSize : 'cover' }">
    <img
      slot="image"
      src="https://images.unsplash.com/photo-1548424190-a2c9ac440def?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2134&q=80"
      alt="..."
    />
    <div :style="{backgroundColor: 'rgba(0,0,0,0.7)'}">
      <div class="author">
        <a href="#">
          <img
            class="avatar"
            src="https://www.flaticon.com/svg/static/icons/svg/855/855093.svg"
            alt="..."
          />
          <h3 class="title">We are all in this, together!</h3>
          <h2 class="title">
            <small>Contact</small><br /><br />
            Vaishu
          </h2>
        </a>

      <h3 class ="title" style="color: #fff">
        <small>Call them at</small> <br />
        +61 4xx xxx xxx
      </h3>
      </div>
      <div slot="footer" class="text-center d-flex justify-content-center">
        <img slot="image" src="img/logo-white.png" width="300px" />
      </div>
    </div>
  </card>
</template>
<script>
import Card from "src/components/Cards/Card.vue";
export default {
  components: {
    Card,
  },
  data() {
    return {
      cardStyle: {
        "background-image":
          "https://images.unsplash.com/photo-1548424190-a2c9ac440def?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2134&q=80",
      },
      details: [
        {
          title: "12",
          subTitle: "Files",
        },
        {
          title: "2GB",
          subTitle: "Used",
        },
        {
          title: "24,6$",
          subTitle: "Spent",
        },
      ],
    };
  },
  methods: {
    getClasses(index) {
      var remainder = index % 3;
      if (remainder === 0) {
        return "col-md-3 col-md-offset-1";
      } else if (remainder === 2) {
        return "col-md-4";
      } else {
        return "col-md-3";
      }
    },
  },
};
</script>
<style>
</style>
