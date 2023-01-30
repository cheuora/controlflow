<template>
  <toolbar class="toolbar">
    <template v-if="!readOnly">
      <toolbar-button command="undo" text="undo" />
      <toolbar-button command="redo" text="redo" />
      <toolbar-button command="copy" text="복사" />
      <toolbar-button command="paste" text="붙여넣기" />
      <div class="split"></div>
    </template>
    <toolbar-button command="zoomIn" icon="zoom-in" text="zoomIn" />
    <toolbar-button command="zoomOut" icon="zoom-out" text="zoomOut" />
    <toolbar-button command="autoZoom" icon="fit" text="autoZoom" />
    <toolbar-button command="resetZoom" icon="actual-size" text="resetZoom" />
    <template v-if="!readOnly">
      <div class="split"></div>
      <toolbar-button command="toBack" icon="to-back" text="to back" />
      <toolbar-button command="toFront" icon="to-front" text="to front" />
      <toolbar-button command="addGroup" icon="group" text="그룹" />
      <toolbar-button command="unGroup" icon="ungroup" text="그룹취소" />
      <toolbar-button command="selectAll" icon="select-all" text="모두선택" />
      <toolbar-button command="multiSelect" icon="select" text="선택" />
      <div class="split"></div>
      <toolbar-button command="delete" text="삭제" label="데이터저장" />
      <toolbar-button command="clear" icon="clear" text="Clear" />
    </template>
    <!-- right toolbar button -->
    <div class="pull-right">
      <toolbar-button
        command="generateData"
        icon="save"
        text="데이터생성"
        label="데이터저장"
      />
      <toolbar-button
        command="downloadImage"
        icon="image"
        text="이미지 다운로드"
        label="이미지 다운로드"
      />
      <button @click.prevent="handleToggleReadOnly">
        {{ readOnly ? '편집모드' : '읽기전용' }}
      </button>
    </div>
  </toolbar>
</template>

<script>
import { Toolbar } from '../index'
import ToolbarButton from './ToolbarButton'

export default {
  name: 'FlowToolbar',

  components: {
    Toolbar,
    ToolbarButton,
  },

  props: ['chartData', 'toggleReadOnly', 'readOnly'],

  methods: {
    generateData() {
      console.log(JSON.stringify(this.chartData))
    },
    handleToggleReadOnly() {
      // ugly
      this.$parent.$parent.$parent.$emit('toggle-read-only')
    },
  },
}
</script>

<style lang="less">
.toolbar {
  display: flex;
  align-items: center;
  height: 27px;

  .split {
    width: 10px;
    height: 100%;
    border-right: 1px solid #eee;
    margin-right: 10px;
  }

  .pull-right {
    display: flex;
    align-items: center;
    margin-left: auto;
  }

  .command {
    display: flex;
    color: #333;

    i {
      display: block;
      width: 27px;
      height: 27px;
      margin: 0 6px;
      padding-top: 10px;
      text-align: center;
      border: 1px solid #fff;
      cursor: pointer;
    }

    span {
      display: block;
      font-size: 12px;
      padding-top: 10px;
      margin-left: -6px;
      padding-right: 6px;
      line-height: 20px;
      cursor: pointer;
    }

    &:hover {
      color: #1890ff;
    }
  }

  .disable {
    color: rgba(0, 0, 0, 0.25);
    i {
      cursor: not-allowed;
    }

    span {
      cursor: not-allowed;
    }

    &:hover {
      color: rgba(0, 0, 0, 0.25);
    }
  }
}
</style>
