<template>
  <section id="intro" class=" text-dark-blue section bg-dark-blue/30">
    <div class="section-ctn min-h-fit">
      <div class="flex flex-col space-y-3 ">
        <div class="mx-auto space-y-2 tracking-wider normal-case text-gold-500 header">
          ₿itcoin
        </div>
        <div class="mx-auto space-y-2 tracking-wider normal-case text-gold-500 header">
          <div>
            The safest way to store and transfer wealth across time and space.
          </div>
        </div>

        <div
          class="flex flex-col space-y-1 text-base leading-relaxed tracking-wide text-center text-gray-300 md:space-y-3 paragraph md:px-20 md:text-xl">
          <ul class="space-y-2 list-outside none">
            <li>
              No dilution.
            </li>
            <li>
              No asset confiscation.
            </li>
            <li>
              No counter-party risk.
            </li>
            <li>
              No single point of failure.
            </li>
          </ul>
          <!-- 
          <div>
            Getting Bitcoin Self-Custody right is of primary importance to build and maintain your legacy in a world of
            increased risks.</div>
          <div>
            BV Custody provides you with best-in-class tools and expertise.</div>

            <div>
              For more than a decade, BitcoinVN has been directing private clients and family offices to enter the world of
              Bitcoin and protect and preserve their wealth for future generations.</div>
              <div>
                Benefit from our high-touch approach to design the solution tailored to your specific situation in life.</div>
              -->
        </div>
        <div>
          <button @click="contact"
            class="h-12 font-semibold tracking-wider text-white uppercase rounded-full hover:border-2 w-60 bg-gradient-to-r from-gold-500/60 to-gold-500/90 border-dark-blue hover:border-white">
            Contact Us
          </button>
        </div>
        <div
          class="flex flex-col space-y-1 text-sm leading-relaxed tracking-wide text-center text-gray-600 md:space-y-3 paragraph md:px-20 hover:text-white md:text-sm hover:underline hover:underline-offset-8 hover:decoration-1">
          <a href="https://newsletter.bitcoinvn.io/private-client?utm_source=custody&utm_medium=intro_section&utm_campaign=subscribe"
            target="_blank"> Or subscribe to our private client newsletter. </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  methods: {
    contact() {
      FreshworksWidget('open');
    }

  }
}
</script>