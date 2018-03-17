<template>
    <div id="FooterContact" class="footer__contact">
        <div class="container">
            <div class="row">
                <div class="holder center-elem">
                    <h2>{{ section_title }}</h2>
                    <div>
                        <ul>
                            <li v-for='(contact, index) in contact_items' :key='index'>
                                <span>{{ contact.platform }}:</span> <a :href="contact.link_url">{{ contact.link_text }}</a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import { butter } from '@/buttercms'
    export default {
        name: 'FooterContact',
        data() {
            return {
                section_title: 'Contact Me',
                contact_items: ''
            }
        },
        methods: {
            getContact() {
                butter.content.retrieve(['benjaminfell_contact'])
                  .then((res) => {
                      console.log(res.data.data)
                      this.contact_items = res.data.data.benjaminfell_contact
                  })
            }
        },
        created() {
            this.getContact()
        }
    }
</script>

<style lang="scss" scoped>

    h2 {
        margin-bottom: 15px;
        font-size: 26px;
        font-weight: 600;
    }

    ul {
        padding: 0;
        list-style-type: none;

        li {
            font-size: 16px;
        }
    }

    .footer__contact {
        border-bottom: 1px solid #eeeeee;
    }

    .holder {
        padding: 20px 3.5%;
    }

    @media (min-width: 768px) {
        .holder {
            width: 90vw;
            padding: 20px 0;
        }
    }

</style>
