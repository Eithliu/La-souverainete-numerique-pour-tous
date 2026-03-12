<script setup lang="ts">
import { computed, ref } from "vue";
import ButtonChoice from "./ButtonChoice.vue";

const european = {
  title: "Le choix européen",
  content:
    "L’Europe a des règles de protection des données, stocker ses données en Europe est donc un choix de protection de vie privée numérique",
};
const antiHegemony = {
  title: "Le choix anti-hégémonie",
  content: `Sans pubs
  Sans trackers
  Donc sans GAFAM (qui rejoint du coup le choix européen)`,
};
const ecologic = {
  title: "Le choix écologique",
  content: `Choisir des appareils et services durables
  Choisir européen permet d’avoir des serveurs physiquement plus près qu’à l’autre bout du monde, donc plus écolos
  Un appareil qu’on peut réparer est un appareil qu’on ne jette pas
  Limiter, voire supprimer l’utilisation des IA génératives, extrêmement énergivores
  Des hébergeurs peuvent aussi être écologiques (exemple : infomaniak)`,
};
const ethical = {
  title: "Le choix éthique",
  content: `Des appareils où l’humain et la nature sont respectés au cours de la chaîne de fabrication
  Des clouds respectueux de l’environnement`,
};
const free = {
  title: "Le choix libre",
  content: `L’open-source est motivé par la notion de partage, de liberté et de protection de la vie privée numérique
  Un peu à croisée de tous les autres choix.`,
};

type Choice = "european" | "ethical" | "anti-hegemony" | "ecologic" | "free";

const shownChoice = ref<Choice>(undefined);

const europeanChoice = useChoiceShown("european");
const ethicalChoice = useChoiceShown("ethical");
const antiHegemonyChoice = useChoiceShown("anti-hegemony");
const ecologicChoice = useChoiceShown("ecologic");
const freeChoice = useChoiceShown("free");

function useChoiceShown(choice: Choice) {
  return computed({
    get: () => shownChoice.value === choice,
    set() {
      shownChoice.value = choice;
    },
  });
}
</script>

<template>
  <h2>Pourquoi la souveraineté numérique ? (et autre choix sous-jacents)</h2>
  <ul class="choix">
    <ButtonChoice
      v-model:choice-shown="europeanChoice"
      :title="european.title"
      :content="european.content"
    />
    <ButtonChoice
      v-model:choice-shown="ethicalChoice"
      :title="ethical.title"
      :content="ethical.content"
    />
    <ButtonChoice
      v-model:choice-shown="antiHegemonyChoice"
      :title="antiHegemony.title"
      :content="antiHegemony.content"
    />
    <ButtonChoice
      v-model:choice-shown="ecologicChoice"
      :title="ecologic.title"
      :content="ecologic.content"
    />
    <ButtonChoice v-model:choice-shown="freeChoice" :title="free.title" :content="free.content" />
  </ul>
</template>

<style>
.choix {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  justify-content: center;
}

.choice-item {
  border: 1px solid lightgrey;
  padding: 1rem 1.2rem;
}
</style>
