<template>
  <HeaderComponent />
  <main class="l-main bd-container">
    <!-- All elements within this div, is generated in PDF -->
    <div class="resume" id="area-cv" ref="areaCv">
      <div class="resume__left">
        <!--========== HOME ==========-->
        <section class="home" id="home">
          <div class="home__container section bd-grid">
            <div class="home__data bd-grid">
              <img v-if="userData.avatar" :src="userData.avatar" alt="profile-img" class="home__img" />
              <img v-else src="/src/assets/img/default-profile-image.png" alt="profile-img" class="home__img" />
              <h1 class="home__title">{{ fullName.trim() ? fullName : 'John Doe' }}</h1>
              <h3 class="home__profession">
                {{ userData.designation ? userData.designation : 'Game Developer' }}
              </h3>
              <div>
                <a download="" class="home__button-movil" @click="downloadResume">Download</a>
              </div>
            </div>

            <div class="home__address bd-grid">
              <p class="home__information">
                <i class="bx bx-map home__icon"></i>
                <span>{{ userData.address ? userData.address : 'Accra Ghana' }}</span>
              </p>
              <p class="home__information">
                <i class="bx bx-envelope home__icon"></i>
                <span>{{ userData.email ? userData.email : 'user@email.com' }}</span>
              </p>
              <p class="home__information">
                <i class="bx bx-phone home__icon"></i>
                <span>{{ userData.phoneno ? userData.phoneno : '123-456-789' }}</span>
              </p>
            </div>
          </div>
          <!-- Theme change button -->
          <ThemeButton />
          <!-- Button to generate and download the pdf. Available for desktop. -->
          <i
            class="bx bx-download generate-pdf"
            title="Generate PDF"
            id="resume-button"
            @click="downloadResume"
          ></i>
        </section>

        <!--========== SOCIAL ==========-->
        <section class="social section">
          <h2 class="section-title">SOCIAL</h2>
          <div class="social__container bd-grid">
            <a href="https://www.linkedin.com/" target="_blank" class="social__link">
              <i class="bx bxl-linkedin-square social__icon"></i>
              <span style="white-space: normal; word-break: break-word">{{
                userData.linkedin ? userData.linkedin : 'https://www.linkedin.com/username/'
              }}</span>
            </a>
            <a href="https://github.com/" target="_blank" class="social__link">
              <i class="bx bxl-github social__icon"></i>
              <span style="white-space: normal; word-break: break-word">{{
                userData.github ? userData.github : 'https://github.com/username/'
              }}</span>
            </a>
            <a href="https://twitter.com/" target="_blank" class="social__link">
              <i class="bx bx-at social__icon"></i>
              <span style="white-space: normal; word-break: break-word">{{
                userData.website ? userData.website : 'https://mywebsite.com'
              }}</span>
            </a>
          </div>
        </section>

        <!--========== PROFILE ==========-->
        <section class="profile section" id="profile">
          <h2 class="section-title">Profile</h2>
          <p v-if="!userData.summary" class="profile__description">
            I am a person, responsible with their work during working hours. Finish various
            technical and higher studies at large universities. I have several years of experience
            and achievements in the labor field.
          </p>
          <p v-else>{{ userData.summary }}</p>
        </section>

        <!--========== EDUCATION ==========-->
        <section class="education section" id="education">
          <h2 class="section-title">Education</h2>
          <div class="education__container bd-grid">
            <div
              v-for="(item, index) in userData.educationItems"
              :key="index"
              class="education__content"
            >
              <div class="education__time">
                <span class="education__rounder"></span>
                <span
                  v-if="userData.educationItems.length - 1 !== index"
                  class="education__line"
                ></span>
              </div>
              <div class="education__data bd-grid">
                <h3 class="education__title">{{ item.edu_school }}</h3>
                <p class="education__studies">
                  {{
                    item.edu_degree
                      ? `${item.edu_degree}, ${item.edu_description}`
                      : 'MASTER OF DESIGN'
                  }}
                </p>
                <span class="education__studies">{{
                  item.edu_city ? item.edu_city : 'University of Studies'
                }}</span>
                <span class="education__year">{{
                  item.edu_start_date
                    ? formatString(item.edu_start_date, item.edu_graduation_date)
                    : '2010 - 2015'
                }}</span>
              </div>
            </div>
          </div>
        </section>
        <!--========== SKILLS  ==========-->
        <section class="skills section" id="skills">
          <h2 class="section-title">Skills</h2>

          <div class="skills__content bd-grid">
            <ul v-for="(item, index) in userData.skills" :key="index" class="skills__data">
              <li class="skills__name">
                <span class="skills__circle"></span>{{ item.skill ? item.skill : 'HTML 5' }}
              </li>
            </ul>
          </div>
        </section>
      </div>

      <div class="resume__right">
        <!--========== EXPERIENCE ==========-->
        <section class="experience section" id="experience">
          <h2 class="section-title">Experience</h2>

          <div class="experience__container bd-grid">
            <div class="experience__content">
              <div class="experience__time">
                <span class="experience__rounder"></span>
                <span class="experience__line"></span>
              </div>

              <div class="experience__data bd-grid">
                <h3 class="experience__title">MASTER OF DESIGN</h3>
                <span class="experience__company"
                  >From 2013 to 2015 | Accra Institute of Technology</span
                >
                <p class="experience__description">
                  Work in this company dedicating the best responsibility in the area that
                  corresponds, delivering the best results for the company and improving
                  productivity.
                </p>
              </div>
            </div>

            <div class="experience__content">
              <div class="experience__time">
                <span class="experience__rounder"></span>
                <span class="experience__line"></span>
              </div>

              <div class="experience__data bd-grid">
                <h3 class="experience__title">MASTER OF GAMES</h3>
                <span class="experience__company">From 2013 to 2015 | Bullet Echo</span>
                <p class="experience__description">
                  Work in this company dedicating the best responsibility in the area that
                  corresponds, delivering the best results for the company and improving
                  productivity.
                </p>
              </div>
            </div>

            <div class="experience__content">
              <div class="experience__time">
                <span class="experience__rounder"></span>
              </div>

              <div class="experience__data bd-grid">
                <h3 class="experience__title">WEB DEVELOPMENT</h3>
                <span class="experience__company"
                  >From 2013 to 2015 | Accra Institute of Technology</span
                >
                <p class="experience__description">
                  Work in this company dedicating the best responsibility in the area that
                  corresponds, delivering the best results for the company and improving
                  productivity.
                </p>
              </div>
            </div>
          </div>
        </section>

        <!--========== CERTIFICATES ==========-->
        <section class="certificate section" id="certificates">
          <h2 class="section-title">Certificates</h2>

          <div class="certificate__container bd-grid">
            <div class="certificate__content">
              <h3 class="certificate__title">Certified for complaince in the work area (2012)</h3>
              <p class="certificate__description">
                For meeting the expectations of leading the team to work the specified tasks in the
                labor field.
              </p>
            </div>

            <div class="certificate__content">
              <h3 class="certificate__title">Certificate of attendance on computer technology.</h3>
              <p class="certificate__description">
                For meeting the expectations of leading the team to work the specified tasks in the
                labor field.
              </p>
            </div>

            <div class="certificate__content">
              <h3 class="certificate__title">
                Achievement medal for productivity excellence during the year (2019)
              </h3>
              <p class="certificate__description">
                For meeting the expectations of leading the team to work the specified tasks in the
                labor field.
              </p>
            </div>
          </div>
        </section>

        <!--========== REFERENCES ==========-->
        <section class="references section" id="references">
          <h2 class="section-title">References</h2>

          <div class="references__container bd-grid">
            <div class="references__content bd-grid">
              <span class="references__subtitle">Sr. Director</span>
              <h3 class="references__title">Dr. John Doe</h3>
              <ul class="references__contact">
                <li>Phone: 999-777-666</li>
                <li>Email: user@email.com</li>
              </ul>
            </div>

            <div class="references__content bd-grid">
              <span class="references__subtitle">Mag. Developer</span>
              <h3 class="references__title">Mr Choongsaeng Douf</h3>
              <ul class="references__contact">
                <li>Phone: 999-777-555</li>
                <li>Email: user@email.com</li>
              </ul>
            </div>
          </div>
        </section>

        <!--========== LANGUAGES ==========-->
        <section class="languages section">
          <h2 class="section-title">languages</h2>

          <div class="languages__container">
            <ul class="languages__content bd-grid">
              <li class="languages__name"><span class="languages__circle"></span>English</li>
              <li class="languages__name"><span class="languages__circle"></span>Espanol</li>
              <li class="languages__name"><span class="languages__circle"></span>French</li>
            </ul>
          </div>
        </section>

        <!--========== INTERESTS ==========-->
        <section class="interests section">
          <h2 class="section-title">Interests</h2>

          <div class="interests__container bd-grid">
            <div class="interests__content">
              <i class="bx bx-headphone interests__icon"></i>
              <span class="interests__name">Music</span>
            </div>
            <div class="interests__content">
              <i class="bx bxs-plane-alt interests__icon"></i>
              <span class="interests__name">Travel</span>
            </div>
            <div class="interests__content">
              <i class="bx bx-swim interests__icon"></i>
              <span class="interests__name">Pools</span>
            </div>
            <div class="interests__content">
              <i class="bx bx-dumbbell interests__icon"></i>
              <span class="interests__name">Exercise</span>
            </div>
            <div class="interests__content">
              <i class="bx bx-book-open interests__icon"></i>
              <span class="interests__name">Book</span>
            </div>
          </div>
        </section>
      </div>
    </div>
  </main>
  <!--========== SCROLL TOP ==========-->
  <a href="#" class="scrolltop" id="scroll-top" :class="{ 'show-scroll': showScrollTopBtn }">
    <i class="bx bx-up-arrow-alt scrolltop__icon"></i>
  </a>
</template>

<script>
import html2pdf from 'html2pdf.js'
import HeaderComponent from './Header.vue'
import ThemeButton from './ThemeButton.vue'

export default {
  name: 'ResumePreview',
  components: { HeaderComponent, ThemeButton },
  inject: ['userData'],
  data() {
    return {
      showScrollTopBtn: false
    }
  },
  computed: {
    fullName() {
      return `${this.userData.firstName} ${this.userData.middleName} ${this.userData.lastName}`
    }
  },
  mounted() {
    window.addEventListener('scroll', this.scrollTop)
    window.addEventListener('scroll', this.scrollActive)
  },
  unmounted() {
    window.removeEventListener('scroll', this.scrollTop)
    window.removeEventListener('scroll', this.scrollActive)
  },
  methods: {
    formatString(start, end) {
      return start.split('-')[0] + ' - ' + end.split('-')[0]
    },
    scrollActive() {
      const scrollY = window.pageYOffset
      const sections = document.querySelectorAll('section[id]')

      sections.forEach((current) => {
        const sectionHeight = current.offsetHeight
        const sectionTop = current.offsetTop - 50
        const sectionId = current.getAttribute('id')

        if (scrollY > sectionTop && scrollY <= sectionTop + sectionHeight) {
          document
            .querySelector('.nav__menu a[href*=' + sectionId + ']')
            ?.classList.add('active-link')
        } else {
          document
            .querySelector('.nav__menu a[href*=' + sectionId + ']')
            ?.classList.remove('active-link')
        }
      })
    },
    scrollTop() {
      // When the scroll is higher than 200 viewport height, add the show-scroll class to the <a> tag with the scroll-top class
      if (window.pageYOffset >= 200) this.showScrollTopBtn = true
      else this.showScrollTopBtn = false
    },
    scaleCv() {
      /* REDUCE THE SIZE AND PRINT ON AN A4 SHEET */
      document.body.classList.add('scale-cv')
    },
    removeScaleCv() {
      /* REMOVE THE SIZE WHEN THE CV IS DOWNLOADED */
      document.body.classList.remove('scale-cv')
    },
    generateResume() {
      const areaCv = this.$refs.areaCv
      // Html2pdf options
      let opt = {
        margin: 0,
        filename: 'myResume.pdf',
        image: { type: 'jpeg', quality: 0.98 },
        html2canvas: { scale: 4 },
        jsPDF: { format: 'a4', orientation: 'portrait' }
      }
      return html2pdf().set(opt).from(areaCv)
    },
    downloadResume() {
      this.scaleCv()
      this.generateResume()
        .save()
        .then(() => this.removeScaleCv())
    }
  }
}
</script>

<style></style>
