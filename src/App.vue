<script setup lang="ts">
import { computed, ref } from "vue";
import Questions from "./components/Questions.vue";
import Why from "./components/Why.vue";
import SmallSteps from "./components/SmallSteps.vue";
import MySteps from "./components/MySteps.vue";

const count = ref(0);
const showPage = ref<Page>(undefined);

type Page = "quiz" | "choices" | "small-steps" | "my-small-steps";

const quizPageShown = usePageShown("quiz");
const choicesPageShown = usePageShown("choices");
const smallStepsPageShown = usePageShown("small-steps");
const mySmallStepsPageShown = usePageShown("my-small-steps");

function usePageShown(page: Page) {
  return computed({
    get: () => showPage.value === page,
    set() {
      showPage.value = page;
    },
  });
}

const questions = [
  "J'utilise Google Chrome",
  "J'utilise un compte Gmail/YouTube",
  "J'utilise Notion ou OneNote ou Google Docs",
  "J'ai un compte sur l'un de ces réseaux: Facebook, Instagram, Twitter, Snapchat, WhatsApp",
  "J'ai un ordinateur (principal) sous Windows ou MacOS",
  "J'ai une carte Visa ou Mastercard",
];

const listGoogleSearch = [
  {
    label: "Ecosia",
    link: "https://ecosia.org",
    logo: "../../public/ecosia.png",
  },
  {
    label: "DuckDuckGo",
    link: "https://duckduckgo.com",
    logo: "../../public/duckduckgo.png",
  },
  {
    label: "Qwant",
    link: "https://www.qwant.com/?l=fr",
    logo: "../../public/qwant.png",
  },
  {
    label: "SearXNG",
    link: "https://docs.searxng.org/",
    logo: "../../public/searxng.png",
  },
  {
    label: "Mojeek",
    link: "https://www.mojeek.com/",
    logo: "../../public/mojeek.png",
  },
];

const listGoogleChrome = [
  {
    label: "Firefox",
    link: "https://mozilla.org",
    logo: "../../public/firefox.png",
  },
  {
    label: "Zen Browser",
    link: "https://zen-browser.app/",
    logo: "../../public/zen.png",
  },
];

const listGmail = [
  {
    label: "Proton Mail",
    link: "https://mail.proton.me/",
    logo: "../../public/protonmail.png",
  },
  {
    label: "Infomaniak Mail",
    link: "https://www.infomaniak.com/fr",
    logo: "../../public/infomaniak.png",
  },
  {
    label: "Zaclys ZMail",
    link: "https://www.zaclys.com/zmail/",
    logo: "../../public/zaclysmail.svg",
  },
  {
    label: "Posteo",
    link: "https://posteo.de/fr",
    logo: "../../public/posteo.png",
  },
];

const listCalendar = [
  {
    label: "Framagenda",
    link: "https://framagenda.org/login",
    logo: "../../public/framagenda.png",
  },
  {
    label: "Proton Calendar",
    link: "https://proton.me/fr/calendar",
    logo: "../../public/protoncalendar.png",
  },
];

const listMessaging = [
  {
    label: "Signal",
    link: "https://signal.app",
    logo: "../../public/signal.png",
  },
  {
    label: "Treebal",
    link: "https://www.treebal.green/",
    logo: "../../public/treebal.png",
  },
];

const listVideo = [
  {
    label: "NewPipe",
    link: "https://newpipe.net/",
    logo: "../../public/newpipe.png",
  },
  {
    label: "Peertube",
    link: "https://sepiasearch.org/",
    logo: "../../public/peertube.png",
  },
];

const listRs = [
  {
    label: "Mastodon",
    link: "https://joinmastodon.org/fr",
    logo: "../../public/mastodon.png",
  },
];

const listNotes = [
  {
    label: "Obsidian",
    link: "https://obsidian.md/",
    logo: "../../public/obsidian.png",
  },
  {
    label: "Anytype",
    link: "https://anytype.io/",
    logo: "../../public/anytype.png",
  },
];
</script>

<template>
  <header>
    <title>La souveraineté numérique chez soi</title>
  </header>
  <main>
    <nav>
      <ul class="navigation-menu">
        <li>
          <button @click="quizPageShown = true">Quiz</button>
        </li>
        <li>
          <button @click="choicesPageShown = true">Pourquoi</button>
        </li>
        <li>
          <button @click="smallStepsPageShown = true">Les petits pas</button>
        </li>
        <li>
          <button @click="mySmallStepsPageShown = true">Mes petits pas</button>
        </li>
      </ul>
    </nav>
    <h1>La souveraineté numérique chez soi</h1>
    <h2>La MeJ qui te fait reprendre la main sur tes données</h2>
    <div class="separator" />
    <Questions :questions v-if="quizPageShown" @like="count++" @dislike="" />
    <Why v-if="choicesPageShown" />
    <div v-if="smallStepsPageShown" class="small-steps">
      <h2>Par quoi remplacer les outils ?</h2>
      <SmallSteps
        :list="listGoogleSearch"
        text="Google Search"
        logo="../../public/googlesearch.png"
      />
      <SmallSteps :list="listGoogleChrome" text="Google Chrome" logo="../../public/google.png" />
      <SmallSteps :list="listGmail" text="Gmail" logo="../../public/gmail.png" />
      <SmallSteps :list="listCalendar" text="Google Agenda" logo="../../public/googleagenda.png" />
      <SmallSteps :list="listMessaging" text="WhatsApp" logo="../../public/whatsapp.png" />
      <SmallSteps :list="listVideo" text="YouTube" logo="../../public/youtube.png" />
      <SmallSteps :list="listRs" text="Facebook" logo="../../public/facebook.png" />
      <SmallSteps :list="listNotes" text="Notion" logo="../../public/notion.png" />
    </div>
    <MySteps v-if="mySmallStepsPageShown" />
  </main>
</template>

<style>
* {
  font-family: Roboto, Arial, sans-serif;
  font-size: 16px;
  color: rgb(86 86 92);

  h1,
  h2,
  h3 {
    padding: 0;
    margin: 0;
  }
}

.separator {
  border-bottom: solid 1px grey;
}

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 15px;
}

.small-steps {
  margin: 15px auto;
}

nav {
  display: flex;
}

.navigation-menu {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.navigation-menu li:active,
.navigation-menu li:link {
  border-bottom: 1px solid rgb(86 86 92);
}

button {
  border: none;
  background: transparent;
  cursor: pointer;
}

h1,
h2 {
  text-align: center;
}

h1 {
  padding: 1rem;
  font-size: 24px;
}

h2 {
  padding: 0.8rem;
  font-size: 20px;
}

.show-result {
  padding: 0.8rem 1.5rem;
  border: none;
  background: #5e6c84;
  color: #fff;
  border-radius: 5px;
  width: fit-content;
  margin: auto;
  cursor: pointer;
}

.navigation {
  display: flex;
  justify-content: flex-end;
}

.icon {
  width: 40px;
  cursor: pointer;
}
</style>
