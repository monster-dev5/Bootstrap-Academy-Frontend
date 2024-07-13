<template>
  <div>
    <Modal v-if="show">
      <Dialog :dialog="dialog">
        <template #content="{ t }">
          <p class="text-body-1 text-body font-body m-0 mt-box">
            Herzlichen Glückwunsch, du hast die Challenges geschafft. Wenn du Lust hast, Audi sucht DICH als neuen Mitarbeiter:
            <NuxtLink to="https://www.linkedin.com/organization/5626/campaign/1a2cd76b-e391-4aa3-8cfa-d4dd7d7d4589/" class="underline-link w-fit inline-block">
              https://www.linkedin.com/organization/5626/campaign/1a2cd76b-e391-4aa3-8cfa-d4dd7d7d4589/
            </NuxtLink>
          </p>
        </template>
      </Dialog>
    </Modal>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed, ref } from "vue";

export default defineComponent({
  props: {
    codingChallengeId: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const show = ref(true);
    const route = useRoute();
    const router = useRouter();

    const dialog = computed(() => {
      return {
        type: "info",
        heading: "Du hast die Challenge geschafft!",
        body: "",
        primaryBtn: {
          label: "Buttons.Continue",
          onclick: () => location.href = "https://www.linkedin.com/organization/5626/campaign/1a2cd76b-e391-4aa3-8cfa-d4dd7d7d4589/",
        },
        secondaryBtn: {
          label: "Buttons.Close",
          onclick: () => show.value = false,
        },
      };
    });

    return { show, dialog, route };
  },
});
</script>
