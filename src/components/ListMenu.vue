<template>
  <a-space direction="vertical">
    <a-menu
      id="dddddd"
      v-model:selectedKeys="selectedKeys"
      style="width: 260px"
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
          <span v-show="show">Остановить поиск <sync-outlined spin/></span>
        </a-button>        
      </a-sub-menu>
      <a-sub-menu key="sub2">      
        <template #title>Рейтинговый турнир</template>
      </a-sub-menu>   
    </a-menu>
  </a-space>
  <br/> 
  <a-space>
    Никнейм
    <a-dropdown :trigger="['click']" placement="topRight">
      <a-button>
        <template #icon><setting-filled/></template>
      </a-button>
      <template #overlay>
        <a-menu>
          <a-menu-item>
            Статус:
          </a-menu-item>
          <a-menu-item>
            Помощь
          </a-menu-item>           
        </a-menu>
      </template>
    </a-dropdown>
  </a-space>
</template>

<script>
import { defineComponent, reactive, toRefs } from 'vue';
import { SyncOutlined, SettingFilled} from '@ant-design/icons-vue';
import SelectVariant from '@/components/SelectVariant'
export default defineComponent({
  components: {
    SelectVariant, SyncOutlined, SettingFilled
  },
  setup() {
    const state = reactive({
      rootSubmenuKeys: ['sub1', 'sub2' ],
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