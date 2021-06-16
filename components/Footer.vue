<template>
  <footer class="container footer">
    <a
      href="https://stakes.social/invite/github"
      class="link-invite"
      target="_blank"
    >
      Do you have eligible OSS projects❓<br />
      Please send us request here 📩
    </a>

    <a href="https://stakes.social/" class="link-stakes" target="_blank">
      <a-row class="footer-link-stales-social" type="flex">
        <img class="ss-logo" src="/images/stakes-social-logo.png" alt="logo" />
        <div class="ss-logo-msg">Originally created with ❤️ in Japan</div>
      </a-row>
    </a>
    <a href="/" class="link-logo">
      <img src="/images/header-logo.svg" alt="logo" />
    </a>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  padding: 11rem 0;
  text-align: center;

  @media (max-width: 576px) {
    padding: 6.25rem 0;
  }

  .link-invite {
    display: block;
    margin-bottom: 60px;
    font-size: 0.9375rem;
    line-height: 200%;
  }

  .footer-link-stales-social {
    flex-direction: column;
    align-items: center;
    margin-bottom: 3.75rem;

    .ss-logo {
      margin-bottom: 0.625rem;
      width: 15.5rem;
    }

    .ss-logo-msg {
      font-size: 0.875rem;
    }
  }

  .link-logo {
    width: 5.375rem;
  }
}
</style>
