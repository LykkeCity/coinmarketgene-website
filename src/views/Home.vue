<template>
  <div class="home">
   <!-- <section class="filter">
      <div class="btn-toolbar justify-content-md-center" role="toolbar">
        <div class="btn-group mr-3" role="group" aria-label="Actions" data-toggle="buttons">
          <label class="btn btn-light btn-lg active">
            <input type="radio" name="actions" value="buy" autocomplete="off" checked> Buy
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="actions" value="sell" autocomplete="off"> Sell
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="actions" value="both" autocomplete="off"> Both
          </label>
        </div>
        <div class="btn-group mr-3" role="group" aria-label="BTC value" data-toggle="buttons">
          <label class="btn btn-light btn-lg active">
            <input type="radio" name="btcvalue" value="0" autocomplete="off" checked> O BTC
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="btcvalue" value="1" autocomplete="off"> 1 BTC
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="btcvalue" value="10" autocomplete="off"> 10 BTC
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="btcvalue" value="100" autocomplete="off"> 100 BTC
          </label>
        </div>
        <div class="btn-group mr-3" role="group" aria-label="Currency" data-toggle="buttons">
          <label class="btn btn-light btn-lg active">
            <input type="radio" name="currency" value="usd" autocomplete="off" checked> USD
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="currency" value="usdt" autocomplete="off"> USDT
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="currency" value="both" autocomplete="off"> Both
          </label>
        </div>
        <div class="btn-group" role="group" aria-label="Time period" data-toggle="buttons">
          <label class="btn btn-light btn-lg active">
            <input type="radio" name="period" value="minute" autocomplete="off" checked> 1 M
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="period" value="hour" autocomplete="off"> 1 H
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="period" value="halfday" autocomplete="off"> 12 H
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="period" value="day" autocomplete="off"> 24 H
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="period" value="week" autocomplete="off"> 1 W
          </label>
          <label class="btn btn-light btn-lg">
            <input type="radio" name="period" value="month" autocomplete="off"> 1 M
          </label>
        </div>
      </div>
    </section>-->

    <section class="content">
      <div class="table-responsive">
        <table class="table table_market">
          <thead>
            <tr>
              <th scope="col">
                <div class="sort_control">
                  Exchange
                  <i class="icon icon--arrow"></i>
                </div>
              </th>
              <th scope="col">
                <div class="sort_control">
                  Volume
                  <i class="icon icon--arrow"></i>
                </div>
              </th>
              <th scope="col">
                <div class="sort_control">
                  Effective price (asset)
                  <i class="icon icon--arrow"></i>
                </div>
              </th>
              <th scope="col">
                <div class="sort_control">
                  Depth
                  <i class="icon icon--arrow"></i>
                </div>
              </th>
              <th scope="col" class="text-right">
                <div class="sort_control">
                  Total cost
                  <i class="icon icon--arrow"></i>
                </div>
              </th>
              <th scope="col" class="text-right">Chart</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in items">
              <td>
                <a href>
                  <div class="exchange_item">
                    <div class="exchange_item__logo">
                      <img :src="item.img" alt="Binance" width="24px">
                    </div>
                    <span class="exchange_item__name">{{item.exchange}}</span>
                  </div>
                </a>
              </td>
              <td>
                <a href="info.html">
                  <span class="_value">{{item.volume}}</span>
                </a>
              </td>
              <td>
                <a href="info.html">
                  <span class="_value">{{item.effectiveprice}}</span>
                </a>
              </td>
              <td>
                <span class="_value">{{item.depth}}</span>
              </td>
              <td class="text-right">
                <span
                  v-bind:class="{ 'badge badge-success':item.totalcost>0, 'badge badge-danger':item.totalcost<0 }"
                >{{item.totalcost}}%</span>
              </td>
              <td class="text-right">
                <div class="chart_preview">
                  <img :src="item.chartimg" alt="chart" class="chart_preview__dummy" width="143px">
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
//import Vue from "vue";
//Vue.use(vueResource);

export default {
  name: "home",

  data() {
    return {
      items: [
        {
          img: "/images/exchange/binance-coin-logo-png-transparent.png",
          exchange: "Binance",
          volume: "$ 833,746,525",
          effectiveprice: "$ 833,746,525",
          depth: "BTC 833,746,525",
          totalcost: "9.91",
          chartimg: "/images/chart.png"
        }
      ]
    };
  },

  created: function() {
    this.getItems();
  },

  methods: {
    getItems: function() {
      this.$http
        .get("https://public-api.lykke.com/api/IsAlive")
        .then(function(response) {
          //  console.log(response);
          //  this.message = response;
        });
    }
  },
  components: {
    HelloWorld
  }
};
</script>
