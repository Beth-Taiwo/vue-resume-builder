<template>
  <div>
    <nav class="navbar bg-white sticky-container">
      <div class="container">
        <div class="navbar-content">
          <div class="brand-and-toggler">
            <a href="index.html" class="navbar-brand">
              <img src="/src/assets/img/curriculum-vitae.png" alt="" class="navbar-brand-icon" />
              <span class="navbar-brand-text">build <span>resume.</span></span>
            </a>
          </div>
        </div>
      </div>
      <div>
        <button class="preview-icon">
          <img src="/src/assets/img/icons8-eye.png" alt="eye_image" class="navbar-brand-icon" />
        </button>
      </div>
    </nav>

    <section id="about-sc" class="">
      <div class="container">
        <!-- form -->
        <div class="build-resume">
          <form action="" class="cv-form" id="cv-form">
            <div class="cv-form-blk">
              <div class="cv-form-row-title">
                <h3>about section</h3>
              </div>
              <div class="cv-form-row cv-form-row-about">
                <div class="cols-3">
                  <div class="form-elem">
                    <label for="" class="form-label">First Name</label>
                    <input
                      v-model="firstName"
                      name="firstname"
                      type="text"
                      class="form-control firstname"
                      id=""
                      placeholder="e.g. John"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label"
                      >Middle Name <span class="opt-text">(optional)</span></label
                    >
                    <input
                      v-model="middleName"
                      name="middlename"
                      type="text"
                      class="form-control middlename"
                      id=""
                      placeholder="e.g. Herbert"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Last Name</label>
                    <input
                      v-model="lastName"
                      name="lastname"
                      type="text"
                      class="form-control lastname"
                      id=""
                      placeholder="e.g. Doe"
                    />
                    <span class="form-text"></span>
                  </div>
                </div>

                <div class="cols-3">
                  <div class="form-elem">
                    <label for="" class="form-label">Your Image</label>
                    <input
                      ref="imgUploadInputRef"
                      name="image"
                      type="file"
                      class="form-control image"
                      id=""
                      accept="image/*"
                      @change="previewImage"
                    />
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Designation</label>
                    <input
                      v-model="designation"
                      name="designation"
                      type="text"
                      class="form-control designation"
                      placeholder="e.g. Sr.Accountants"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Address</label>
                    <input
                      v-model="address"
                      name="address"
                      type="text"
                      class="form-control address"
                      placeholder="e.g. Lake Street-23"
                    />
                    <span class="form-text"></span>
                  </div>
                </div>

                <div class="cols-3">
                  <div class="form-elem">
                    <label for="" class="form-label">Email</label>
                    <input
                      v-model="email"
                      name="email"
                      type="text"
                      class="form-control email"
                      placeholder="e.g. johndoe@gmail.com"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Phone No:</label>
                    <input
                      v-model="phoneno"
                      name="phoneno"
                      type="text"
                      class="form-control phoneno"
                      placeholder="e.g. 456-768-798, 567.654.002"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Summary</label>
                    <input
                      v-model="summary"
                      name="summary"
                      type="text"
                      class="form-control summary"
                      placeholder="e.g. Doe"
                    />
                    <span class="form-text"></span>
                  </div>
                </div>

                <div class="cols-3">
                  <div class="form-elem">
                    <label for="" class="form-label">Linkedin</label>
                    <input
                      v-model="linkedin"
                      name="linkedin"
                      type="url"
                      class="form-control linkedin"
                      placeholder="e.g. https://www.linkedin.com/username/"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Github</label>
                    <input
                      v-model="github"
                      name="github"
                      type="url"
                      class="form-control github"
                      placeholder="e.g. https://github.com/username/"
                    />
                    <span class="form-text"></span>
                  </div>
                  <div class="form-elem">
                    <label for="" class="form-label">Website</label>
                    <input
                      v-model="website"
                      name="website"
                      type="url"
                      class="form-control website"
                      placeholder="e.g. https://mywebsite.com"
                    />
                    <span class="form-text"></span>
                  </div>
                </div>
              </div>
            </div>

            <div class="cv-form-blk">
              <div class="cv-form-row-title">
                <h3>education</h3>
              </div>

              <div class="row-separator repeater">
                <div class="repeater" data-repeater-list="group-c">
                  <div v-for="(item, index) in educationItems" :key="index" data-repeater-item>
                    <div class="cv-form-row cv-form-row-experience">
                      <div class="cols-3">
                        <div class="form-elem">
                          <label for="" class="form-label">School</label>
                          <input
                            v-model="item.edu_school"
                            name="edu_school"
                            type="text"
                            class="form-control edu_school"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Degree</label>
                          <input
                            v-model="item.edu_degree"
                            name="edu_degree"
                            type="text"
                            placeholder="Bachelor's degree"
                            class="form-control edu_degree"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">City</label>
                          <input
                            v-model="item.edu_city"
                            name="edu_city"
                            type="text"
                            placeholder="Accra"
                            class="form-control edu_city"
                          />
                          <span class="form-text"></span>
                        </div>
                      </div>

                      <div class="cols-3">
                        <div class="form-elem">
                          <label for="" class="form-label">Start Date</label>
                          <input
                            v-model="item.edu_start_date"
                            name="edu_start_date"
                            type="date"
                            class="form-control edu_start_date"
                            id="start-date-input"
                            :max="minDate"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">End Date</label>
                          <input
                            v-model="item.edu_graduation_date"
                            name="edu_graduation_date"
                            type="date"
                            class="form-control edu_graduation_date"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Description</label>
                          <input
                            v-model="item.edu_description"
                            name="edu_description"
                            type="text"
                            placeholder="History"
                            class="form-control edu_description"
                          />
                          <span class="form-text"></span>
                        </div>
                      </div>

                      <button
                        v-if="index >= 1"
                        data-repeater-delete
                        type="button"
                        class="repeater-remove-btn"
                        @click="removeEducationItem(index)"
                      >
                        -
                      </button>
                    </div>
                  </div>
                </div>
                <button
                  type="button"
                  data-repeater-create
                  value="Add"
                  class="repeater-add-btn"
                  @click="addEducationItems"
                >
                  +
                </button>
              </div>
            </div>

            <div class="cv-form-blk">
              <div class="cv-form-row-title">
                <h3>certificates</h3>
              </div>

              <div class="row-separator repeater">
                <div class="repeater" data-repeater-list="group-a">
                  <div v-for="(item, index) in achievements" :key="index" data-repeater-item>
                    <div class="cv-form-row cv-form-row-achievement">
                      <div class="cols-2">
                        <div class="form-elem">
                          <label for="" class="form-label">Title</label>
                          <input
                            v-model="item.achieve_title"
                            name="achieve_title"
                            type="text"
                            class="form-control achieve_title"
                            placeholder="e.g. johndoe@gmail.com"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Description</label>
                          <input
                            v-model="item.achieve_description"
                            name="achieve_description"
                            type="text"
                            class="form-control achieve_description"
                            placeholder="e.g. johndoe@gmail.com"
                          />
                          <span class="form-text"></span>
                        </div>
                      </div>
                      <button
                        v-if="index >= 1"
                        data-repeater-delete
                        type="button"
                        class="repeater-remove-btn"
                        @click="removeAchievementsItem(index)"
                      >
                        -
                      </button>
                    </div>
                  </div>
                </div>
                <button
                  type="button"
                  data-repeater-create
                  value="Add"
                  class="repeater-add-btn"
                  @click="addAchievementsItems"
                >
                  +
                </button>
              </div>
            </div>

            <div class="cv-form-blk">
              <div class="cv-form-row-title">
                <h3>experience</h3>
              </div>

              <div class="row-separator repeater">
                <div class="repeater" data-repeater-list="group-b">
                  <div v-for="(item, index) in experiences" :key="index" data-repeater-item>
                    <div class="cv-form-row cv-form-row-experience">
                      <div class="cols-3">
                        <div class="form-elem">
                          <label for="" class="form-label">Title</label>
                          <input
                            v-model="item.exp_title"
                            name="exp_title"
                            type="text"
                            class="form-control exp_title"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Company / Organization</label>
                          <input
                            v-model="item.exp_organization"
                            name="exp_organization"
                            type="text"
                            class="form-control exp_organization"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Location</label>
                          <input
                            v-model="item.exp_location"
                            name="exp_location"
                            type="text"
                            class="form-control exp_location"
                          />
                          <span class="form-text"></span>
                        </div>
                      </div>

                      <div class="cols-3">
                        <div class="form-elem">
                          <label for="" class="form-label">Start Date</label>
                          <input
                            v-model="item.exp_start_date"
                            name="exp_start_date"
                            type="date"
                            :max="minDate"
                            class="form-control exp_start_date"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">End Date</label>
                          <input
                            v-model="item.exp_end_date"
                            name="exp_end_date"
                            type="date"
                            class="form-control exp_end_date"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Description</label>
                          <input
                            v-model="item.exp_description"
                            name="exp_description"
                            type="text"
                            class="form-control exp_description"
                          />
                          <span class="form-text"></span>
                        </div>
                      </div>

                      <button
                        v-if="index >= 1"
                        data-repeater-delete
                        type="button"
                        class="repeater-remove-btn"
                        @click="removeExperiencesItem(index)"
                      >
                        -
                      </button>
                    </div>
                  </div>
                </div>
                <button
                  type="button"
                  data-repeater-create
                  value="Add"
                  class="repeater-add-btn"
                  @click="addExperiencesItems"
                >
                  +
                </button>
              </div>
            </div>

            <div class="cv-form-blk">
              <div class="cv-form-row-title">
                <h3>projects</h3>
              </div>

              <div class="row-separator repeater">
                <div class="repeater" data-repeater-list="group-d">
                  <div v-for="(item, index) in projects" :key="index" data-repeater-item>
                    <div class="cv-form-row cv-form-row-experience">
                      <div class="cols-3">
                        <div class="form-elem">
                          <label for="" class="form-label">Project Name</label>
                          <input
                            v-model="item.proj_title"
                            name="proj_title"
                            type="text"
                            class="form-control proj_title"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Project link</label>
                          <input
                            v-model="item.proj_link"
                            name="proj_link"
                            type="text"
                            class="form-control proj_link"
                          />
                          <span class="form-text"></span>
                        </div>
                        <div class="form-elem">
                          <label for="" class="form-label">Description</label>
                          <input
                            v-model="item.proj_description"
                            name="proj_description"
                            type="text"
                            class="form-control proj_description"
                          />
                          <span class="form-text"></span>
                        </div>
                      </div>
                      <button
                        v-if="index >= 1"
                        data-repeater-delete
                        type="button"
                        class="repeater-remove-btn"
                        @click="removeProjectsItem(index)"
                      >
                        -
                      </button>
                    </div>
                  </div>
                </div>
                <button
                  type="button"
                  data-repeater-create
                  value="Add"
                  class="repeater-add-btn"
                  @click="addProjectItems"
                >
                  +
                </button>
              </div>
            </div>

            <div class="cv-form-blk">
              <div class="cv-form-row-title">
                <h3>skills</h3>
              </div>

              <div class="row-separator repeater">
                <div class="repeater" data-repeater-list="group-e">
                  <div v-for="(item, index) in skills" :key="index" data-repeater-item>
                    <div class="cv-form-row cv-form-row-skills">
                      <div class="form-elem">
                        <label for="" class="form-label">Skill</label>
                        <input
                          v-model="item.skill"
                          name="skill"
                          type="text"
                          class="form-control skill"
                        />
                        <span class="form-text"></span>
                      </div>

                      <button
                        v-if="index >= 1"
                        data-repeater-delete
                        type="button"
                        class="repeater-remove-btn"
                        @click="removeSkillItem(index)"
                      >
                        -
                      </button>
                    </div>
                  </div>
                </div>
                <button
                  type="button"
                  data-repeater-create
                  value="Add"
                  class="repeater-add-btn"
                  @click="addSkillItems"
                >
                  +
                </button>
              </div>
            </div>
          </form>
        </div>
        <!-- resume preview -->
        <div class="cv-form-blk">
          <div class="sticky-container sticky-resume">
            <PreviewResume />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import PreviewResume from '../resumePreview/index.vue'
import { computed } from 'vue'

export default {
  name: 'BuildResume',
  components: { PreviewResume },
  provide() {
    return {
      userData: computed(() => this.userData)
    }
  },
  data() {
    return {
      avatar: null,
      firstName: '',
      middleName: '',
      lastName: '',
      designation: '',
      address: '',
      email: '',
      phoneno: '',
      summary: '',
      linkedin: '',
      github: '',
      website: '',
      minDate: '',
      edu_graduation_date: '',
      educationItems: [
        {
          edu_school: '',
          edu_degree: '',
          edu_city: '',
          edu_start_date: '',
          edu_graduation_date: '',
          edu_description: ''
        }
      ],
      achievements: [{ achieve_title: '', achieve_description: '' }],
      experiences: [
        {
          exp_title: '',
          exp_organization: '',
          exp_location: '',
          exp_start_date: '',
          exp_end_date: '',
          exp_description: ''
        }
      ],
      projects: [{ proj_title: '', proj_link: '', proj_description: '' }],
      skills: [{ skill: '' }]
    }
  },
  computed: {
    userData() {
      return {
        avatar: this.avatar,
        firstName: this.firstName,
        middleName: this.middleName,
        lastName: this.lastName,
        designation: this.designation,
        address: this.address,
        email: this.email,
        phoneno: this.phoneno,
        summary: this.summary,
        linkedin: this.linkedin,
        github: this.github,
        website: this.website,
        educationItems: this.educationItems,
        achievements: this.achievements,
        experiences: this.experiences,
        projects: this.projects,
        skills: this.skills
      }
    }
  },
  mounted() {
    const now = new Date()
    // Calculate the minimum date as today or in the past
    this.minDate = now.toISOString().substring(0, 10)
  },
  methods: {
    previewImage(e) {
      if (e.target.files[0]) {
        const imgPrev = e.target.files[0]
        if (imgPrev.size > 204800) {
          this.$refs.imgUploadInputRef.value = null
        } else {
          this.avatar = URL.createObjectURL(e.target.files[0])
        }
      } else {
        this.avatar = null
        // clear input reference from field
        this.$refs.imgUploadInputRef.value = null
      }
    },
    addEducationItems() {
      this.educationItems.push({
        edu_school: '',
        edu_degree: '',
        edu_city: '',
        edu_start_date: '',
        edu_description: ''
      })
    },
    removeEducationItem(index) {
      this.educationItems.splice(index, 1)
    },
    addAchievementsItems() {
      this.achievements.push({ achieve_title: '', achieve_description: '' })
    },
    removeAchievementsItem(index) {
      this.achievements.splice(index, 1)
    },
    addExperiencesItems() {
      this.experiences.push({
        exp_title: '',
        exp_organization: '',
        exp_location: '',
        exp_start_date: '',
        exp_end_date: '',
        exp_description: ''
      })
    },
    removeExperiencesItem(index) {
      this.experiences.splice(index, 1)
    },
    addProjectItems() {
      this.projects.push({ proj_title: '', proj_link: '', proj_description: '' })
    },
    removeProjectsItem(index) {
      this.projects.splice(index, 1)
    },
    addSkillItems() {
      this.skills.push({ skill: '' })
    },
    removeSkillItem(index) {
      this.skills.splice(index, 1)
    }
  }
}
</script>

<style>
</style>