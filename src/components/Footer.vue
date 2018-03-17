<template>
  <div id="Footer">
    <footer-contact></footer-contact>
    <footer-copyright></footer-copyright>
  </div>
</template>

<script>
    import FooterContact from '@/components/footer/Contact'
    import FooterCopyright from '@/components/footer/Copyright'
    export default {
        name: 'Footer',
        components: {
            'footer-contact': FooterContact,
            'footer-copyright': FooterCopyright
        }
    }
</script>