<template>
  <div>
    <div class="gray al-c" v-if="$loadingRouteData">Loading data...</div>
    <div class="gray al-c" v-if="!$loadingRouteData">message #{{message.id}}: {{message.text}}</div>
  </div>
</template>

<script>
import messagesService from '../../services/messages'
module.exports = {
  route: {
    // data hook
    // Useful for doing async data loading.
    // sets the component's "$loading" property to
    // true when called, and sets it to false when resolved.
    // two options:
    // 1. return a promise
    // 2. explicitly call transition.next() or
    //     transition.abort(reason)
    data ({ to, next }) {
      // "this" is available
      var params = {
        id: to.params.messageId
      }
      console.log('to', to)
      console.log('next', next)
      // callback based
      messagesService.get(params, (err, message) => {
        if (err) {
          // handle error, e.g. display a warning
        } else {
          next({
            message: message
          })
        }
      })

      // or promise based (with ES6 sugar)
      // return messagesService
      //   .get(params)
      //   .then(message => ({ message }))
    }
  },

  // default state
  data () {
    return {
      message: {}
    }
  }
}
</script>
