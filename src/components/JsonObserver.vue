<script lang="ts">
export default {
  name: "JsonObserver",
  props: {
    data: Object,
    showLocation: Boolean,
    showAdress: Boolean,
    showHide: Function,
  },
  data(props) {
    return {
      firstname: props.data.firstname,
      lastname: props.data.lastname,
      main: props.data.location.address.main,
      extra: props.data.location.address.main,
      zipcode: props.data.location.zipcode,
      fruit: "XXXX",
      avantDernier: props.data.null,
      dernier: props.data.undefined,
    };
  },
};
</script>

<template>
  <div class="item">
    <ul>
      <li>
        firstname : <input v-model="firstname" :placeholder="data.firstname" />
      </li>
      <li>
        lastname : <input v-model="lastname" :placeholder="data.lastname" />
      </li>
      <li>
        location : <span v-if="showLocation" @click="showHide('showLocation', showLocation)">( - )</span><span v-else
          @click="showHide('showLocation', showLocation)">( + )</span>
        <ul v-if="showLocation">
          <li>adress : <span v-if="showAdress" @click="showHide('showAdress', showAdress)">( - )</span><span v-else
              @click="showHide('showAdress', showAdress)">( + )</span>
            <ul v-if="showAdress">
              <li>main : <input v-model="main" :placeholder="data.location.address.main" /></li>
              <li>extra : <input v-model="extra" :placeholder="data.location.address.extra" />
              </li>
            </ul>
          </li>
          <li>zipcode : <input v-model="zipcode" :placeholder="data.location.zipcode" /></li>
        </ul>
      </li>
      <li>
        cart : <select name="cart" id="cart-select" v-model="fruit">
          <option value="">--Choisissez un fruit--</option>
          <option v-for="item in data.cart" :key="item" :value="item">{{ item }}</option>
        </select>
      </li>
      <li>null : <input v-model="avantDernier" :placeholder="data.null" /></li>
      <li>undefined : <input v-model="dernier" :placeholder="data.undefined" /></li>
    </ul>
  </div>
  <div>
    <h2>Mon nom est {{ firstname }}, {{ lastname }}</h2>
    <p>J'habite a {{ main }}, {{ extra }}, {{ zipcode }}</p>
    <h2>J'aime les {{ fruit }}</h2>
    <h2>Mais aussi {{ avantDernier }}, {{ dernier }}</h2>
  </div>
</template>

<style scoped>
.item {
  margin-top: 2rem;
  display: flex;
}

.details {
  flex: 1;
  margin-left: 1rem;
}

i {
  display: flex;
  place-items: center;
  place-content: center;
  width: 32px;
  height: 32px;

  color: var(--color-text);
}

h3 {
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 0.4rem;
  color: var(--color-heading);
}

@media (min-width: 1024px) {
  .item {
    margin-top: 0;
    padding: 0.4rem 0 1rem calc(var(--section-gap) / 2);
  }

  i {
    top: calc(50% - 25px);
    left: -26px;
    position: absolute;
    border: 1px solid var(--color-border);
    background: var(--color-background);
    border-radius: 8px;
    width: 50px;
    height: 50px;
  }

  .item:before {
    content: ' ';
    border-left: 1px solid var(--color-border);
    position: absolute;
    left: 0;
    bottom: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:after {
    content: ' ';
    border-left: 1px solid var(--color-border);
    position: absolute;
    left: 0;
    top: calc(50% + 25px);
    height: calc(50% - 25px);
  }

  .item:first-of-type:before {
    display: none;
  }

  .item:last-of-type:after {
    display: none;
  }
}
</style>
