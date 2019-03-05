<template>
  <div>
    <img :src="mediapath" :alt="coinname + '-logo'">
  </div>
</template>

<script>
export default {
  name: "IconCrypto",
  props: {
    coinname: {
      type: String,
      required: true
    },
    color: {
      type: String,
      default: "color",
      validator: function(value) {
        return ["color", "black", "white"].indexOf(value) !== -1;
      }
    },
    format: {
      type: String,
      default: "32",
      validator: function(value) {
        return ["32", "128", "svg"].indexOf(value) !== -1;
      }
    }
  },
  data() {
    return {
      ext: ".png"
    };
  },
  created() {
    this.coinname.toLowerCase();
    if (this.format === "svg") {
      this.ext = ".svg";
    }
  },
  computed: {
    mediapath() {
      try {
        return require(`../../node_modules/cryptocurrency-icons/svg/color/${this.coinname.toLowerCase()}.svg`);
      } catch (e) {
        return require(`../../node_modules/cryptocurrency-icons/svg/color/generic.svg`);
      }
      // try {
        // return require(`~/node_modules/cryptocurrency-icons/svg/color/${this.coinname.toLowerCase()}.svg`);
      // } catch (e) {
        // return require(`~/node_modules/cryptocurrency-icons/svg/color/generic.svg`);
      // }

      // try {
      //   return require(`@/assets/cryptocurrency-icons/${this.format}/${
      //     this.color
      //   }/${this.coinname.toLowerCase() + this.ext}`);
      // } catch (e) {
      //   return require(`@/assets/cryptocurrency-icons/${this.format}/${
      //     this.color
      //   }/generic${this.ext}`);
      // }
    }
  }
};
</script>