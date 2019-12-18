<template>
  <div class="container">
    <h1>Our Pricing</h1>

    <div class="plan-selector">
      <span @click="toggleBilling()" role="button" aria-hidden="true">Monthly</span>
      <button type="button" role="switch" :aria-checked="showMonthlyBilling" @click="toggleBilling()" :class="{active : !showMonthlyBilling}">
        <span class="toggle" aria-hidden="true"></span>
        <span class="visually-hidden">Monthly</span>
        <span class="visually-hidden">Annually</span>
      </button>
      <span @click="toggleBilling()" role="button" aria-hidden="true">Annually</span>
    </div>

    <div class="plans">
      <div v-for="plan in plans" :key="plan.title" class="plan">
        <div>
          <!-- This container exists to deal with scaling issues on desktop -->
          <h2>{{ plan.title }}</h2>
          <div class="price"><span>&dollar;</span>{{ showMonthlyBilling ? plan.monthlyFee : plan.yearlyFee }}</div>
          <ul>
            <li>{{ plan.storage}} Storage</li>
            <li>{{ plan.usersAllowed }} Users Allowed</li>
            <li>Send up to {{ plan.bandwidth }}</li>
          </ul>
          <a href="#">Learn More</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      plans: [
        {
          bandwidth: '3 GB',
          monthlyFee: '19.99',
          storage: '500 GB',
          title: 'Basic',
          usersAllowed: '2',
          yearlyFee: '199.99',
        },
        {
          bandwidth: '10 GB',
          monthlyFee: '24.99',
          storage: '1 TB',
          title: 'Professional',
          usersAllowed: '5',
          yearlyFee: '249.99',
        },
        {
          bandwidth: '20 GB',
          monthlyFee: '39.99',
          storage: '2 TB',
          title: 'Master',
          usersAllowed: '10',
          yearlyFee: '399.99',
        }
      ],
      showMonthlyBilling: true,
    }
  },
  methods: {
    toggleBilling () {
      this.showMonthlyBilling = !this.showMonthlyBilling;
    }
  }
}
</script>

<style>
  a {
    background: rgb(153,159,243);
    background: linear-gradient(90deg, rgba(153,159,243,1) 0%, rgba(113,120,237,1) 100%);
    border-radius: 6px;
    border: rgba(0,0,0,0) 1px solid;
    color: white;
    display: block;
    line-height: 43px;
    text-decoration: none;
    text-transform: uppercase;
    transition: all .2s;
  }

  a:hover {
    background: #fff;
    border-color: rgba(113,120,237,1);
    color: rgba(113,120,237,1);
  }

  button {
    background: rgb(153,159,243);
    background: linear-gradient(90deg, rgba(153,159,243,1) 0%, rgba(113,120,237,1) 100%);
    border-radius: 16px;
    border: 0;
    cursor: pointer;
    height: 32px;
    margin: 0 10px;
    outline: none;
    position: relative;
    width: 57px;
  }

  button.active span {
    transform: translateX(calc(57px - 32px));
  }

  h1, .plan-selector > span {
    color: hsl(233, 13%, 49%);
  }

  h1 {
    margin-bottom: 40px;
  }

  h2 {
    font-size: 18px;
    line-height: 1;
    margin-bottom: 22px;
  }

  li {
    border-top: #ccc 1px solid;
    color: hsl(232, 13%, 33%);
    line-height: 52px;
  }

  ul {
    border-bottom: #ccc 1px solid;
    list-style: none;
    margin: 0 0 32px;
    padding: 0;
  }
 
  .container {
    display: flex;
    flex-direction: column;
    padding-top: 65px;
    text-align: center;
  }

  .plan {
    background-color: #fff;
    border-radius: 8px;
    margin-bottom: 20px;
    max-width: 327px;
    padding: 40px 30px;
    text-align: center;
    width: 100%;
  }

  .plan:nth-child(2n) {
    background: rgb(153,159,243);
    background: linear-gradient(180deg, rgba(153,159,243,1) 0%, rgba(113,120,237,1) 100%);
    color: #fff;
  }

  .plan:nth-child(2n) a {
    background: white;
    color: rgba(113,120,237,1)
  }

  .plan:nth-child(2n) a:hover {
    background: rgba(0,0,0,0);
    border-color: #fff;
    color: #fff;
  }

  .plan:nth-child(2n) ul,
  .plan:nth-child(2n) li  {
    border-color: rgba(255,255,255,.2);
    color: #fff;
  }

  .plan:nth-child(2n) .price,
  .plan:nth-child(2n) .price span {
    color: #fff;
  }

  .plans {
    align-items: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-bottom: 40px;
  }
  
  .plan-selector {
    align-items: center;
    display: flex;
    justify-content: center;
    margin-bottom: 60px;
  }

  .price {
    color: #000;
    font-size: 72px;
    letter-spacing: -2px;
    line-height: 1;
  }

  .price span {
    color: hsl(232, 13%, 33%);
    display: inline-block;
    font-size: 50%;
    margin-bottom: 22px;
    padding-right: 10px;
    transform: translateY(-25%);
  }

  .toggle {
    background-color: #fff;
    border-radius: 100%;
    display: inline-block;
    height: 24px;
    left: 4px;
    position: absolute;
    top: 4px; 
    transition: all .2s;
    width: 24px;
  } 

  @media (min-width: 1024px) {
    h1 {
      margin-bottom: 20px;
    }

    .container {
      align-items: center;
      display: flex;
      flex-direction: column;
      height: 100vh;
      justify-content: center;
      width: 100%;
    }

    .plan {
      margin-bottom: 0;
    }

    .plans,
    .plan-selector,
    h1 {
      align-self: center;
    }
    
    .plan-selector {
      margin-bottom: 60px;
    }

    .plan-selector span {
      cursor: pointer;
    }    

    .plan:nth-child(2n) {
      transform: scaleY(1.1) scaleX(1.1)
    }

    .plan:nth-child(2n) > div {
      transform: scaleY(.91) scaleX(.91);
    }

    .plans {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      margin-bottom: 80px;
      width: calc(3 * 327px);
    }
  }
</style>
