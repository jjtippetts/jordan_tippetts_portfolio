<template lang="pug">
  div.h-100
    div.d-flex.justify-content-center.navbar.container-fluid
      a.btn.btn-lg.btn-outline-primary.wiggle.nav-item.px-4.m-3(href="#about") about
      a.btn.btn-lg.btn-outline-primary.wiggle.nav-item.px-4.m-3(href="#projects") projects
      button.btn.btn-lg.btn-outline-primary.wiggle.nav-item.px-4.m-3(data-bs-toggle="modal" data-bs-target="#contactModal") contact
      a.btn.btn-lg.btn-secondary.wiggle-horizontally.px-4.m-4(href="./Jordan_Tippetts_Resume.pdf" target="_blank" rel="noopener") Resume
    main.container.pt-5
      div.row.h-100
        div.col.h-100.d-flex.flex-column.align-content-center.justify-content-center
          h1#display-name.display-1.text-center {{name}}
          p.lead.text-center Programmer & Developer
    section.container.pt-5
      div.row
        div.col
          h2#about.fw-bold About
          hr
          p {{aboutDescription}}
    section.container.pt-5
      div.row
        div.col
          h3.fw-bold Programming Toolbox
          hr
      div.row
        div.col
          div#toolBoxAccordion.accordion.accordion-flush
            div.accordion-item(v-for="(category, index) in programingToolBox")
              h2.accordion-header
                button.accordion-button.border-primary(type="button" data-bs-toggle="collapse" v-bind:data-bs-target="'#category-collapse-' + index" v-bind:class="{collapsed: index !== 0}")
                  h4 {{category.title}}
              div.accordion-collapse.collapse(v-bind:id="'category-collapse-' + index" data-bs-parent="#toolBoxAccordion" v-bind:class="{show: index === 0}")
                div.accordion-body
                  div.row(v-for="tool in category.tools")
                    div.col-3.col-sm-2
                      p {{tool.name}}
                    div.col-9.col-sm-10
                      div.progress(style="height: 25px")
                        div.progress-bar.progress-bar-striped.progress-bar-animated(v-bind:style="{width: tool.progressBarWidth + '%'}", v-bind:class="progressBarColor(tool.progressBarWidth)")
    section.container.pt-5
      h2#projects.fw-bold Recent Projects
      hr
      div.row
        div.col-sm-6.pt-3(v-for="project in recentProjects")
          div.card.border-primary
            div.card-header {{project.header}}
            div.card-body
              h5.card-title {{project.title}}
              p.card-text {{project.description}}
              a.btn.btn-primary.px-5(v-bind:href="project.url" target="_blank" rel="noopener") Visit

    footer.container.pt-5
      div.row
        hr
        div.col.d-flex.justify-content-between
          p Contact: tippet2@pdx.edu
          p © 2020 Jordan Tippetts

    div#contactModal.modal.fade(tabindex="-1")
      div.modal-dialog
        div.modal-content
          div.modal-header
            button.btn-close(type="button" data-bs-dismiss="modal" aria-label="Close")
          div.modal-body
            iframe.w-100(src="https://docs.google.com/forms/d/e/1FAIpQLSeUWkIvdenJJn2GH_P2qu_z7--eyDqsag9kRBDw9gsjiYXKJA/viewform?embedded=true" height="675" frameborder="0" marginheight="0" marginwidth="0") Loading…
          div.modal-footer
            button.btn.btn-primary(type="button" data-bs-dismiss="modal") Close

</template>

<script>

export default {
  data: function () {
    return {
      name: 'Jordan Tippetts',
      aboutDescription: "Hi. I'm a Masters in Computer Science student at Portland State University. I'm interested in Software" +
          " Development, Automation, Cloud Systems, and Database Management Systems. I'm currently working as the End User Support" +
          " Lead in the IT Department at Portland State. I also develop websites using the latest technology in my" +
          " free time time. I few of the things I enjoy are automating boring tasks, xkcd comics, and spending time in the" +
          " outdoors.",
      programingToolBox: [
        {
          title: "Backend Languages",
          tools: [
            {
              name: "Java",
              progressBarWidth: 90
            },
            {
              name: "C++",
              progressBarWidth: 75
            },
            {
              name: "C",
              progressBarWidth: 60
            },
            {
              name: "Python",
              progressBarWidth: 80
            }
          ]
        },
        {
          title: "Frontend Languages",
          tools: [
            {
              name: "Javascript",
              progressBarWidth: 80
            },
            {
              name: "HTML5",
              progressBarWidth: 100
            },
            {
              name: "CSS3",
              progressBarWidth: 100
            },
            {
              name: "Vue",
              progressBarWidth: 70
            },
            {
              name: "typescript",
              progressBarWidth: 40
            }
          ]
        },
        {
          title: "Web DevelopmentTools",
          tools: [
            {
              name: "SASS",
              progressBarWidth: 100
            },
            {
              name: "Pug",
              progressBarWidth: 60
            },
            {
              name: "Google Firebase",
              progressBarWidth: 80
            },
            {
              name: "Spring Boot",
              progressBarWidth: 70
            },
            {
              name: "node.js",
              progressBarWidth: 75
            }
          ]
        },
        {
          title: "Databases",
          tools: [
            {
              name: "Postgresql",
              progressBarWidth: 90
            },
            {
              name: "Google Firestore",
              progressBarWidth: 80
            },
            {
              name: "Google BigQuery",
              progressBarWidth: 70
            },
            {
              name: "Sqlite",
              progressBarWidth: 75
            },
            {
              name: "JPA",
              progressBarWidth: 60
            }
          ]
        }
      ],
      recentProjects: [
        {
          header: "Web Development",
          title: "Nature Tech Landscape Services",
          description: "Fully custome website for a local company. Built using HTML, CSS, SASS, PHP, and Bootstrap",
          url: "http://naturetechlandscapeservices.com/"
        },
        {
          header: "Web Development",
          title: "Smart Living",
          description: "Full Stack Project for developing diet plans. Uses Spring Ecosystem, H2 database, JPA, and Bootstrap",
          url: "https://smart-living.herokuapp.com/"
        }
      ]
    }
  },
  props: {
    msg: String
  },
  methods: {
    progressBarColor(progressBarWidth) {
      if (progressBarWidth <= 40) {
        return "bg-danger"
      } else if (progressBarWidth > 40 && progressBarWidth <= 60) {
        return "bg-warning"
      } else if (progressBarWidth > 60 && progressBarWidth <= 80) {
        return "bg-primary"
      } else {
        return "bg-success"
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Yanone+Kaffeesatz:wght@500&display=swap');

main {
  height: 60vh;
  #display-name {
    font-family: 'Yanone Kaffeesatz', sans-serif;
    @include font-size(150px);
  }
}

@keyframes wiggle {
  20% {
    transform: translateY(-13%);
  }
  40% {
    transform: translateY(13%);
  }
  60% {
    transform: translateY(-7%);
  }
  80% {
    transform: translateY(7%);
  }
}

.wiggle:hover {
  animation: wiggle .75s ease-in-out;
  animation-delay: 0s;
}

@keyframes wiggle-horizontally {
  20% {
    transform: rotate(15deg);
  }
  40% {
    transform: rotate(-15deg);
  }
  60% {
    transform: rotate(15deg);
  }
  80% {
    transform: rotate(-15deg);
  }
}

.wiggle-horizontally:hover {
  animation: wiggle-horizontally .75s ease-in-out;
  animation-delay: 0s;
}
</style>