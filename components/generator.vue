<template>
  <v-container>
    <v-layout
      text-xs-center
      row
      wrap
    >
      <v-flex xs3>
        <v-checkbox
          label='使用a-z'
          v-model='useLower'
        >
        </v-checkbox>
      </v-flex>
      <v-flex xs3>
        <v-checkbox
          label='使用A-Z'
          v-model='useUpper'
        >
        </v-checkbox>
      </v-flex>
      <v-flex xs3>
        <v-checkbox
          label='使用0-9'
          v-model='useNum'
        >
        </v-checkbox>
      </v-flex>
      <v-flex xs3>
        <v-checkbox
          label='使用特殊字符'
          v-model='useSpec'
        >
        </v-checkbox>
      </v-flex>
      <v-flex xs3>
        <v-text-field
            label="长度"
            v-model="length"
            clearable
          ></v-text-field>
      </v-flex>
      <v-flex xs1></v-flex>
      <v-flex xs6>
        <v-text-field
            label="密码生成"
            clearable
            counter
            append-icon='file_copy'
            @click:append="copy"
            @click:clear="clear"
            :hint = 'hint'
            :value = 'result'
            persistent-hint
          ></v-text-field>
      </v-flex>
      <v-flex xs2>
        <v-btn @click="gen">生成</v-btn>
      </v-flex>
        
      
    </v-layout>
  </v-container>
</template>

<script>
  var lower = 'abcdefghijklmnopqrstuvwxyz'
  var upper = 'ABCDEFGHIJKLMNPQRSTUVWXYZ'
  var num = '0123456789'
  var spec = '!@#%&^*-_+=()"{}[]<>'
  export default {
    data () {
      return {
        length: '8',
        useUpper: true,
        useLower: true,
        useNum: true,
        useSpec: true,
        result: '',
        hint: ''
      }
    },
    methods:{
      /* eslint no-console: 0*/
      copy: function() {
        if(this.result.length>0){
          this.hint = '已经复制到剪贴板！'
        }
      },
      clear: function() {
        this.hint = ''
      },
      gen: function() {
        var code = new Array()
        var pwd = new Array()
        if(this.useUpper){
          code.push(upper)
          // code+=upper
        }
        if(this.useLower){
          code.push(lower)
          // code+=lower
        }
        if(this.useNum){
          code.push(num)
          // code+=num
        }
        if(this.useSpec){
          code.push(spec)
          // code+=spec
        }
        
        var truecode = code.join("")
        if(truecode.length>1){
          for(var i=0;i<this.length;i++){
            var pos = Math.round(Math.random()*truecode.length)
            pwd.push(truecode[pos])
          }
        }
        this.hint = ''
        this.result = pwd.join("")
      }
    }
  }
</script>

<style>

</style>
