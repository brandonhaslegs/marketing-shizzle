<template>
  <Card class="StubCard">
    <div class="price">
      <span class="text">{{ price }}</span>
    </div>
    <span class="title">{{ title }}</span>
    <div class="location">
      <span class="text">{{ location }}</span>
    </div>
    <span class="description">{{ description }}</span>
  </Card>
</template>

<script>
import Card from '@/components/Card'
export default {
  components: {
    Card
  },
  props: {
    title: {
      type: String,
      default: 'Title'
    },
    location: {
      type: String,
      default: 'Location'
    },
    description: {
      type: String,
      default: 'Description'
    },
    price: {
      type: String,
      default: '0€'
    }
  }
}
</script>

<style scoped lang="sass" src="./StubCard.sass" />
