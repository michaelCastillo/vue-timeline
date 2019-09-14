<template>
  <div class="hello">
    <div v-for="(value,index) in data" v-bind:key="value.date + index" class="valueData">
      <div v-if="left[index]" class="dateLeft date">
        <div class="header">
          <span class="dateSp">{{value.date}}</span>
          <span class="titleSp">{{value.title}}</span>
        </div>
        <div v-if="left[index]" class="bottomLine" />
      </div>
      <div v-else class="description description-left">
        <slot>
          <p>{{value.description}}</p>
        </slot>
      </div>
      <LineAndDot :selected="index === onView" @send-message="inView" v-bind:index="index" />
      <div v-if="!left[index]" class="dateRight date">
        <div class="header">
          <span class="dateSp">{{value.date}}</span>
          <span class="titleSp">{{value.title}}</span>
        </div>
        <div v-if="!left[index]" class="bottomLine" />
      </div>
      <div v-else class="description description-right">
        <slot>
          <p>{{value.description}}</p>
        </slot>
      </div>
    </div>
  </div>
</template>

<script>
import LineAndDot from "./LineAndDot.vue";
export default {
  name: "Timeline",
  components: { LineAndDot },
  props: {
    data: Array
  },
  data: function() {
    return {
      onView: 0,
      left: this.data.map((value, index) => index % 2 == 0)
    };
  },
  mounted() {},
  methods: {
    inView: function(event) {
      this.onView = event;
    }
  }
};
</script>

<style scoped>
.valueData {
  display: flex;
  justify-content: center;
}
.dateSp {
  font-size: 18px;
}
.titleSp {
  font-size: 32px;
}
.header {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
.date {
  display: flex;
  flex-direction: column;
  font-size: 25px;
  font-weight: 750;
  text-align: center;
  margin: auto 0px;
  width: 100%;
}
.description {
  font-size: 25px;
  font-weight: 750;
  margin: auto 0px;
  width: 100%;
}
.description-left {
  text-align: end;
}
.description-right {
  text-align: start;
}
.bottomLine {
  background: linear-gradient(
    90deg,
    rgb(174, 238, 238) 0%,
    rgba(233, 231, 148, 1) 100%
  );
  text-align: center;
  width: 36%;
  height: 2px;
}
.dateRight {
  align-items: flex-start;
}
.dateLeft {
  align-items: flex-end;
}
</style>
