<template>
  <div class="mainTitle">
    <div class="title">主标题</div>
    <div class="wrapper">
      <baseItem label="显示">
        <el-checkbox
          v-model="dataInfo.show"
          @change="changeFun('title','show',dataInfo.show)"
          :disabled="cShowDisabled"
        ></el-checkbox>
      </baseItem>
    </div>
    <div class="wrapper">
      <baseItem label="文本">
        <el-input
          v-model="dataInfo.text"
          size="mini"
          @change="changeFun('title','text',dataInfo.text)"
          :disabled="cDisabled"
        ></el-input>
      </baseItem>
    </div>

    <div class="wrapper">
      <baseItem label="x方向">
        <el-select
          v-model="dataInfo.x"
          placeholder="请选择水平方向"
          @change="changeFun('title','x',dataInfo.x)"
          size="mini"
          :disabled="cDisabled"
        >
          <el-option
            v-for="item in xDirections"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          ></el-option>
        </el-select>
      </baseItem>
    </div>
    <div class="wrapper">
      <baseItem label="y方向">
        <el-select
          v-model="dataInfo.y"
          placeholder="请选择垂直方向"
          @change="changeFun('title','y',dataInfo.y)"
          size="mini"
          :disabled="cDisabled"
        >
          <el-option
            v-for="item in yDirections"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          ></el-option>
        </el-select>
      </baseItem>
    </div>
    <div class="wrapper">
      <baseItem label="样式">
        <settingDialog
          :dataInfo="dataInfo"
          :disabled="cDisabled"
          @changeColorFont="changeColorFontFun"
          attrs="title"
          :width="70"
          attrsKey="textStyle"
        ></settingDialog>
      </baseItem>
    </div>
  </div>
</template>

<script>
import baseItem from "../baseItem";
import settingDialog from "../settingDialog";
import { defaultTtileKeys, fontStyleOptions, fontFamilyOptions, xDirections, yDirections } from "../commonData/commonData";
import componentsMixins from "../mixins/component";
import { clearValues } from "../../../utils/utils";
export default {
  name: "mainTitle",
  mixins: [componentsMixins],
  components: {
    baseItem,
    settingDialog
  },
  data () {
    return {
      dataInfo: clearValues(defaultTtileKeys),
      fontStyleOptions,
      fontFamilyOptions,
      yDirections,
      xDirections
    };
  },
  methods: {
    changeColorFontFun (attrs, props, value) {
      this.changeFun(attrs, props, value);
    }
  }
};
</script>

<style lang="scss" scoped>
.wrapper {
  margin-bottom: 5px;
  &:last-child {
    margin-bottom: 0;
  }
}
</style>
