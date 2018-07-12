<template>
    <div class="rating">
    <ul class="list">
      <li v-for="star in maxStars" @click="rate(star)" :class="{ 'active': star <= stars }" class="star">
        <icon scale="2" :name="star <= stars ? 'star' : 'star-o'"/>
      </li>
    </ul>
    <!-- <span>{{ counter }}</span> -->
    <span v-if="hasCounter">{{ stars }} of {{ maxStars }}</span>
  </div>
</template>
<script>
import 'vue-awesome/icons/star'
import 'vue-awesome/icons/star-o'
import Icon from 'vue-awesome/components/Icon'
export default {
  name: 'rate',
  components: { Icon },
  data () {
    return {
      stars: this.grade,
      // maxStars: 5,
      // hasCounter: true
    }
},
   props: {
    grade: {
      type: Number,
      required: true
    },
    maxStars: {
      type: Number,
      default: 5
    },
    hasCounter: {
      type: Boolean,
      default: true
    }
  },
  computed: {
    counter() {
      return `${this.stars} of ${this.maxStars}`
    }
  },
  methods: {
    rate(star) {
      this.stars = star
    }
  }
}
</script>
<style scoped>
  .rating {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-size: 14px;
    color: #a7a8a8;
  }
  .list {
    margin: 0 0 5px 0;
    padding: 0;
    list-style-type: none;
  }
  .list:hover .star {
    color: #f3d23e;
  }
  .star {
    display: inline-block;
    cursor: pointer;
  }
  .star:hover ~ .star:not(.active) {
    color: inherit;
  }
  .active {
    color: #f3d23e;
  }
</style>