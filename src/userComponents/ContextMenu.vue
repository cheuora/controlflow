<template>
  <context-menu class="contextMenu">
    <node-menu>
      <menu-li command="copy" text="복사" />
      <menu-li command="delete" text="삭제" />
    </node-menu>
    <edge-menu>
      <menu-li command="delete" text="삭제" />
    </edge-menu>
    <group-menu>
      <menu-li command="copy" text="복사" />
      <menu-li command="delete" text="삭제" />
      <menu-li command="unGroup" icon="ungroup" text="그룹해제" />
    </group-menu>
    <multi-menu>
      <menu-li command="copy" text="복사" />
      <menu-li command="paste" text="붙여넣기" />
      <menu-li command="addGroup" icon="group" text="그룹" />
      <menu-li command="delete" text="삭제" />
    </multi-menu>
    <canvas-menu>
      <menu-li command="undo" text="undo" />
      <menu-li command="redo" text="redo" />
      <menu-li command="pasteHere" icon="paste" text="여기에 붙여넣기" />
    </canvas-menu>
  </context-menu>
</template>

<script>
import {
  NodeMenu,
  EdgeMenu,
  GroupMenu,
  MultiMenu,
  CanvasMenu,
  ContextMenu,
} from '../index'
import MenuLi from './ContextMenuItem'

export default {
  name: 'EditorContextMenu',
  components: {
    NodeMenu,
    EdgeMenu,
    GroupMenu,
    MultiMenu,
    CanvasMenu,
    ContextMenu,
    MenuLi,
  },
}
</script>

<style lang="less">
.contextMenu {
  display: none;
  overflow: hidden;
  font-size: 12px;
  background: #fff;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
}

.contextMenu .command.disable .item {
  color: rgba(0, 0, 0, 0.25);
  cursor: auto;
}

.contextMenu .command.disable .item:hover {
  background: #fff;
}

.contextMenu .item {
  display: flex;
  align-items: center;
  padding: 5px 12px;
  cursor: pointer;
  transition: all 0.3s;
  user-select: none;
}

.contextMenu .item:hover {
  background: #e6f7ff;
}

.contextMenu .item i {
  margin-right: 8px;
  margin-top: 3px;
}
</style>
