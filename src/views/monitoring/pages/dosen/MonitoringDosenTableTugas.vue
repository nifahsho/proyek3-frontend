<template>
    <v-row :style="{color: currentTheme.onBackground}">
        <v-col cols="12">
            <p class="text-h4 font-weight-bold">Monitoring APPL 1 - W1 Polymorphism</p>
        </v-col>
        <v-col cols="12">
             <breadcumbs :breadcrumb-items="breadcrumbItems"/>
        </v-col>
        <v-simple-table>
            <template v-slot:default>
                <thead>
                    <tr :style="{background: currentTheme.colorPrimary}">
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">NIM</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Nama</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Rata-rata Progress</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Taks Dikerjakan</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Total Durasi</div>
                        </th>
                        <th class="text-center">
                            <div :style="tableTitleStyle" class="text-subtitle-2">Detail</div>
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
                    <td class="text-capitalize text-body-2 font-weight-light text-center test" :style="{color: currentTheme.onSurface}">{{ subTask.Nim }}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-left" :style="{color: currentTheme.onSurface}">{{ subTask.Nama}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.RataRataProgress}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.TaksDikerjakan}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.TotalDurasi}}</td>
                    <td class="text-capitalize text-body-2 font-weight-light text-center" :style="{color: currentTheme.onSurface}">{{ subTask.Detail}}</td>
                </tr>
             </tbody>
        </template>
    </v-simple-table>
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
            Nim: "181524002",
            Nama: "Alvira Putrina Derajat",
            RataRataProgress: "50%",
            TaksDikerjakan: "3",
            TotalDurasi: "250",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524003",
            Nama: "Ananda Bayu Fauzan",
            RataRataProgress: "60%",
            TaksDikerjakan: "5",
            TotalDurasi: "300",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524004",
            Nama: "Chofief Al Farroqie Ariestotles",
            RataRataProgress: "60%",
            TaksDikerjakan: "4",
            TotalDurasi: "270",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524005",
            Nama: "Dewanto Joyo Pramono",
            RataRataProgress: "50%",
            TaksDikerjakan: "4",
            TotalDurasi: "240",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524006",
            Nama: "Dwinanda Alfauzan Suhando",
            RataRataProgress: "50%",
            TaksDikerjakan: "3",
            TotalDurasi: "150",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524007",
            Nama: "Evan Lokajaya",
            RataRataProgress: "70%",
            TaksDikerjakan: "5",
            TotalDurasi: "340",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524008",
            Nama: "Fajrina Aflaha",
            RataRataProgress: "50%",
            TaksDikerjakan: "4",
            TotalDurasi: "300",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524009",
            Nama: "Fatharani",
            RataRataProgress: "60%",
            TaksDikerjakan: "5",
            TotalDurasi: "300",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524010",
            Nama: "Hafizh Muhammad F",
            RataRataProgress: "60%",
            TaksDikerjakan: "3",
            TotalDurasi: "300",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524012",
            Nama: "Hanifah Sholihat",
            RataRataProgress: "50%",
            TaksDikerjakan: "2",
            TotalDurasi: "200",
            Detail: "Lihat Detail"
          },
          {
            Nim: "181524012",
            Nama: "Hanifah Sholihat",
            RataRataProgress: "50%",
            TaksDikerjakan: "2",
            TotalDurasi: "200",
            Detail: "Lihat Detail"
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
