<template>
  <a-menu
    id="dddddd"
    v-model:selectedKeys="selectedKeys"
    style="width: 256px"
    mode="inline"
    :openKeys="openKeys"
    @openChange="onOpenChange"
  >
    <a-sub-menu key="sub1">
      <template #title>Рейтинговый матч</template>        
        <p>Набор игровых правил</p>
        <SelectVariant />
        <br />
        <a-button @click="show = !show">
          <span v-show="!show">Начать игру</span>
          <span v-show="show">Остановить поиск</span>
        </a-button>  
    </a-sub-menu>
    <a-sub-menu key="sub2">      
      <template #title>Рейтинговый турнир</template>
      <a-menu-item key="5">Option 5</a-menu-item>
      <a-menu-item key="6">Option 6</a-menu-item>
    </a-sub-menu>   
  </a-menu>
  
</template>

<script>
import { defineComponent, reactive, toRefs } from 'vue';
import SelectVariant from '@/components/SelectVariant'
export default defineComponent({
  components: {
    SelectVariant
  },
  setup() {
    const state = reactive({
      rootSubmenuKeys: ['sub1', 'sub2', 'sub4'],
      openKeys: ['sub1'],
      selectedKeys: [],
    });
    const onOpenChange = openKeys => {
      const latestOpenKey = openKeys.find(key => state.openKeys.indexOf(key) === -1);
      if (state.rootSubmenuKeys.indexOf(latestOpenKey) === -1) {
        state.openKeys = openKeys;
      } else {
        state.openKeys = latestOpenKey ? [latestOpenKey] : [];
      }
    };
    return {
      ...toRefs(state),
      onOpenChange,
    };
  },
});
</script>