<template>
    <v-row :style="{color: currentTheme.onBackground}">
        <v-col cols="12">
            <p class="text-h4 font-weight-bold">Monitoring APPL 1 - W1 Polymorphism</p>
        </v-col>
        <v-col cols="12">
             <breadcumbs :breadcrumb-items="breadcrumbItems"/>
        </v-col>
         <v-col  class="ml-auto pl-13 py-4" cols="0" xs="6" sm="6" md="5" lg="4" xl="3">
            <v-combobox solo  v-model="selected" :items="choices" label="181524012 Alvira Putrina D" :dark="isDark"></v-combobox>
        </v-col>
        <v-col cols="12">
        <v-simple-table>
            <template v-slot:default>
                <thead>
                    <tr :style="{background: currentTheme.colorPrimary}">
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Selesai</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Nama</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Target</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Skala Pemahaman</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Durasi</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Catatan</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Lampiran</div>
                        </th>
                    </tr>
                </thead>
            <tbody :style="{background: currentTheme.surface}">
                <tr
                    v-for="subTask in SubTaskList"
                    :key="subTask.selesai"
                    :style="{pointerEvents: 'none' }"
                    align-center
                >
                    <td class="text-capitalize text-body-2 font-weight-light text-center test" :style="{color: currentTheme.onSurface}">{{ subTask.selesai}}
                        <v-checkbox></v-checkbox>
                    </td>
                    <td class="text-capitalize text-body-2 font-weight-light text-left" :style="{color: currentTheme.onSurface}">{{ subTask.nama}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.target}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.skalapemahaman}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.durasi}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.catatan}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.lampiran}}</td>
                </tr>
             </tbody>
        </template>
    </v-simple-table>
    </v-col>
    </v-row>
</template>

<script>
import { mapGetters } from "vuex"
import Breadcumbs from "@/views/shared/navigation/Breadcumbs"

export default {
  name: "DosenViewTable",
  components: { Breadcumbs },
  props: {
    SubTaskList: {
      type: Array,
      required: false,
      default: () => {
        return [
          {
            nama: "Another Type of Employee",
            target: "50",
            skalapemahaman: "30",
            durasi: "00:30:00",
            catatan: "",
            lampiran: "Link Spreadsheet"
          },
          {
            nama: "Another Type of Employee",
            target: "50",
            skalapemahaman: "30",
            durasi: "00:30:00",
            catatan: "Dalam kasus ini multi-Thread, ketika program di run hasilnya kata Hello JTK 2018 tidak beraturan,ini dikarenakan thread..",
            lampiran: "Link Spreadsheet"
          },
          {
            nama: "Planning Shapes",
            target: "50",
            skalapemahaman: "30",
            durasi: "00:30:00",
            catatan: "",
            lampiran: "Link Spreadsheet"
          },
          {
            nama: "Polymorphic Sorting",
            target: "50",
            skalapemahaman: "30",
            durasi: "00:30:00",
            catatan: "",
            lampiran: "Link Spreadsheet"
          },
          {
            nama: "Timming Searching and Sorting Algorithms",
            target: "50",
            skalapemahaman: "30",
            durasi: "00:30:00",
            catatan: "",
            lampiran: "Link Spreadsheet"
          },
          {
            nama: "Coloring a Moveaible Circle",
            target: "80",
            skalapemahaman: "7",
            durasi: "00:50:00",
            catatan: "",
            lampiran: "Link Spreadsheet"
          },
          {
            nama: "Speed Control",
            target: "100",
            skalapemahaman: "6",
            durasi: "01:02:00",
            catatan: "Dalam kasus ini multi-Thread, ketika program di run hasilnya kata Hello JTK 2018 tidak beraturan,ini dikarenakan thread..",
            lampiran: "Link Spreadsheet"
          }
        ]
      }
    }
  },
  computed: {
    ...mapGetters({
      currentTheme: "theme/getCurrentColor"
    }),
    isMobile () {
      return this.$vuetify.breakpoint.sm || this.$vuetify.breakpoint.xs
    },
    tableTitleStyle () {
      return {
        color: this.currentTheme.colorOnPrimary
      }
    }
  },
  data () {
    return {
      selected: null,
      choices: ["181524002 Alvira Putrina D", "181524004 Ananda Bayu F", "181524004 Chofief Al Farroqie A"],
      breadcrumbItems: [
        {
          text: "Monitoring",
          disabled: false,
          href: ""
        },
        {
          text: "Link 1",
          disabled: false,
          href: ""
        },
        {
          text: "Link 2",
          disabled: true,
          href: ""
        }
      ]
    }
  }
}
</script>

<style scoped>
</style>
