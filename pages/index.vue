<template>
  <a-layout>
    <div class="hero">
      <div class="title display-2 font-whyte-inktrap">
        Another way to help OSS projects
      </div>
      <div class="information display-5">
        More than 90% of OSS projects are run by non-crypto users and have
        trouble onboarding on Stakes.social because they don't have a small
        amount of ETH for gas fee. You can help by donating the cost of their
        gas fee and help make their crypto experience an amazing journey.
      </div>
    </div>
    <div class="donation-wrapper">
      <a-row class="donation" type="flex" justify="center" align="top">
        <div class="message display-5 font-whyte-inktrap">
          Donations are accepted in ETH or USD
        </div>
        <a href="/?#how-to-be-a-sponsor" class="how-to display-5 blue"
          >How to be a sponsor →</a
        >
      </a-row>

      <a-row
        class="donation-way"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="way-left" :xs="24" :sm="24" :md="12" :lg="12">
          <div class="currency display-5 font-whyte-inktrap">ETH</div>
          <div class="way">
            <img src="/images/eth_qr.png" alt="ETH" />
          </div>
          <div class="message01">
            0x4528e1D848A38AD3662EA11A1669B4831258252E
          </div>
          <a
            href="https://etherscan.io/address/0x4528e1D848A38AD3662EA11A1669B4831258252E"
            class="message02 display-6"
            target="_blank"
            >View on Etherscan ↗</a
          >
        </a-col>
        <a-col class="way-right" :xs="24" :sm="24" :md="12" :lg="12">
          <div class="currency display-5 font-whyte-inktrap">USD</div>
          <div class="way">
            <a-button
              type="default"
              class="stripe display-5"
              @click="handleStripe"
              >Pay $150 with Stripe</a-button
            >
          </div>
        </a-col>
      </a-row>
    </div>
    <div class="special-sponsors-wrapper">
      <div class="section-title display-5">Special sponsors</div>
      <a href="https://sios.jp/products/oss/yorozu/" target="_blank">
        <img
          src="/images/sponsors/logos/sios.png"
          alt="SIOS"
          class="sponsors-logo"
        />
      </a>
    </div>
    <div class="fundable-list-wrapper">
      <div class="section-title display-4">All fundable OSSs</div>
      <a-row
        v-for="(oss, index) in sortedFundableOSSsByStars"
        :key="oss.id"
        class="list-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col :xs="3" :sm="3" :md="2" :lg="2">{{ index + 1 }}</a-col>
        <a-col :xs="14" :sm="14" :md="18" :lg="18" span="18"
          ><a :href="oss.url" target="_blank">{{ oss.name }} ↗</a></a-col
        >
        <a-col :xs="7" :sm="7" :md="4" :lg="4" style="text-align: right"
          >{{ oss.stars_display }} stars</a-col
        >
      </a-row>
    </div>
    <div class="sponsors-wrapper">
      <div class="section-title display-4">Sponsors</div>
      <div class="sponsors-title display-5">Special sponsors</div>
      <a href="https://sios.jp/products/oss/yorozu/" target="_blank">
        <img
          src="/images/sponsors/logos/sios.png"
          alt="SIOS"
          class="sponsors-logo"
        />
      </a>
      <div class="sponsors-title display-5">Individual sponsors</div>
      <a-row
        class="individual-sponsors-row"
        type="flex"
        justify="space-between"
      >
        <a-col
          v-for="sponsor in sponsors"
          :key="sponsor.id"
          :xs="24"
          :sm="24"
          :md="12"
          :lg="12"
        >
          <a-row
            class="individual-sponsors-col"
            type="flex"
            justify="space-between"
          >
            <a-col span="12">{{ sponsor.ens || sponsor.address }}</a-col>
          </a-row>
        </a-col>
      </a-row>
    </div>
    <div class="program-overview-wrapper">
      <div id="program-overview" class="section-title display-4">
        Program overview
      </div>
      <a-row
        id="what-is-this"
        class="program-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="program-title" :xs="24" :sm="24" :md="8" :lg="8"
          >What is the purpose of the program?</a-col
        >
        <a-col class="program-content" :xs="24" :sm="24" :md="16" :lg="16"
          >This sponsorship program will support the onboarding of great OSS
          projects that wished to join Stakes.social but have not yet been
          tokenized.
        </a-col>
      </a-row>
      <a-row
        id="benefits-for-sponsors"
        class="program-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="program-title" :xs="24" :sm="24" :md="8" :lg="8"
          >Benefits for sponsors</a-col
        >
        <a-col class="program-content" :xs="24" :sm="24" :md="16" :lg="16"
          >Special sponsors (Enterprises, or those who donate above and beyond)
          will be featured with their logo on the program page and on also
          Stakes.social's front page. <br />
          <br />
          Individual sponsors will be listed with their ENS or wallet address
          and their name on the Stripe payment. please make
          <a
            href="https://buy.stripe.com/dR600w8Rpbme5EY7su"
            style="text-decoration: underline"
            >a donation here</a
          >
          if you would prefer to be anonymous.
        </a-col>
      </a-row>
      <a-row
        id="how-to-be-a-sponsor"
        class="program-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="program-title" :xs="24" :sm="24" :md="8" :lg="8">
          How to be a sponsor?
        </a-col>
        <a-col class="program-content" :xs="24" :sm="24" :md="16" :lg="16">
          Send 0.05 ETH to the specified address, or pay 150 USD with a credit
          card. If you want to become a special sponsor, please enter via
          <a
            href="https://airtable.com/shrE9S6Fb6lFGEZhZ"
            style="text-decoration: underline"
            >this form</a
          >.
        </a-col>
      </a-row>
      <a-row
        id="how-donations-are-paid-to-oss"
        class="program-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="program-title" :xs="24" :sm="24" :md="8" :lg="8">
          How are donations paid to OSS?
        </a-col>
        <a-col class="program-content" :xs="24" :sm="24" :md="16" :lg="16">
          The Dev Protocol team will confirm with the OSS owners on whether the
          donation is accepted or not. If they accept it and agree to the
          program, the team will support their onboarding process. If the
          donation exceeds the required amount, it will be used for payment fees
          or carried over to the next month.
        </a-col>
      </a-row>
      <a-row
        id="oss-projects-eligible-for-sponsorship"
        class="program-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="program-title" :xs="24" :sm="24" :md="8" :lg="8">
          OSS projects eligible for sponsorship
        </a-col>
        <a-col class="program-content" :xs="24" :sm="24" :md="16" :lg="16">
          OSS projects with more than 100 stars at the invited date are
          automatically added to the program. The projects are sorted in
          descending order by the number of stars they have, and the gas fee
          equivalent is allocated starting from the top.
        </a-col>
      </a-row>
      <a-row
        id="program-duration"
        class="program-row"
        type="flex"
        justify="space-between"
        align="top"
      >
        <a-col class="program-title" :xs="24" :sm="24" :md="8" :lg="8">
          Program duration
        </a-col>
        <a-col class="program-content" :xs="24" :sm="24" :md="16" :lg="16">
          The program ends on the 31st of August (JST). We will automatically
          add any invitation requests received by the team during this period to
          the program.
        </a-col>
      </a-row>
    </div>
  </a-layout>
</template>

<script>
import Vue from 'vue'
import foundableOSS from '@/assets/json/fundable_oss.json'
import sponsorsData from '@/assets/json/sponsors.json'

export default Vue.extend({
  data() {
    return {
      foundableOSSs: foundableOSS,
      sponsors: sponsorsData,
    }
  },
  computed: {
    sortedFundableOSSsByStars() {
      // eslint-disable-next-line vue/no-side-effects-in-computed-properties
      return this.foundableOSSs.sort((a, b) => {
        return a.stars > b.stars ? -1 : a.stars < b.stars ? 1 : 0
      })
    },
  },
  methods: {
    handleStripe() {
      const url = 'https://buy.stripe.com/eVa8x2ffN4XQffycMN'
      window.open(url, '_blank')
    },
  },
})
</script>

<style lang="scss">
p,
h3,
h4,
dl,
dd {
  margin: 0;
}

.blue {
  color: #0047ff;
}

.ant-layout {
  margin: 0 auto;
  padding-top: 10rem;
  max-width: 53.75rem;
  background-color: #fff;

  @media (max-width: 576px) {
    padding: 6rem 1rem 0;
  }
}

.hero {
  margin-bottom: 6.56rem;

  @media (max-width: 576px) {
    margin-bottom: 0;
  }

  .title {
    position: relative;
    margin-bottom: 7rem;
    width: 100%;
    font-weight: bold;
    text-align: center;

    @media (max-width: 576px) {
      margin-bottom: 2rem;
      font-size: 26px !important;
    }

    &::after {
      content: '';
      position: absolute;
      top: -65px;
      right: 39px;
      width: 78px;
      height: 78px;
      background: url('/images/sponsors/dove.png') no-repeat;
      background-size: contain;

      @media (max-width: 576px) {
        top: -35px;
        right: 25px;
        width: 35px;
        height: 35px;
      }
    }
  }

  .information {
    text-align: center;
    line-height: 130%;

    @media (max-width: 576px) {
      margin-bottom: 4rem;
    }
  }
}

.donation-wrapper {
  margin: 0 auto 11.75rem;
  width: 700px;

  @media (max-width: 576px) {
    margin-bottom: 5rem;
    width: 100%;
  }

  .donation {
    margin-bottom: 3.75rem;

    @media (max-width: 576px) {
      flex-direction: column;
      align-items: center;
      margin-bottom: 2rem;
    }

    .message {
      padding-right: 1rem;
      font-weight: bold;

      @media (max-width: 576px) {
        margin-bottom: 0.625rem;
        padding-right: 0;
      }
    }

    .how-to {
      text-decoration: underline;
    }
  }

  .donation-way {
    text-align: center;

    @media (max-width: 576px) {
      flex-direction: column;

      .way-left {
        margin-bottom: 3.125rem;
      }
    }

    .currency {
      margin-bottom: 2.625rem;
      font-weight: bold;

      @media (max-width: 576px) {
        margin-bottom: 0.625rem;
      }
    }
    .way {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 14rem;

      @media (max-width: 576px) {
        height: unset;

        img {
          width: 12.5rem;
        }
      }
    }
    .message01 {
      margin-bottom: 1.25rem;
      font-size: 0.75rem;

      @media (max-width: 576px) {
        margin-bottom: 0.625rem;
      }
    }
    .stripe {
      padding: 18px;
      height: unset;
      color: #fff;
      background-color: #000;
    }
  }
}

.special-sponsors-wrapper {
  margin: 0 auto 11.25rem;
  width: 700px;
  text-align: center;

  @media (max-width: 576px) {
    margin-bottom: 5rem;
    width: 100%;
  }

  .section-title {
    margin-bottom: 10px;
    text-align: left;
    color: #bfbfbf;
  }

  .sponsors-logo {
    width: 200px;
    height: 200px;
  }
}

.fundable-list-wrapper {
  margin: 0 auto 6.625rem;
  width: 100%;

  @media (max-width: 576px) {
    margin-bottom: 3rem;
  }

  .section-title {
    margin-bottom: 7.5rem;
    font-weight: bold;
    text-align: center;

    @media (max-width: 576px) {
      margin-bottom: 3rem;
    }
  }

  .list-row {
    margin-bottom: 1.125rem;
    font-size: 1.125rem;

    @media (max-width: 576px) {
      font-size: 0.875rem;
    }

    &:last-child {
      margin-bottom: 0;
    }
  }
}

.sponsors-wrapper {
  margin: 0 auto 10.3125rem;
  width: 700px;

  @media (max-width: 576px) {
    margin-bottom: 3rem;
    width: 100%;
  }

  .section-title {
    margin-bottom: 4.1875rem;
    font-weight: bold;
    text-align: center;

    @media (max-width: 576px) {
      margin-bottom: 3rem;
    }
  }

  .sponsors-title {
    margin-bottom: 10px;
    text-align: left;
    color: #bfbfbf;
  }

  .sponsors-logo {
    margin-bottom: 2.5rem;
    width: 5.75rem;
    height: 5.75rem;

    @media (max-width: 576px) {
      margin-bottom: 1.25rem;
    }
  }

  .individual-sponsors-row {
    font-size: 1.125rem;

    @media (max-width: 576px) {
      flex-direction: column;
    }
  }
}

.program-overview-wrapper {
  margin: 0 auto 1.25rem;
  width: 100%;

  .section-title {
    margin-bottom: 5.1875rem;
    font-weight: bold;
    text-align: center;

    @media (max-width: 576px) {
      margin-bottom: 3rem;
    }
  }

  .program-row {
    margin-bottom: 1.5rem;
    min-height: 6.25rem;

    @media (max-width: 576px) {
      margin-bottom: 2.5rem;
      min-height: unset;
    }

    .program-title {
      font-size: 1.125rem;

      @media (max-width: 576px) {
        margin-bottom: 0.625rem;
        font-weight: bold;
      }
    }

    .program-content {
      font-size: 1rem;
    }

    &:last-child {
      margin-bottom: 0;
    }
  }
}
</style>
