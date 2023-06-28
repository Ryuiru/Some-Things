<template>
  <div class="main">
    <div class="selectCurrency">
      <label for="base-currency"><h3>Select Base Currency:</h3> </label>
      <select
        id="base-currency"
        v-model="baseCurrency"
        @change="fetchExchangeRates"
      >
        <option
          v-for="currency in currencies"
          :value="currency"
          :key="currency"
        >
          {{ currency }} - {{ getCountryCode(currency).name }}
        </option>
      </select>
    </div>
    <div class="container">
      <ul>
        <li v-for="(rate, currency) in filteredExchangeRates" :key="currency">
          <span
            class="currencyFlag"
            :class="'flag-icon flag-icon-' + getCountryCode(currency).code"
          >
          </span>
          <span class="currencyName">{{ getCountryCode(currency).name }}</span>
          <span class="currencyRate">{{ rate }}</span>
          <span class="currencyCode">{{ currency }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      baseCurrency: 'USD',
      exchangeRates: {},
      currencies: [
        'USD',
        'EUR',
        'JPY',
        'BGN',
        'CZK',
        'DKK',
        'GBP',
        'HUF',
        'PLN',
        'RON',
        'SEK',
        'CHF',
        'ISK',
        'NOK',
        'TRY',
        'AUD',
        'CNY',
      ],
    };
  },
  mounted() {
    this.fetchExchangeRates();
  },
  computed: {
    filteredExchangeRates() {
      const filteredRates = { ...this.exchangeRates };
      delete filteredRates[this.baseCurrency];
      return filteredRates;
    },
  },
  methods: {
    fetchExchangeRates() {
      const symbols =
        'USD,EUR,JPY,BGN,CZK,DKK,GBP,HUF,PLN,RON,SEK,CHF,ISK,NOK,TRY,AUD,CNY';
      const amount = 1;
      const places = 4;
      const requestURL = `https://api.exchangerate.host/latest?base=${this.baseCurrency}&symbols=${symbols}&amount=${amount}&places=${places}`;
      const request = new XMLHttpRequest();
      request.open('GET', requestURL);
      request.responseType = 'json';
      request.send();
      request.onload = () => {
        const response = request.response;
        this.exchangeRates = response.rates;
      };
    },
    getCountryCode(currency) {
      const countryCodeMap = {
        USD: { code: 'us', name: 'United States' },
        EUR: { code: 'eu', name: 'European Union' },
        JPY: { code: 'jp', name: 'Japan' },
        BGN: { code: 'bg', name: 'Bulgaria' },
        CZK: { code: 'cz', name: 'Czech Republic' },
        DKK: { code: 'dk', name: 'Denmark' },
        GBP: { code: 'gb', name: 'United Kingdom' },
        HUF: { code: 'hu', name: 'Hungary' },
        PLN: { code: 'pl', name: 'Poland' },
        RON: { code: 'ro', name: 'Romania' },
        SEK: { code: 'se', name: 'Sweden' },
        CHF: { code: 'ch', name: 'Switzerland' },
        ISK: { code: 'is', name: 'Iceland' },
        NOK: { code: 'no', name: 'Norway' },
        TRY: { code: 'tr', name: 'Turkey' },
        AUD: { code: 'au', name: 'Australia' },
        CNY: { code: 'cn', name: 'China' },
      };

      return countryCodeMap[currency] || { code: 'unknown', name: 'Unknown' };
    },
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  max-width: 100%;
}
body {
  padding: 3rem;
  background-color: rgb(255, 206, 206);
}
@import url('https://fonts.googleapis.com/css2?family=Orbitron&display=swap');
@media screen and (max-width: 768px) {
  body {
    padding: 2rem 0.5rem 0.5rem 0.5rem;
  }
}
</style>
<style scoped>
.main {
  text-align: center;
}
.container {
  width: 50%;
  display: inline-block;
  background-color: rgba(0, 0, 0, 0.897);
  border-radius: 1rem;
  padding: 1rem;
  transition: width 0.5s;
}
.selectCurrency {
  margin-bottom: 1rem;
  font-family: 'Orbitron', sans-serif;
}
li {
  list-style: none;
  text-align: left;
  border: 1px solid rgb(255, 0, 0);
  padding: 0.5rem;
  color: limegreen;
  font-size: 1.2rem;
  transition: padding 0.5s, font-size 0.5s;
}
.currencyFlag {
  float: left;
  margin-right: 1rem;
}

.currencyDetails {
  margin-right: 10px;
}

.currencyName {
  font-weight: bold;
  text-align: left;
  margin-right: 1rem;
  color: white;
  display: inline-block;
  transition: font-size 0.5s;
}

.currencyCode {
  font-size: 1rem;
  color: white;
  text-align: left;
  font-style: bold;
  float: right;
  /* width: 50px; */
}

.currencyRate {
  float: right;
  font-weight: bold;
  font-family: 'Orbitron', sans-serif;
  text-align: right;
  margin-left: 1rem;
  display: block;
  width: 30%;
  transition: font-size 0.5s;
}
@media screen and (max-width: 840px) {
  .container {
    width: 100%;
  }

  .currencyFlag {
    float: none;
    margin-right: 1rem;
  }

  .currencyDetails {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-right: 0;
    margin-bottom: 5px;
  }

  .currencyName {
    margin-right: 0;
  }

  .currencyRate {
    text-align: right;
  }
  .container {
    width: 100%;
  }
}
@media screen and (max-width: 500px) {
  .currencyName {
    font-size: 1rem;
  }
  .currencyRate {
    font-size: 1rem;
  }
  .currencyFlag {
    float: none;
    margin-right: 0.5rem;
  }
  li {
    padding: 0.2rem;
  }
}
@media screen and (max-width: 340px) {
  .currencyName {
    font-size: 0.8rem;
  }
  .currencyRate {
    font-size: 0.8rem;
  }

  .currencyFlag {
    float: none;
    margin-right: 0.5rem;
  }
  li {
    padding: 0.2rem;
  }
}
</style>
