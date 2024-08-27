<template>
    <div class="">
        <div class="container my-3 py-3">
            <p class="px-2 py-3 text-center mb-0 bill"><span class="fs-2">~ Connect ~</span></p>

            <div class="row d-flex justify-content-center ">
                <div v-for="(icon, index) in contact" :key="index" class="col-3 col-md-3 py-2"
                    @click="handleIconClick(icon.action)">
                    <div class="d-flex justify-content-center align-items-center">
                        <div class="rounded-circle border border-5 d-flex align-items-center justify-content-center"
                            style="width: 60px; height: 60px;background: black !important;">
                            <a class="text-white" :href="icon.url" target="_blank">
                                <i :class="icon.icon"></i>
                            </a>
                        </div>
                    </div>
                    <p class="text-center mt-2 fw-bold">{{ icon.name }}</p>
                </div>
            </div>
        </div>


    </div>

</template>
<script>
export default {
    name: 'ContactCard',
    data() {
        return {
            contact: [
                { name: 'Email', icon: 'bi-envelope-fill fs-5', action: 'openEmail' },
                { name: 'Call', icon: 'bi-telephone-fill fs-5', action: 'openDialer' }, 
                { name: 'Whatsapp', icon: 'bi-whatsapp fs-5', action: 'openWhatsapp' },
                { name: 'Map', icon: 'bi-geo-fill fs-5', action: 'openMaps' }, 
                {
                    icon: 'bi bi-facebook fs-3', name: 'Facebook', url: 'https://www.facebook.com/yourpage'
                },
                {
                    icon: 'bi bi-globe fs-3', name: 'Website', url: 'https://covisor.in'
                },
                {
                    icon: 'bi bi-youtube fs-3', name: 'YouTube', url: 'https://www.youtube.com/'
                },
                {
                    icon: 'bi bi-linkedin fs-3', name: 'LinkedIn', url: 'https://www.linkedin.com/in/yourprofile'
                },
            ],
            name: '',
            email: '',
            query: '',
        }
    },
    methods: {
        handleIconClick(action) {
            const phoneNumber = '+918802172121';
            const emailAddress = 'ayush@covisor.in';
            const location = '2nd Floor, Block B1/632, Janakpuri, Delhi, 110058';
            // const offcanvasQuery = new window.bootstrap.Offcanvas(document.getElementById('offcanvasQuery'));
            // let blob, url, a;

            // const vcardContent = `BEGIN:VCARD
            // VERSION:3.0
            // N:;${phoneNumber};;;
            // FN:${phoneNumber}
            // TEL;TYPE=CELL:${phoneNumber}
            // END:VCARD`;

            switch (action) {
                case 'openEmail':
                    window.location.href = `mailto:${emailAddress}`;
                    break;
                case 'openDialer':
                    window.location.href = `tel:${phoneNumber}`;
                    break;
                // case 'openSMS':
                //   window.location.href = `sms:${phoneNumber}`;
                //   break;
                // case 'downloadData':
                //   blob = new Blob([vcardContent], { type: 'text/vcard' });
                //   url = window.URL.createObjectURL(blob);
                //   a = document.createElement('a');
                //   a.href = url;
                //   a.download = `contact.vcf`;
                //   a.click();
                //   window.URL.revokeObjectURL(url);
                //   break;
                case 'openWhatsapp':
                    window.open(`https://wa.me/${phoneNumber}?text=Hello...`, '_blank');
                    break;
                case 'openMaps':
                    window.open(`https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(location)}`, '_blank');
                    break;
                // case 'openQuery':
                //     offcanvasQuery.show();
                //     break;
                default:
                    break;
            }
        },
        saveContact() {
            const contactNumber = '+918826658501';
            const contactName = 'Contact Name'; // Add the contact name here

            // Generate VCF content
            const vcfContent = `BEGIN:VCARD
            VERSION:3.0
            FN:${contactName}
            TEL:${contactNumber}
            END:VCARD`;

            // Create a blob from the VCF content
            const blob = new Blob([vcfContent], { type: 'text/vcard' });

            // Create a link element
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = 'contact.vcf';

            // Trigger the download
            document.body.appendChild(link);
            link.click();

            // Clean up
            document.body.removeChild(link);
        },
        submitQuery() {
            console.log('Submit Query')
            const data = {
                name: this.name,
                email: this.email,
                query: this.query,
            }
            this.$store.dispatch('submitQuery', data)
        },
        share() {
            if (navigator.share) {
                navigator.share({
                    title: 'Share this content',
                    text: 'Check out this awesome content!',
                    url: window.location.href,
                }).then(() => {
                    console.log('Successful share');
                }).catch((error) => {
                    console.log('Error sharing', error);
                });
            } else {
                alert('Web Share API is not supported in your browser.');
            }
        },
    }
}
</script>
<style lang="">

</style>