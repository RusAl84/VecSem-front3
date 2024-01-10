<style src="vue-d3-network/dist/vue-d3-network.css"></style>
<template>
  <div id="app">
    <q-card class="chatmessages">
      <div class="flexrow">
        <div>
          <q-card-section>
            <div class="text-h6">
              Введите текст для анализа:
            </div>
          </q-card-section>
          <q-card-section>
            <q-input
            filled
            v-model="proc_text"
            type="textarea"
            autogrow
            float-label="Введите текст для анализа"
          /></q-card-section>
          <q-card-section>
            <q-btn color="primary" label="Обработать" @click="onProc" />
          </q-card-section>
        </div>
      </div>
      <q-card-section>
      <d3-network
      :net-nodes="nodes"
      :net-links="links"
      :options="options"
    ></d3-network></q-card-section>
    ></q-card>
    <q-card class="chatmessages">
      <div class="flexrow">
        <div>
          <q-card-section>
            <div class="text-h6">Загрузка модели:</div>
          </q-card-section>
        </div>
        <div>
          <q-card-section>
            <q-uploader
              :url="hostae_uploadaem"
              label="Загрузите модель векторной семантики .model/*"
              square
              flat
              bordered
              single
              @uploaded="fileUploadedM"
              accept=".model, semanticModel/*"
              style="min-width: 900px; max-width: 900px"
            />
          </q-card-section>
        </div>
      </div>
    </q-card>
  </q-page>
  </div>
</template>

<script>
import D3Network from "vue-d3-network";
import { ref } from "vue";
export default {
  components: {
    D3Network,
  },
  data() {
    return {
      proc_text: ref(""),
      optionsT: [0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1],
      threshold: ref(2),
      nodes: ref([
        { id: 1, name: "" },
        { id: 2, name: "" },
      ]),
      links: ref([
        { sid: 1, tid: 2},
        { sid: 2, tid: 1},
      ]),
      options: {
        force: 3000,
        nodeSize: 15,
        nodeLabels: true,
        linkWidth: 5,
      },
    };
  },
};
</script>
<style lang="sass">
.page
  padding-bottom: 10px
  padding-top: 10px
  padding-left: 10px
  padding-r: 10px

.chatmessages
  padding: 10px
  margin: 10px
.flexrowЁ
  display: flex
  flex-flow: row wrap
  justify-content: flex-start
.editorclass
  max-height: 500px
.inputtext
  width: 800px
</style>