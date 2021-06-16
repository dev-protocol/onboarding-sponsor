<template>
  <a-page-header class="header">
    <a href="/" class="logo">
      <img src="/images/header-logo.svg" alt="logo" />
      <span class="display-4">Onboarding Sponsors</span>
    </a>
    <div class="right-content">
      <a href="/?#program-overview" class="display-6">Program overview</a>
    </div>
  </a-page-header>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  padding: 1rem 8rem;

  @media (max-width: 576px) {
    padding: 1rem;
  }
}
a {
  text-decoration: none;
  &,
  &:hover {
    color: black;
  }
}
.logo {
  display: flex;
  align-items: center;

  img {
    padding-right: 0.5rem;
  }

  @media (max-width: 576px) {
    width: 50%;

    span {
      font-size: 14px !important;
      line-height: 120%;
    }
  }
}
.ant-page-header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0;
  width: 100%;

  img {
    width: 86px;
    @media (max-width: 576px) {
      width: 50px;
    }
  }
  .right-content {
    font-weight: 500;
    text-align: right;

    @media (max-width: 576px) {
      width: 50%;

      a {
        font-size: 12px !important;
      }
    }
  }
}
</style>
