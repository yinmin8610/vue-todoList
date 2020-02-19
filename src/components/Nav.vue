<template>
  <div class="Nav">
    <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
      <li class="nav-item">
        <a
          class="nav-link"
          href="#All"
          :class="{'active':selected ==='All'}"
          @click="selected = 'All'"
        >All</a>
      </li>
      <li class="nav-item">
        <a
          class="nav-link"
          href="#Doing"
          :class="{'active': selected ==='Doing'}"
          @click="selected = 'Doing'"
        >Doing</a>
      </li>
      <li class="nav-item">
        <a
          class="nav-link"
          href="#Done"
          :class="{'active':selected ==='Done'}"
          @click="selected = 'Done'"
        >Done</a>
      </li>
    </ul>

    <div class="tab-content">
      <div v-if="selected === 'All'">
        <!-- {{ status }} -->
      </div>
      <div v-else-if="selected === 'Doing'">
        <!-- {{ doing }} -->
      </div>
      <div v-else-if="selected === 'Done'">
        <!-- {{ done }} -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav',
  props: ['status'],
  data: function () {
    return {
      selected: 'All'
    }
  }
}
</script>
