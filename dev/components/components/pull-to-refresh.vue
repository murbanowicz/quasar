<template>
  <quasar-layout>
    <div class="toolbar" slot="header">Pull To Refresh</div>

    <div class="layout-view">
      <quasar-pull-to-refresh :handler="refresher">
        <div class="layout-padding bg-white">
          <p class="caption">
            Pull down to refresh on the content below.
            On desktop it works by dragging the content down.
          </p>

          <p v-for="(item, index) in items" class="caption">
            <span class="label bg-secondary text-white shadow-1">
              {{ items.length - index }}
            </span>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
          </p>
        </div>
      </quasar-pull-to-refresh>
    </div>
  </quasar-layout>
</template>

<script>
import { Toast } from 'quasar'

export default {
  data () {
    return {
      items: [{}, {}, {}, {}, {}, {}]
    }
  },
  methods: {
    refresher (done) {
      setTimeout(() => {
        done()
        this.items.push({})
        Toast.create('Item #' + this.items.length + ' is new.')
      }, 1000)
    }
  }
}
</script>
