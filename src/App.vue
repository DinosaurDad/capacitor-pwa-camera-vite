<script setup>

import {onMounted} from 'vue'
import {IonApp, IonButton, IonItem, IonLabel, IonPage} from '@ionic/vue'
import {Camera, CameraResultType, CameraSource} from '@capacitor/camera'
import {defineCustomElements} from '@ionic/pwa-elements/loader'

onMounted(async () => {
  await defineCustomElements(window);
})

const snap = async () => {
  const permissions = {
    permissions: ["photos","camera"]
  }

  const options = {
    resultType: CameraResultType.Uri,
    source: CameraSource.Prompt,
    quality: 70,
  }
  await Camera.getPhoto(options)
}

</script>

<template>
  <ion-app>
    <ion-page>
      <ion-item>
        <ion-label>Camera Issue</ion-label>
        <ion-button @click="snap">Snap</ion-button>
      </ion-item>
    </ion-page>
  </ion-app>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
