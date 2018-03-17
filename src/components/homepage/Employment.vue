<template>
    <div id="Employment" class="homepage__employment bg-secondary">
        <div class="holder">
            <h2 class="txt-white">{{ section_title }}</h2>
            <div class="employment-list">
                <div v-for="(employer, index) in employment_items" :key="index" class="employment-list__card">
                    <div class="employment-list__info">
                        <div class="employment-list__location"><h3>{{ employer.organisation_name }}</h3>, <p>{{ employer.organistion_base }}</p></div>
                        <div class="employment-list__date"><time>{{ employer.date_from | dateFormat }}</time> - <time>{{ employer.date_to | dateFormat }}</time></div>
                        <div class="employment-list__role">{{ employer.role }}</div>
                    </div>
                    <div class="employment-list__duties-and-achivements">
                        <h4>{{ section_subtitle }}</h4>
                        <div v-html="employer.duties_and_achivements"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
    import { butter } from '@/buttercms'
    export default {
        name: 'Employment',
        data() {
            return {
                section_title: 'Employment',
                section_subtitle: 'Duties and Achivements',
                employment_items: []
            }
        },
        methods: {
            getEmployment() {
                butter.content.retrieve(['benjaminfell_employment'])
                    .then((res) => {
                        console.log(res.data.data);
                        this.employment_items = res.data.data.benjaminfell_employment
                    })
            }
        },
        created() {
            this.getEmployment();
        },
        filters: {
            dateFormat: function (value) {
                var date = new Date(value),
                    locale = 'en-gb',
                    month  = date.toLocaleString(locale, {month: "long"}),
                    year   = date.getFullYear()
                return month + ' ' + year; 
            }
        }
    }
</script>

<style lang="scss" scoped>

    h4 {
        font-size: 18px;
        margin-bottom: 10px;
    }

    ul {
        li {
            font-size: 14px;
        }
    }

    .holder {
        padding-right: 3.5%;
        padding-left: 3.5%;
    }

    .employment-list {

        &__card {
            padding: 17.5px;
            margin: 5px 0 10px;
            background: #ffffff;
            border-radius: 5px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
            transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        }

        &__location {
            > * {
                display: inline-block;
                font-size: 22px;
            }
        }

        &__date {
            margin-bottom: 10px;
            font-size: 12px;         
        }

        &__role {
            padding-bottom: 10px;
            margin-bottom: 10px;
            font-size: 14px;
            line-height: 1.43;
            border-bottom: 1px solid #EEEEEE;
        }
    }

    @media (min-width: 768px) {
        .holder {
            float: right;
            padding-right: 3%;
            padding-left: 5vw;
        }
    }

</style>