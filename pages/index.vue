<template>
  <div id="index">
    <div class="emojis">
      <no-ssr>
        <marquee-text :duration="80" :repeat="2">
          {{ emojis }}
        </marquee-text>
      </no-ssr>
    </div>
    <div class="logo">
      <div class="logo">
        <span class="title">Bingo</span>
        <img class="logo" src="@/static/logo.png" />
        <span class="title">Bango</span>
      </div>
      <span class="text">{{ $t('home.description') }}</span>
      <span class="text">{{ $t('home.comingSoon') }}</span>
    </div>
    <div class="cards">
      <StubCard
        class="card1"
        :price="$t('home.cards.1.price')"
        :title="$t('home.cards.1.title')"
        :location="$t('home.cards.1.location')"
        :description="$t('home.cards.1.description')"
      />
      <StubCard
        class="card2"
        :price="$t('home.cards.2.price')"
        :title="$t('home.cards.2.title')"
        :location="$t('home.cards.2.location')"
        :description="$t('home.cards.2.description')"
      />
      <StubCard
        class="card3"
        :price="$t('home.cards.3.price')"
        :title="$t('home.cards.3.title')"
        :location="$t('home.cards.3.location')"
        :description="$t('home.cards.3.description')"
      />
    </div>
  </div>
</template>

<script>
import StubCard from '@/components/StubCard'
import emojis from '@/assets/emojis.js'
export default {
  components: {
    StubCard
  },
  data() {
    return {
      emojis: emojis().join('')
    }
  },
  head() {
    return {
      title: this.$t('home.pageTitle'),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('home.description')
        }
      ]
    }
  }
}
</script>

<style lang="sass">
@import '@/styles/Typography.sass'
@import '@/node_modules/include-media/dist/_include-media.scss'
#index
  display: grid
  user-select: none
  height: 100vh
  overflow: hidden
  width: 100vw
  grid-template-rows: 1fr 3fr 1fr
  grid-template-columns: 1fr
  grid-template-areas: "emojis" "logo" "cards"
  .emojis
    display: flex
    align-items: center
    grid-area: emojis
    font-size: 48px
    letter-spacing: 32px
    min-width: 0
  .logo
    grid-area: logo
    display: flex
    justify-content: center
    align-items: center
    flex-direction: column
    margin-bottom: 24px
    text-align: center
    .title
      @include media("<desktop")
        @include typography(head)
        font-size: 13vw
      @include media(">=desktop")
        @include typography(huge)
      margin-bottom: 16px
    .text
      @include typography(normal)
      margin-top: 16px
      max-width: 400px
      padding: 0 16px
    .logo
      display: flex
      flex-direction: row
      .logo
        width: 15vw
        max-width: 196px
        margin: 0 -4.5vw 0 -4vw
        z-index: 10
        transform: translateY(minmax(-.5vw, -10px))
        border-radius: 98px
  .signup
    grid-area: signup
    display: flex
    flex-direction: column
    max-width: 315px
    margin: 0 auto
    justify-content: center
    align-items: center
    text-align: center
    .description
      @include typography(normal)
  .cards
    grid-area: cards
    display: flex
    flex-direction: row
    justify-content: space-around
    transform: translateY(32px)
    @include media("<desktop")
        transform: translateY(32px) scale(.9)
    > *
      padding-bottom: 64px
      @include media("<desktop")
        padding-bottom: 32px
    .card1
      transform: rotate(-5deg)
    .card2
      @include media("<desktop")
        display: none
      transform: rotate(4.5deg)
    .card3
      @include media("<desktop")
        display: none
      transform: rotate(2.86deg)
</style>
