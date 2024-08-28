<script setup lang="ts">
import { open } from '@tauri-apps/plugin-dialog';
import {open as openFile} from '@tauri-apps/plugin-shell'

const openVideo = (path: string) => {
		openFile(path).then(() => {
			console.log('Video opened')
		}).catch((error) => {
			console.error(error)
		})
}


const getVideoFilePath = () => {
	open({
			filters: [{
				extensions: ['mp4'],
				name: 'MP4 Files',
			}],
		defaultPath: '../src/assets',
	}).then((res) => {
		console.log(res)
		openVideo(res.path)
	}).catch((error) => {
		console.error(error)
	})
}


</script>

<template>
  <div class="container">
			<button @click="getVideoFilePath">Open a Video</button>

  </div>
</template>
