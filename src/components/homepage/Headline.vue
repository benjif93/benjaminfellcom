<template>
  <div id="Headline" class="homepage__headline bg-primary txt-white">
      <div class="container">
        <div class="row">
            <h2 class="center-elem">{{ headline_content }}</h2>
        </div>
      </div>
  </div>
</template>

<script>
    import { butter } from '@/buttercms'
    export default {
        name: 'homepage-headline',
        data() {
            return {
                headline_content: ''
            }
        },
        methods: {
            getHeadline() {
                butter.content.retrieve(['benjaminfell_homepage_headline'])
                  .then((res) => {
                    console.log(res.data.data)
                    this.headline_content = res.data.data.benjaminfell_homepage_headline
                  })
            }
        },
        created() {
            this.getHeadline()
        }
    }
</script>

<style scoped>
    h2 {
        padding: 40px 3.5%;
        font-family: "Open Sans";
        font-size: calc(.8em + (2vw));
        line-height: 1.43;
    }

    @media (min-width: 768px) {
        h2 {
            width: 90vw;
            padding: 80px 0;
        }
    }
</style>
