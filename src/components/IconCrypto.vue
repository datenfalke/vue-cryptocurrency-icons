<template>
  <img :src="mediapath" :alt="coinname + '-logo'" @error="imageLoadError">
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
    if (this.format === "svg") {
      this.ext = ".svg";
    }
  },
  methods: {
    imageLoadError (event) {
      event.target.src = 'https://cdn.jsdelivr.net/npm/cryptocurrency-icons@0.10.1/svg/black/generic.svg';
    }
  },
  computed: {
    mediapath() {
        return `https://cdn.jsdelivr.net/npm/cryptocurrency-icons@0.11.0/${this.format}/${
           this.color
         }/${this.coinname.toLowerCase() + this.ext}`;
    }
  }
};
</script>