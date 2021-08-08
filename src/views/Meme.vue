<template>
  <div class="container-md">
    <div class="col col-md-5 mx-auto">
      <h2>
        Drakeposting
        <p>
          <small class="text-muted">
            <i>DRKP</i>
          </small>
        </p>
      </h2>

      <div class="price mb-4">
        <div class="h1 fw-normal" v-if="purchased">$502.50</div>
        <menu class="p-0">
          <button class="btn btn-outline-primary" @click="openBuyDialog">Purchase</button>
        </menu>
        <div class="d-flex">
          <div class="text-success">▲$2.50(2%)</div>
          <div class="text-muted fw-bold ms-2">Today</div>
        </div>
      </div>
      <div class="graph mb-2">
        <MemeTrendChart/>
        </div>
      <ul class="nav nav-pills">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">1D</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">1W</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">1M</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">3M</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">1Y</a>
        </li>
      </ul>

      <h3 class="mt-5">About</h3>
      <hr>
      <img class="img-fluid" src="https://en.meming.world/images/en/0/07/Drakeposting.jpg" alt="">

      <dialog ref="dialog">
        <form method="dialog">
          <p><label>Favorite animal:
            <select>
              <option></option>
              <option>Brine shrimp</option>
              <option>Red panda</option>
              <option>Spider monkey</option>
            </select>
          </label></p>
          <menu>
            <button value="cancel">Cancel</button>
            <button id="confirmBtn" value="default">Confirm</button>
          </menu>
        </form>
      </dialog>

    </div>
  </div>
</template>

<script>
import MemeTrendChart from '../components/MemeTrendChart.vue'

export default {
  name: 'MemeView',
  components: { MemeTrendChart },
  data: () => ({
    puchasePrice: null,
    purchased: false
  }),
  methods: {
    openBuyDialog () {
      this.$refs.dialog.showModal()
    }
  }
}
</script>
