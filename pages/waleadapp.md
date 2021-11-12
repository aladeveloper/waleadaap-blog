---
layout: page
title: WALeadApp
description: WALeadApp by aladeve.
permalink: /waleadapp/
---

<img class="img-rounded" src="/assets/img/uploads/waleadapp-round.png" alt="WALeadApp" width="200">

# WALeadApp,

![placeholder](/assets/img/uploads/waleadapp-main.png "Tampilan Utama WALeadApp")

## Download

<style type="text/css" media="screen">
  .container {
    margin: 0px auto;
    max-width: 600px;
  }
</style>

<div class="container">

  <h2>{{ site.translations.contact.title | default: "Download" }}</h2>

  <div id="form" class="contact-form">
    <form accept-charset="UTF-8" method="POST" action="#" v-on:submit.prevent="validateBeforeSubmit" ref="contact">
      <fieldset>
        <input type="hidden" name="_subject" value="{{ site.translations.contact.subject | default: 'New contact!' }}" />
        <input type="hidden" name="_next" value="{{ site.url }}{{ site.sent_message_url }}" />
        <input type="hidden" name="_language" value="{{ site.language }}" />

        <input type="text" name="name" placeholder="{{ site.translations.contact.placeholders.name | default: 'Your name' }}" v-validate="'required'"
               :class="{ 'has-error': errors.has('name') }">
        <span v-if="errors.has('name')" v-cloak>${ errors.first('name') }</span>

        <input type="text" name="email" placeholder="{{ site.translations.contact.placeholders.email | default: 'Your email' }}" v-validate="'required|email'"
               :class="{ 'has-error': errors.has('email') }">
        <span v-if="errors.has('email')" v-cloak>${ errors.first('email') }</span>

        <textarea name="message" onkeyup="adjust_textarea(this)" placeholder="{{ site.translations.contact.placeholders.message | default: 'Your message' }}" v-validate="'required'"
                  :class="{ 'has-error': errors.has('message') }"></textarea>
        <span v-if="errors.has('message')" v-cloak>${ errors.first('message') }</span>

        <button type="submit">{{ site.translations.contact.submit_btn | default:  "Send" }}</button>
      </fieldset>
    </form>
  </div>

</div>

<script type="text/javascript">
function adjust_textarea(h) {
    h.style.height = "200px";
    h.style.height = (h.scrollHeight)+"px";
}
</script>

<script src="https://unpkg.com/vue@2.4.2"></script>
<script src="https://unpkg.com/vee-validate@2.0.0-rc.8"></script>
<script type="text/javascript">
Vue.use(VeeValidate);

const dictionary = {
  {{ site.translations.contact.errors.locale | default: 'en' }}: {
    custom: {
      name: {
        required: "{{ site.translations.contact.errors.empty_name | default: 'Name is required' }}"
      },
      email: {
        required: "{{ site.translations.contact.errors.empty_email | default: 'Email is required' }}",
        email: "{{ site.translations.contact.errors.invalid_email | default: 'Email is invalid' }}"
      },
      message: {
        required: "{{ site.translations.contact.errors.empty_message | default: 'Message is required' }}"
      }
    }
  }
};

VeeValidate.Validator.updateDictionary(dictionary);
VeeValidate.Validator.setLocale("{{ site.translations.contact.errors.locale | default: 'en' }}");

new Vue({
  el: '#form',
  delimiters: ['${', '}'],
  methods: {
    validateBeforeSubmit: function () {
      this.$validator.validateAll();
      if (!this.errors.any()) {
        this.$refs.contact.submit();
      }
    }
  }
});
</script>

{% else %}

<script>window.location = "{% if site.url == '' and site.baseurl == '' %}/{% else %}{{ site.url }}{{ site.baseurl }}{% endif %}";</script>

{% endif %}


<iframe src="https://docs.google.com/forms/d/e/1FAIpQLSdUvdkn_-UBhLjwa8ZuXPF-xPpW8544qcS-mt94iR-L_1SaEQ/viewform?embedded=true" width="640" height="709" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe>


## Tutorial

1. [Instalasi WALeadApp](http://aladeve.com/apps)
2. [Mengimpor kontak dari Excel](http://aladeve.com/apps)
3. [Menyusun pesan dan emoji](http://aladeve.com/apps)
4. [Memasukkan gambar](http://aladeve.com/apps)
5. [Mengirim pesan broadcast](http://aladeve.com/apps)
6. [Mengekspor laporan ke Excel](http://aladeve.com/apps)
7. [Mengumpulkan respon](http://aladeve.com/apps)

## Video
1. WALeadApp untuk reseller
2. WALeadApp untuk UMKM
3. WALeadApp untuk pendidikan
4. WAleadApp untuk layanan publik





