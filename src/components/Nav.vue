<template>
  <div class="Nav">
    <ul class="nav nav-pills mb-3" id="pills-tab" role="tablist">
      <li class="nav-item">
        <a
          class="nav-link"
          href="#Todo"
          :class="{'active':selected ==='Todo'}"
          @click="selected = 'Todo'"
        >Todo</a>
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
      <div v-if="selected === 'Todo'">
        1
      </div>
      <div v-else-if="selected === 'Doing'">
        2
      </div>
      <div v-else-if="selected === 'Done'">
        3
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav',
  data: function () {
    return {
      selected: 'Todo'

    }
  }
}
</script>
