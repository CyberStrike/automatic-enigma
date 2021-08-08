<template>
  <div class="random">
    <trend-chart :datasets="datasets" :grid="grid" :labels="labels" :min="0" class="random-chart"></trend-chart>
    <div id="pop" role="tooltip" ref="tooltip" class="tooltip" :class="{'is-active': tooltipData}">
      <div class="tooltip-container" v-if="tooltipData">
        <strong>{{labels.xLabels[tooltipData.index]}}</strong>
      </div>
    </div>
  </div>
</template>

<script>
import TrendChart from 'vue-trend-chart'

export default {
  name: 'MemeTrendChart',
  components: { TrendChart },
  data: () => ({
    datasets: [
      {
        data: [70, 100, 400, 180, 100, 300, 500],
        smooth: true,
        showPoints: true,
        fill: true,
        className: 'curve1'
      }
    ],
    grid: {
      verticalLines: true,
      horizontalLines: true
    },
    labels: {
      xLabels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      yLabels: 5,
      yLabelsTextFormatter: val => Math.round(val * 100) / 100
    },
    tooltipData: null,
    popper: null,
    popperIsActive: false
  })
}
</script>

<style lang="scss">
.random {
  width: 100%;
  .vtc {
    height: 250px;
    font-size: 12px;
    @media (min-width: 699px) {
      height: 320px;
    }
  }
  .labels {
    stroke: rgba(0, 0, 0, 0.05);
  }
  .active-line {
    stroke: rgba(0, 0, 0, 0.2);
  }
  .point {
    stroke-width: 2;
    transition: stroke-width 0.2s;
  }
  .point.is-active {
    stroke-width: 5;
  }
  .curve1 {
    .stroke {
      stroke: #fbac91;
      stroke-width: 2;
    }
    .fill {
      fill: #fbac91;
      opacity: 0.05;
    }
    .point {
      fill: #fbac91;
      stroke: #fbac91;
    }
  }
  .curve2 {
    .stroke {
      stroke: #fbe1b6;
      stroke-width: 2;
    }
    .point {
      fill: #fbe1b6;
      stroke: #fbe1b6;
    }
  }
  .curve3 {
    .stroke {
      stroke: #7fdfd4;
      stroke-width: 2;
    }
    .point {
      fill: #7fdfd4;
      stroke: #7fdfd4;
    }
  }

  .tooltip {
    &:not(.is-active) {
      display: none;
    }
    padding: 10px;
    background: #fff;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
    pointer-events: none;
    &-data {
      display: flex;
      &-item {
        display: flex;
        align-items: center;
        &:not(:first-child) {
          margin-left: 20px;
        }
        &:before {
          content: "";
          display: block;
          width: 15px;
          height: 15px;
          margin-right: 5px;
        }
        &--1:before {
          background: #fbac91;
        }
        &--2:before {
          background: #fbe1b6;
        }
        &--3:before {
          background: #7fdfd4;
        }
      }
    }
  }
}
</style>
