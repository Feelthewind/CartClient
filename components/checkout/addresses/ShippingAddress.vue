<template>
  <article class="message">
    <div class="message-body">
      <h1 class="title is-5">Ship to</h1>

      <template v-if="selectedAddress">
        {{ selectedAddress.name }}<br>
        {{ selectedAddress.address_1 }}<br>
        {{ selectedAddress.city }}<br>
        {{ selectedAddress.postal_code }}<br>
        {{ selectedAddress.country.name }}<br>
      </template>
    </div>
  </article>
</template>

<script>
export default {
  data() {
    return {
      localAddresses: this.addresses,
      selectedAddress: null
    };
  },

  props: {
    addresses: {
      required: true,
      type: Array
    }
  },

  computed: {
    defaultAddress() {
      return this.localAddresses.find(a => a.default === true);
    }
  },

  methods: {
    switchAddress(address) {
      this.selectedAddress = address;
    }
  },

  created() {
    if (this.addresses.length) {
      this.switchAddress(this.defaultAddress);
    }
  }
};
</script>

