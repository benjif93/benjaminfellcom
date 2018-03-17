<template>
    <div id="Skils" class="homepage__skills bg-tertiary">
        <div class="holder">            
            <h2 class="txt-white">{{ section_title }}</h2>
            <ul>
                <li v-for="(skill, index) in skill_items" :key="index">{{ skill.skill }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
    import { butter } from '@/buttercms'
    export default {
        name: 'Skills',
        data() {
            return {
                section_title: 'Skills',
                skill_items: []
            }
        },
        methods: {
            getSkills() {
                butter.content.retrieve(['benjaminfell_skills'])
                  .then((res) => {
                      console.log(res.data.data)
                      this.skill_items = res.data.data.benjaminfell_skills
                  })
            }
        },
        created() {
            this.getSkills()
        }
    }
</script>

<style lang="scss" scoped>
    .holder {
        padding-right: 3.5%;
        padding-left: 3.5%;
    }

    ul {
        padding-left: 0;
        list-style-type: none;
        li {
            display: inline-block;
            padding: 3px 8px;
            margin: 0 5px 10px;
            background: #ffffff;
            color: #00171F;
            font-family: "Roboto";
            font-size: 16px;
            text-align: center;
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
        }
    }

    @media (min-width: 768px) {
        .holder {
            padding-right: 5vw;
            padding-left: 3%;
        }
    }
</style>
