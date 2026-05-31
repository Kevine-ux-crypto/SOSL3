<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1489392191049-fc10c97e64b6?w=1400')"
  >

    <!-- Hero - dark overlay -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Contact Us</h1>
      <p class="text-gray-300 mt-4 text-lg">We'd love to hear from you — let's plan your Rwanda adventure</p>
    </section>

    <!-- Contact Info + Form - green overlay -->
    <section class="bg-green-900/70 px-8 md:px-20 py-20">
      <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16">

        <!-- Left: Contact Info -->
        <div>
          <h2 class="text-3xl font-bold text-white mb-6">Get In Touch</h2>
          <p class="text-green-100 leading-relaxed mb-10">
            Whether you have questions about our tours, need help planning your itinerary,
            or just want to know more about Rwanda — our team is here to help.
          </p>

          <div class="space-y-6">
            <div class="flex items-start gap-4">
              <div class="bg-green-700/60 p-3 rounded-full text-xl">📍</div>
              <div>
                <h4 class="font-semibold text-white">Address</h4>
                <p class="text-green-200 text-sm">KG 123 Street, Kigali, Rwanda</p>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div class="bg-green-700/60 p-3 rounded-full text-xl">📞</div>
              <div>
                <h4 class="font-semibold text-white">Phone</h4>
                <p class="text-green-200 text-sm">+250 788 000 000</p>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div class="bg-green-700/60 p-3 rounded-full text-xl">📧</div>
              <div>
                <h4 class="font-semibold text-white">Email</h4>
                <p class="text-green-200 text-sm">info@visitrwanda.com</p>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div class="bg-green-700/60 p-3 rounded-full text-xl">🕐</div>
              <div>
                <h4 class="font-semibold text-white">Working Hours</h4>
                <p class="text-green-200 text-sm">Mon – Fri: 8:00 AM – 6:00 PM</p>
                <p class="text-green-200 text-sm">Sat: 9:00 AM – 3:00 PM</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Contact Form -->
        <div class="bg-black/40 border border-green-700/50 rounded-2xl p-8">
          <h2 class="text-2xl font-bold text-white mb-6">Send Us a Message</h2>
          <form @submit.prevent="submitForm" class="space-y-5">

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
              <div>
                <label class="block text-green-200 text-sm mb-1">First Name</label>
                <input
                  v-model="form.firstName"
                  type="text"
                  placeholder="John"
                  class="w-full bg-black/30 border border-green-700/50 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:outline-none focus:border-green-400"
                />
              </div>
              <div>
                <label class="block text-green-200 text-sm mb-1">Last Name</label>
                <input
                  v-model="form.lastName"
                  type="text"
                  placeholder="Doe"
                  class="w-full bg-black/30 border border-green-700/50 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:outline-none focus:border-green-400"
                />
              </div>
            </div>

            <div>
              <label class="block text-green-200 text-sm mb-1">Email</label>
              <input
                v-model="form.email"
                type="email"
                placeholder="john@example.com"
                class="w-full bg-black/30 border border-green-700/50 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:outline-none focus:border-green-400"
              />
            </div>

            <div>
              <label class="block text-green-200 text-sm mb-1">Subject</label>
              <select
                v-model="form.subject"
                class="w-full bg-black/30 border border-green-700/50 rounded-lg px-4 py-3 text-white focus:outline-none focus:border-green-400"
              >
                <option value="" disabled selected class="bg-gray-900">Select a subject</option>
                <option value="tour" class="bg-gray-900">Tour Inquiry</option>
                <option value="accommodation" class="bg-gray-900">Accommodation</option>
                <option value="transport" class="bg-gray-900">Transport</option>
                <option value="other" class="bg-gray-900">Other</option>
              </select>
            </div>

            <div>
              <label class="block text-green-200 text-sm mb-1">Message</label>
              <textarea
                v-model="form.message"
                rows="5"
                placeholder="Tell us about your travel plans..."
                class="w-full bg-black/30 border border-green-700/50 rounded-lg px-4 py-3 text-white placeholder-gray-400 focus:outline-none focus:border-green-400 resize-none"
              ></textarea>
            </div>

            <button
              type="submit"
              class="w-full bg-green-600 hover:bg-green-500 text-white font-bold py-3 rounded-full transition duration-200"
            >
              Send Message
            </button>

            <!-- Success Message -->
            <p v-if="submitted" class="text-center text-green-300 text-sm mt-2">
              ✅ Message sent! We'll get back to you shortly.
            </p>

          </form>
        </div>

      </div>
    </section>

    <!-- Map placeholder - emerald overlay -->
    <section class="bg-emerald-900/75 py-16 text-center">
      <h2 class="text-2xl font-bold text-white mb-2">Find Us</h2>
      <p class="text-emerald-200 mb-8">Located in the heart of Kigali, Rwanda</p>
      <div class="mx-auto max-w-4xl px-8">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d63800.22878612446!2d30.0131658!3d-1.9440727!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x19dca4258ed8e797%3A0xe2ff5e430aaa79e1!2sKigali%2C%20Rwanda!5e0!3m2!1sen!2s!4v1700000000000"
          class="w-full h-72 rounded-2xl border border-green-700/50"
          allowfullscreen
          loading="lazy"
        ></iframe>
      </div>
    </section>

  </div>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      submitted: false,
      form: {
        firstName: '',
        lastName: '',
        email: '',
        subject: '',
        message: ''
      }
    }
  },
  methods: {
    submitForm() {
      console.log('Form submitted:', this.form)
      this.submitted = true
      this.form = { firstName: '', lastName: '', email: '', subject: '', message: '' }
      setTimeout(() => { this.submitted = false }, 4000)
    }
  }
}
</script>