<template>
    <div id="Copyright" class="footer__copyright">
        <div class="container">
            <div class="row">
                <div class="holder center-elem">
                    <div class="footer__copyright__mainmenu">
                        <main-menu></main-menu>
                    </div>
                    <p>© {{ current_year }} • {{ footer_headline }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import { butter } from '@/buttercms'
    import MainMenu from '@/components/menu/MainMenu'
    export default {
        name: 'FooterCopyright',
        components: {
            'main-menu': MainMenu
        },
        data() {
            return {
                current_year: new Date(),
                footer_headline: ''
            }
        },
        methods: {
            getCopyright() {
                butter.content.retrieve(['benjaminfell_footer'])
                  .then((res) => {
                      console.log(res.data.data)
                      this.footer_headline = res.data.data.benjaminfell_footer
                  })
            },
            getCurrentYear() {
                this.current_year = (new Date()).getFullYear()
            }
        },
        created() {
            this.getCopyright()
            this.getCurrentYear()
        }
    }
</script>

<style lang="scss">
    .footer__copyright {
        
        &__mainmenu {
            margin-bottom: 15px;

            ul {
                li {
                    margin-right: 10px;
                    font-size: 16px;
                }
            }

            a {
                font-weight: 400;
                color: #333333;
                text-decoration: none;
            }
        }
    }
</style>

<style lang="scss" scoped>
    
    .holder {
        padding: 20px 3.5%;
    }

    .footer__copyright {
        
        &__mainmenu {
            margin-bottom: 15px;
        }
    }

    @media (min-width: 768px) {
        .holder {
            width: 90vw;
            padding: 20px 0;
        }
    }

</style>
