<template>
  <div class="container">
    <section>
      <h1>
        Small Businesses Can Save the Internet
      </h1>
      <p>Small businesses will be among those hurt most by the loss of net neutrality, but they can also
      play a key role in saving it. In May 2018, we organized thousands of small business owners from
      around the nation to sign on to our open letter to Congress in support of net neutrality.
      Many of these business owners attended protest events and hand-delivered copies of the open letter
      to their lawmakers ... and it worked. The Senate voted to overturn the FCC's repeal of net neutrality.</p>
      <p>Now we need to win the vote in the House of Representatives, and we're calling on small
      business owners once again. Tell your lawmakers to protect competition and free markets on the
      Internet. Tell your lawmakers to support net neutrality.</p>
      <p><a class="btn btn-block" href="#signon">Sign the letter</a></p>
      <nav class="section-links flex-center">
        <a href="#letter">Read the Letter</a>
        <a href="#businesses">Participating Businesses</a>
        <a href="#events">Join an Event</a>
      </nav>
    </section>

    <section id="signon">
      <div v-if="!hasSigned">
        <h2>
          Sign the Letter
          <small>Business owners: enter your company information below</small>
        </h2>
        <action-network-form></action-network-form>
      </div>
      <div class="thanks" v-else>
        <h2>Thanks for signing on.</h2>
        <p>Thank you for signing on the to the open letter in support of the Congressional Review Act (CRA) resolution to restore net neutrality. Please forward widely and spread the word to other small business owners you know:</p>

        <p>Thank you for signing on the to the open letter. We will be sure to add your name.</p>
        <p>Now, will you take the next step and share this campaign to maximize your impact? Share now with just a couple of clicks:</p>

        <p class="buttons">
          <facebook-button></facebook-button>
          &nbsp;
          <twitter-button></twitter-button>
          &nbsp;
          <linked-in-button></linked-in-button>
        </p>

        <p>Now we need you to help deliver the open letter directly to Congress:</p>

        <p>
          <a class="btn btn-block" href="#events">Let's go!</a>
        </p>

        <p>Sharing the open letter widely and helping a delivery and press conference happen will make a difference, and we’ll be here to help you every step of the way.</p>
      </div>
    </section>

    <section id="letter">
      <h2>
        Read the Letter
        <small><a href="/businesses_for_net_neutrality.pdf">Download the Letter to Congress</a></small>
      </h2>
      <div v-html="letterToCongress"></div>
    </section>

    <section id="businesses">
      <h2>Participating Businesses</h2>
      <p>Thousands of businesses have signed the letter to support the CRA to save net neutrality.  Will your business join us?</p>
      <div class="logos">
        <img src="~/assets/images/logos/asbc.png" alt="The American Sustainable Business Council">
        <img src="~/assets/images/logos/demand-progress.png" alt="Demand Progress">
        <img src="~/assets/images/logos/engine.png" alt="Engine Advocacy">
        <img src="~/assets/images/logos/etsy.svg" alt="Etsy" class="padded">
        <img src="~/assets/images/logos/fftf-dark.svg" alt="Fight for the Future">
        <img src="~/assets/images/logos/good-business-colorado.png" alt="Good Business Colorado">
        <img src="~/assets/images/logos/msa.png" alt="The Main Street Alliance">
        <img src="~/assets/images/logos/patreon.svg" alt="Patreon">
        <img src="~/assets/images/logos/small-business-majority.png" alt="Small Business Majority">
      </div>

      <a @click.prevent="toggleBusinessList()" href="#" class="view-all"><span v-if="businessListIsVisible"><strong>-</strong> Hide</span><span v-else><strong>+</strong> View</span> all {{ signatureCount }} Businesses</a>
      <div v-if="businessListIsVisible">
        <p v-if="isLoading"><i>Loading businesses...</i></p>
        <ul v-else>
          <li v-for="biz in businesses" :key="biz.id">
            {{ biz.name }}
            <small v-if="biz.city && biz.state">{{ biz.city }}, {{ biz.state }}</small>
          </li>
        </ul>
      </div>
    </section>

    <section id="events">
      <h2>Host or Join an Event</h2>
      <p>
        <b>Check out the map to find events related to net neutrality in your area</b><br>
        If you’d like to organize a letter delivery to a congressperson in your area, read the instructions below and click the link to Organize a Delivery.
      </p>
      <iframe class="map" :src="eventsMapURL"></iframe>

      <h3>
        How to Organize a Letter Delivery
        <a href="https://docs.google.com/document/d/1dS-GtwKUxFPnjcpXzTtEroEiGmct1L6B-aUVBewN1YQ/" target="_blank">(Click Here to View a Downloadable Package):</a>
      </h3>

      <ol>
        <li>
          <h4>Pick a Congressional Office and Add It to the Map</h4>
          <p>First, decide which member of Congress’ office you want to deliver the letter to. <a href="https://www.battleforthenet.com/scoreboard/" target="_blank">Check here</a> to see where your lawmakers stand on the CRA to save net neutrality and, if you can, organize the letter delivery at the office of a lawmaker who does not yet support the CRA. Preserving the open Internet matters to the overwhelming majority of Americans, so it’s important that we persuade as many members of Congress as possible to vote for the CRA.</p>
        </li>
        <li>
          <h4>Recruit Others and Alert Local Media</h4>
          <p>Once you add your event to the map, we’ll contact other small business owners and net neutrality supporters in your area and encourage them to attend. But you should spread the word too! Invite others to join you directly via email, text message, and social media <a href="https://docs.google.com/document/d/1dS-GtwKUxFPnjcpXzTtEroEiGmct1L6B-aUVBewN1YQ/" target="_blank">(sample content here)</a>. Send a simple Media Advisory <a href="https://docs.google.com/document/d/1dS-GtwKUxFPnjcpXzTtEroEiGmct1L6B-aUVBewN1YQ/" target="_blank">(sample here)</a> to local reporters and invite them to come.</p>
        </li>
        <li>
          <h4 id="deliver-the-letter">Deliver the Letter</h4>
          <p>Select your state below to print out the letter and complete list of businesses who have signed on. Show up a few minutes early and wait outside the office for others to come. Around 15 minutes after the start time, go into the office with your crew of people and deliver the letter to the staffer at the front desk. Be friendly and polite, note the number of businesses in their district that have signed, and ask them to make sure the lawmaker gets it. Reiterate the ask of the letter: we want the Congress member to support the Congressional Review Act (CRA) resolution to overturn the FCC’s repeal of net neutrality.</p>
          <div class="state-selector flex-row">
            <select v-model="selectedState">
              <option :value="null">Select your state</option>
              <option v-for="(name, abbr) in states" :key="abbr" :value="abbr">{{ name }}</option>
            </select>
            <button class="btn" :disabled="!selectedState" @click="printLetter()">Print the Letter</button>
          </div>
        </li>
        <li>
          <h4>Talk to the Press</h4>
          <p>After you deliver the letter, host a short “press conference” outside the office. Gather all your supporters together in a tight group right in front of the building. Think about how it will look in a photo in the local paper. Face the press with your crowd behind you. Have any small business owners in attendance speak for no more than 2 minutes about why they signed the letter and why net neutrality is important to them <a href="https://docs.google.com/document/d/1dS-GtwKUxFPnjcpXzTtEroEiGmct1L6B-aUVBewN1YQ/edit" target="_blank">(sample talking points here)</a>. Have copies of the letter and/or your press advisory to hand to reporters. The whole thing should be quick, wrap it up after 30 minutes or so! Be sure to post photos on social media using the hashtags #SmallBusinessWeek and #NetNeutrality, and send them to us at <a href="mailto:team@fightforthefuture.org">team@fightforthefuture.org</a> so we can share them with the world on social media!</p>

          <div class="organize">
            <p><b>Don’t worry if you’ve never done anything like this before.  Many people who organize a delivery are doing it for the first time.  Organizing a delivery will make a difference, and we’ll be here to help you.</b></p>
            <a :href="createEventURL" target="_blank" @click="$ga.event('button', 'clicked', 'Organize a Delivery')">Organize a Delivery</a>
          </div>
        </li>
      </ol>
    </section>

    <footer class="site-footer">
      <p>Built by:</p>
      <a href="https://www.fightforthefuture.org"><img src="~/assets/images/logos/fftf-dark.svg" alt="Fight for the Future"></a>
      <p>
        Press contact:
        <a href="mailto:press@fightforthefuture.org">press@fightforthefuture.org</a> /
        <a href="tel:15084745248">+1 508 474 5248</a>
      </p>
    </footer>

    <social-sidebar/>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import { stringify } from 'querystring'
import ActionNetworkForm from '~/components/ActionNetworkForm'
import SocialSidebar from '~/components/SocialSidebar'
import FacebookButton from '~/components/FacebookButton'
import TwitterButton from '~/components/TwitterButton'
import LinkedInButton from '~/components/LinkedInButton'
import states from '~/assets/data/states.json'
import { geocodeState, simpleFormat } from '~/assets/js/helpers.js'
import settings from '~/config.json'
import axios from 'axios'

export default {
  components: {
    ActionNetworkForm,
    SocialSidebar,
    FacebookButton,
    TwitterButton,
    LinkedInButton
  },

  computed: {
    ...mapState(['hasSigned']),
    states: () => states,
    signatureCount: () => settings.signatureCount,
    letterToCongress: () => simpleFormat(settings.letterToCongress),

    eventsQueryString() {
      return stringify(Object.assign({
        source: 'businessesfornetneutrality'
      }, this.$route.query))
    },

    createEventURL() {
      return `https://act.demandprogress.org/event/team-internet/create/?${this.eventsQueryString}`
    },

    eventsMapURL() {
      return `https://events.battleforthenet.com/iframe?${this.eventsQueryString}`
    }
  },

  data() {
    return {
      selectedState: null,
      businessListIsVisible: false,
      businesses: [],
      isLoading: false
    }
  },

  async created() {
    try {
      const state = await geocodeState()
      this.selectedState = state.abbr
    }
    catch (error) {
      console.error("Geocoder error", error)
    }
  },

  mounted() {
    if (window.location.hash) {
      const el = document.querySelector(window.location.hash)
      if (el) {
        el.scrollIntoView()
      }
    }
  },

  methods: {
    printLetter() {
      this.$ga.event('button', 'clicked', 'Print the Letter')
      window.open(`/pdfs/${this.selectedState.toLowerCase()}.pdf`, '_blank')
    },

    toggleBusinessList() {
      this.businessListIsVisible = !this.businessListIsVisible

      if (this.businessListIsVisible && this.businesses.length === 0) {
        this.fetchBusinesses()
      }
    },

    async fetchBusinesses() {
      this.isLoading = true
      const { data } = await axios.get('/businesses.json')
      this.businesses = data
      this.isLoading = false
    }
  }
}
</script>
