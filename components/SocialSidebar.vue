<style lang="scss">
.social-sidebar {
  position: absolute;
  left: 0;
  top: 500px;
  z-index: 100;

  @include mobile {
    display: none;
  }

  .btn {
    display: block;
    position: relative;
    height: 60px;
    width: 80px;
    border-radius: 0 30px 30px 0;
    margin-bottom: 10px;
    transition: width 0.2s ease-in;
    background-image: none;
    padding: 0;
    font-size: 16px;
    
    &:before {
      content: none;
    }

    span {
      font-family: $body-font;
      font-weight: bold;
      color: white;
      text-transform: uppercase;
      display: block;
      line-height: 60px;
      width: 200px;
      text-align: right;
      opacity: 0;
      position: absolute;
      right: 60px;
      transition: opacity 0.4s ease-in;
    }

    img {
      position: absolute;
      height: 50px;
      right: 15px;
      top: 5px;
    }

    &.btn-linkedin img {
      height: 30px;
      top: 15px;
      right: 22.5px;
    }

    &:hover {
      width: 250px;

      span {
        opacity: 1.0;
      }
    }
  }
}
</style>

<template>
  <div class="social-sidebar">
    <twitter-button>
      <span>Share on Twitter</span>
      <img src="~/assets/images/twitter_white.svg" alt="">
    </twitter-button>
    <facebook-button>
      <span>Share on Facebook</span>
      <img src="~/assets/images/facebook_white.svg" alt="">
    </facebook-button>
    <linked-in-button>
      <span>Share on LinkedIn</span>
      <img src="~/assets/images/linked-in-share-button.png" alt="">
    </linked-in-button>
  </div>
</template>

<script>
import FacebookButton from '~/components/FacebookButton'
import TwitterButton from '~/components/TwitterButton'
import LinkedInButton from '~/components/LinkedInButton'

export default {
  components: {
    FacebookButton,
    TwitterButton,
    LinkedInButton
  }
}
</script>