<template>
  <div>
    <register-command
      name="generateData"
      :config="generateDataCommandConfig"
      extend="copy"
    />
    <register-command
      name="downloadImage"
      :config="downloadImageCommandConfig"
      extend="copy"
    />
  </div>
</template>

<script>
import { RegisterCommand } from '../index'

export default {
  name: 'CustomCommand',

  components: {
    RegisterCommand,
  },

  inject: ['root'],

  props: ['save', 'download'],

  data() {
    const { propsAPI } = this.root
    const { save, download } = this
    return {
      generateDataCommandConfig: {
        queue: false, // 是否进入列队，默认为 true
        enable(/* editor */) {
          // 命令是否可用
          return true
        },
        execute(/* editor */) {
          // 正向命令逻辑
          console.log('정방향 명령 실행')
          const data = propsAPI.save()
          console.log(data)
          console.log(JSON.stringify(data))
          save(data)
          alert(JSON.stringify(data))
        },
        back(/* editor */) {
          // 反向命令逻辑
          console.log('역방향 명령 실행')
        },
      },
      downloadImageCommandConfig: {
        queue: false,
        enable() {
          return true
        },
        execute() {
          download()
        },
        back() {},
      },
    }
  },
}
</script>
