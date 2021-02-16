<template lang="pug">
  div.h-100
    div.container.d-flex.justify-content-center.py-4.navbar
      a.px-4.mx-3.btn.btn-lg.btn-outline-primary.wiggle.nav-item(href="#about") about
      a.px-4.mx-3.btn.btn-lg.btn-outline-primary.wiggle.nav-item(href="#projects") projects
      a.px-4.mx-3.btn.btn-lg.btn-outline-primary.wiggle.nav-item(href="#contact") contact
      button.px-4.mx-4.btn.btn-lg.btn-secondary.wiggle-horizontally Resume
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
      div.row(v-for="tool in programingToolBox")
        div.col-2
          p {{tool.name}}
        div.col-10
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

    section.container.pt-5
      div.row
        div.col
          h2#contact.fw-bold Contact
          hr
          form
            div.mb-3
              label.form-label(for="email") Your Email
              input#email.form-control(type="email" placeholder="johndoe@gmail.com" required)
            div.mb-3
              label.form-label(for="message") Message
              textarea#message.form-control(rows="4" required)
            button.btn.btn-primary.btn-lg.px-3(type="button") Send
    footer.container.pt-5
      div.row
        hr
        div.col.d-flex.justify-content-between
          p Contact: tippet2@pdx.edu
          p © 2020 Jordan Tippetts

</template>

<script>


export default {
  data: function () {
    return {
      name: 'Jordan Tippetts',
      aboutDescription: "Hi. I'm a Masters in Computer Science student at Portland State University. I'm interested in Software" +
          " Development, Automation, Cloud Systems, and Database Management Systems. I'm currently working as the End User Support" +
          " Lead in the IT Department at Portland State. I also develop websites using the latest technology in my" +
          " free time time. I few of the things I enjoy are find ways to automate tasks, xkcd comics, and spending time in the" +
          " outdoors.",
      programingToolBox: [
        {
          name: "HTML5",
          progressBarWidth: 100
        },
        {
          name: "CSS3",
          progressBarWidth: 100
        },
        {
          name: "Java",
          progressBarWidth: 85
        },
        {
          name: "Javascript",
          progressBarWidth: 75
        },
        {
          name: "VueJs",
          progressBarWidth: 60
        },
        {
          name: "SASS",
          progressBarWidth: 100
        },
        {
          name: "Pug",
          progressBarWidth: 55
        },
        {
          name: "Google Firebase",
          progressBarWidth: 60
        },
        {
          name: "Spring Boot",
          progressBarWidth: 70
        },
        {
          name: "node.js",
          progressBarWidth: 70
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

#display-name {
  font-family: 'Yanone Kaffeesatz', sans-serif;
  font-size: 150px;
}

main {
  height: 60vh;
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
