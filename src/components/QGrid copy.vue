<template>
  <q-table
    :rows="data"
    :columns="columns"
    v-model:pagination="pagination"
    @request="onRequest"
    row-key="codendereco"
  >
  </q-table>
</template>

<script>
import { defineComponent, computed } from "vue";

export default defineComponent({
  name: "QGrid",

  props: {
    data: { type: Array, default: () => [] },
    columns: { type: Array, default: () => [] },
    pagination: { type: Object },
  },
  setup(props) {
    const pagination = computed({
      get: () => {
        console.log("carai da pag", props.pagination);
        return props.pagination;
      },
      set: (val) => {},
    });

    return {
      pagination,
    };
  },

  methods: {
    onRequest(props) {
      this.$emit("OnRequest", props.pagination);
    },
  },

  emits: ["OnRequest"],
});
</script>

<style scoped></style>
