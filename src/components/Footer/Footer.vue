<template>
  <footer class="footer">
    <div class="footer__left">
      <p class="left__description">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique
        nostrum repudiandae odio tempore quis reprehenderit ullam excepturi
        maxime eligendi nam blanditiis eveniet dolorem rerum asperiores
        repellat, ipsam iste ratione nemo.
      </p>
      <div class="left__icons">
        <ul class="icons">
          <li class="icon">
            <img class="i" src="../../assets/icons/facebook.png" alt="" />
          </li>
          <li class="icon">
            <img class="i" src="../../assets/icons/instagram.png" alt="" />
          </li>
          <li class="icon">
            <img class="i" src="../../assets/icons/youtube.png" alt="" />
          </li>
        </ul>
      </div>
    </div>
    <div class="footer__right">
      <h3 class="right__title">Kontakt</h3>
      <ul class="right__options">
        <li class="option__link">+48 21374202</li>
        <li class="option__link">2137@gmail.com</li>
      </ul>
    </div>
  </footer>
</template>

<script></script>

<style lang="scss">
@import "~/assets/styles/_variables.scss";
.footer {
  width: 100%;
  padding: 2rem 0 2rem 0;
  margin: 1rem 0 0 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-top: 0.05rem solid $white-color;
  border-bottom: 0.05rem solid $white-color;

  .footer__left {
    .left__description {
      margin: 1rem 0 1rem 0;
      text-align: justify;
      color: $gray-color;
    }
    .left__icons {
      display: flex;
      flex-direction: column;
      margin: 0 0 1rem 0;
      .logo {
        width: 150px;
        height: 150px;
        background: url("../../assets/images/logo.jpg");
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
      }
      .icons {
        width: 100%;
        padding: 0;
        display: flex;
        justify-content: flex-start;
        align-items: flex-end;
        list-style-type: none;

        .icon {
          width: 40px;
          height: 40px;
          display: flex;
          justify-content: center;
          align-items: center;
          margin: 0 1rem 0 0;

          .i {
            width: 100%;
            height: 100%;
          }
        }

        .icon:nth-of-type(3) {
          .i {
            width: 50px;
            height: 50px;
            margin: 10px 0 0 0;
          }
        }
      }
    }
  }

  .footer__right {
    width: 100%;
    .right__title {
      color: $white-color;
    }

    .right__options {
      list-style-type: none;
      padding: 0;
      margin: 1rem 0 0 0;
    }

    .option__link {
      padding: 0 0 0.5rem 0;
      color: $gray-color;
    }
  }
}
</style>
