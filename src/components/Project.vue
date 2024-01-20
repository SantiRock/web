<script setup>
import { ref, computed } from "vue";
import { projectsapi } from "./projectsapi"

const projects = ref(projectsapi)
const hideProjects = ref(false)
let selectedTag = ref(null)

const filteredProjects = computed(() => {
  if (selectedTag.value === null) {
    return projects.value;
  }

  return projects.value.filter(project => project.tags.includes(selectedTag.value))

})

function filterProjects(tag) {
  selectedTag.value = tag;
}


function projectsColor(isHover) {
    var items = document.querySelectorAll('.project_container');

    items.forEach(function(item) {
        item.style.outline = isHover ? '2px solid white' : '1px solid grey';
    })
}

</script>

<template>
    <div class="projects_container" id="projects">
      <h2 class="projects_title" @mouseover="projectsColor(true)" @mouseout="projectsColor(false)">Proyectos</h2>
      <div class="projects_btns_container">
        <button class="projects_btn" @click="filterProjects('react')">React</button>
        <button class="projects_btn" @click="filterProjects('vanilla')">Vanilla</button>
        <button class="projects_btn" @click="filterProjects('html')">HTML</button>
        <button class="projects_btn" @click="filterProjects('solid')">Solid</button>
        <button class="projects_btn" @click="filterProjects('api')">Api</button>
        <button class="projects_btn" @click="filterProjects(null)">All</button>
      </div>

      <ul class="projects_project_container">
        <li v-for="project in filteredProjects" :key="project.id" class="project_container">
          <a class="project_link" :href="project.link" target="_blank">
            <p class="project_title">{{ project.title }}, {{ project.fecha }}</p>
            <div class="project_card">
              <img class="project_img" :src="project.image" :alt="project.title"/>
              <p class="project_description"> {{ project.concepto }}</p>
            </div>
            <p class="project_stack">Stack: {{ project.stack }}</p>
          </a>
        </li>
      </ul>
    </div>
    <div class="linea_container"><div class="linea"></div>  </div>
</template>

<style>
.projects_container {
    margin: auto; 
    margin-bottom: 10px;
    padding: 21px 35px;
    max-width: 1280px;
    min-width: 320px;
}

.projects_title {
    width: fit-content;
    font-size: 24px;
    font-style: italic;
    font-weight: lighter;
    cursor: url('data:./cursor/circulolinea.png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAGlQTFRFAAAAseLRseLSsuLSseLSseHSsuHSseHRsOHQpNvIsuHSsuHSsuLSseHRotHRktu2suHSqtWqmczMsuLRseLSseLSseHSsuLRseLRseHRsuHSsuLRsuDRseHSsuLRmczMseHSsuLSseHRyrOKtAAAACN0Uk5TACpYX15kX1YpBk9gZk4EA2MCBFBlYShXV2BWYihPZAJhTWSrrDvsAAAAh0lEQVR4nG3Q6RaCIBQE4CmELK6Ca2Jq5vs/ZLh1Ypl/fAcO9w6w5nJlCeeJuKU4c39IOiKzfDel6S+82O45ZrW0WNUu1pn9oyEvTYunb0QdRIgGJkQJHaKOY/R5FCMj9UiD4V8DMPpo10TOXZvUWlPh6PTeCy3H+aT5o37dt51gy8JMP2zHL8u1EeCxPg+TAAAAAElFTkSuQmCC'), auto;
}

.projects_btns_container {
  display: flex;
  justify-content: space-between;
  max-width: 375px;
  margin: auto;
  margin-top: 17px;
  margin-bottom: 21px;
}

.projects_btn {
  padding: 5px 5px;
  background-color: rgb(65, 65, 65);
  border-radius: 7px;
  cursor: none;
}

.projects_btn:hover {
  transform: scale(1.01);
  background-color: var(--verde-oscuro);
  border: 1px solid white;

}

.projects_project_container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 27px;
}

.project_container {
  width: 80vw;
  padding: 7px;
  border: 1px solid grey;
  background-color: var(--verde-oscuro);
  border: 1px solid grey;
  border-radius: 10px;
  transition: transform 0.5s ease;
}

.project_container:hover {
  transform: scale(1.05);
  border: 2px solid white;
}

.project_link {
  color: white;
  text-decoration: none;
  cursor: url('data:./cursor/circulonegro.png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAMAAAC6V+0/AAAAAXNSR0IB2cksfwAAAAlwSFlzAAALEwAACxMBAJqcGAAAALdQTFRFAAAAqtjKos7Am8W4epyUY356nsi6os3Aq9fJpNvInci7cZCKGB8mAAALcpKMnsm8otHRktu2rdzMFBoiFx4lrt3OqtWqr97OmczMm8W4FBoiFx4lnMe6cI+Ic5OMqdfKo8/BGiEooczAmsS3nMa6eJmSepyTZH56ZIB6nci6n8m8oMy/GyMqoMy9cZGLdJONqtjJm8a5GSAnm8W5sN7PmczMdJSMdZWOnce6nMe6fJ6WY356n8q9Gh1AiAAAAD10Uk5TAGnb7ez57thnDsbx///xwgsH9/7++Qb5Csn9/cTz82Xa/9nu7/Dx+Pjv8dr/1vP0Y8X+wvsF8vLA7u368ILNhkAAAACiSURBVHicbdDXEoIwEAXQVUFREwWkWSn2ggJiA///uwxBGZNw33JmM5tcgCKNZkuSZandUeCXbq+PMA0aDNXSNH2EqximRed0zMR2CI4nLE5nZMccc1m44CEe/QCWvGG8grWIG9iKuKvH2ut7EQ9wFJ50CkE583iJAGKDteRK/q6aLKZaUZNl/80m6a0s1Inv/nfH46lV3bvBK8vz7B1G9PgB9OoX5Dj9cg0AAAAASUVORK5CYII='), pointer;
}

.project_title {
  font-size: 16px;
  font-style: italic;
  font-weight: lighter;
}

.project_card {
  display: flex;
  gap: 13px;
  margin: 13px 0; 
}

.project_img {
  width: 120px;
  height: 120px;
  border-radius: 5px;
}

.project_description {
  font-size: 14px;
  line-height: 1.5;
}

.project_stack {
  font-size: 12px;
}

@media screen and (min-width: 380px) {
  .projects_btn {
    padding: 5px 7px;
  }
}

@media screen and (min-width: 692px) {
  .project_container {
    width: 40vw;
  }
}

@media screen and (min-width: 700px) {
  .projects_title {
    padding-left: 10px;
    font-size: 26px;
  }
}

@media screen and (min-width: 900px) {
  .projects_title {
    padding-left: 40px;
    font-size: 36px;

  }
  
}

@media screen and (min-width: 1010px) {
  .projects_container {
    padding: 21px 0;
  }
  
  .project_container {
    width: 290px;
  }


}

</style>

