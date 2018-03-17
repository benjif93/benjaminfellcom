<template>
  <div id="Homepage" class="app-homepage">
    <homepage-headline></homepage-headline>
    <div class="container">
        <div class="row">
            <div class="employment-and-skills flex flex-wrap">
                <homepage-employment></homepage-employment>
                <homepage-skills></homepage-skills>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
    import HomepageHeadline from '@/components/homepage/Headline'
    import HomepageEmployment from '@/components/homepage/Employment'
    import HomepageSkills from '@/components/homepage/Skills'
    export default {
        name: 'Homepage',
        components: {
            'homepage-headline': HomepageHeadline,
            'homepage-employment': HomepageEmployment,
            'homepage-skills': HomepageSkills
        }
    }
</script>

<style lang="scss">
    
    .homepage {
        $self: &;

        &__employment,
        &__skills {
            padding: 20px 0;

            h2 {
                margin: 0 0 20px;
                font-size: 28px;
            }
        }

        &__employment,
        &__skills { 
            flex-basis: 100%;
        }
    }

    @media (min-width: 768px) {
        .homepage { 
            &__employment {
                flex-basis: 60%;
            }

            &__skills {
                flex-basis: 40%;
            }
        }
    }

</style>