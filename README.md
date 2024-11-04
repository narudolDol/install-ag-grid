# Installing ag-Grid in Nuxt 3

## Step 1: Install Required Packages

```bash
npm install ag-grid-vue3 ag-grid-community ag-grid-enterprise ag-grid-charts-enterprise
```


## Step 2: Create a Plugin File for ag-Grid
Create a plugin file named ag-grid.ts in the plugins folder of your Nuxt 3 project. This file will register AgGridVue as a global component and configure the AG-Grid license.


```bash
import { defineNuxtPlugin } from '#app'
import { AgGridVue } from 'ag-grid-vue3'
import 'ag-grid-community/styles/ag-grid.css'
import 'ag-grid-community/styles/ag-theme-quartz.css'
import { LicenseManager } from 'ag-grid-enterprise'

const licenseKey = process.env.AG_GRID_LICENSE_KEY || ''
LicenseManager.setLicenseKey(licenseKey)

export default defineNuxtPlugin((nuxtApp) => {
  nuxtApp.vueApp.component('AgGridVue', AgGridVue)
})
```


## Step 3: Set the License Key
If you are using AG-Grid Enterprise, set your license key in the project’s .env file by adding this line:

```bash
AG_GRID_LICENSE_KEY=YOUR_LICENSE_KEY
```

## Step 4: Use AG-Grid

```bash
<template>
  <AgGridVue
    style="width: 100%; height: 500px;"
    class="ag-theme-quartz"
    :columnDefs="columnDefs"
    :rowData="rowData"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue';

const columnDefs = ref([
  { field: 'Column Name' },
  { field: 'Column Data' },
]);

const rowData = ref([
  { 'Column Name': 'Example 1', 'Column Data': 'Data 1' },
  { 'Column Name': 'Example 2', 'Column Data': 'Data 2' },
]);
</script>
```

