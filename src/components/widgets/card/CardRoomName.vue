<template>
  <v-card color="#061422">
    <v-card-title>
      <span id="card-title">{{ $t('CardRoomName.title') }}</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-text-field
              dark
              maxlength="10"
              autofocus
              :error-messages="errorMessage"
              v-model="roomName"></v-text-field>
          </v-col>          
        </v-row>
      </v-container>
    </v-card-text>
    <v-card-actions>
      <div class="flex-grow-1"></div>
      <v-btn
        dark
        depressed
        color="#FF5252"
        @click="searchRoom">{{ $t('CardRoomName.next') }}</v-btn>
      <v-btn
        dark
        depressed
        color="#43B581"
        @click="cancel">{{ $t('CardRoomName.cancel') }}</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
  import Vue, { PropType } from 'vue'

  export type DataType = {
    roomName: string,
  }

  export default Vue.extend({
    name: 'CardRoomName',

    props: {
      errorMessage: String,
    },

    data(): DataType {
      return {
        roomName: '',
      }
    },

    methods: {
      searchRoom(): void {
        this.$emit('searchRoom', this.roomName)
      },

      cancel(): void {
        this.$emit('cancel')
      },
    },
  })
</script>

<style scoped>
  #card-title {
    font-size: 16px;
    font-weight: 500;
    color: #FFFFFF;
    opacity: 0.9;
  }   
</style>