<template>
    <ion-page>
        <ion-header>
            <ion-row class="ion-align-items-center">
                <ion-col size="3">
                    <a href="/kolam">
                        <font-awesome-icon icon="fa-solid fa-angle-left" style="margin-left: 10%; font-size: 30px;"/>
                    </a>
                </ion-col>
                <ion-col>
                    <h1>Registrasi Kolam</h1>
                </ion-col>
            </ion-row>
        </ion-header>

        <ion-content :fullscreen="true">
            <ion-item class="input">
                <ion-label position="stacked" class="label-input">Nama Kolam</ion-label>
                <ion-input type="text" v-model="nama" name="lokasiName" placeholder="Kolam 1"></ion-input>
            </ion-item>
            <ion-item class="input">
                <ion-label position="stacked" class="label-input">Lokasi Kolam</ion-label>
                <ion-input v-model="lokasi" name="lokasiVar" placeholder="Blok A"></ion-input>
            </ion-item>
            <ion-item>
                <ion-label position="stacked" class="label-input-select">Material Kolam</ion-label>
                <ion-select v-model:value="material" placeholder="Tanah">
                    <ion-select-option value="Tanah">Tanah</ion-select-option>
                    <ion-select-option value="Ubin">Ubin</ion-select-option>
                    <ion-select-option value="Kaca">Kaca</ion-select-option>
                </ion-select>
            </ion-item>
            <ion-item>
                <ion-label position="stacked" class="label-input-select">Bentuk Kolam</ion-label>
                <ion-select v-model="bentuk" placeholder="Bundar">
                    <ion-select-option value="Bundar">Bundar</ion-select-option>
                    <ion-select-option value="Persegi">Persegi</ion-select-option>
                    <ion-select-option value="Segi Tiga">Segi Tiga</ion-select-option>
                </ion-select>
            </ion-item>

            <div class="ion-text-center btn-container">
                <ion-button @click="regValue">Registrasi</ion-button>
            </div>
        </ion-content>
    </ion-page>
</template>

<script lang="ts">
import {
    IonContent,
    IonHeader,
    IonPage,
    IonInput,
    IonItem,
} from "@ionic/vue";
import { defineComponent } from "vue";
import { homeSharp } from "ionicons/icons";
import { Storage } from '@ionic/storage';

export default defineComponent({
    name: "RegisterPage",
    components: {
        IonContent,
        IonHeader,
        IonPage,
        IonInput,
        IonItem,
    },
    data() {
        return {
            "home-sharp" : homeSharp,
            nama: ``,
            lokasi: ``,
            material: 'Tanah',
            bentuk: `Bundar`,
            // pondReg: `kolam : ${nama} location : ${lokasi} material : ${material} bentuk: ${bentuk}` 
        };
    },
    methods: {
        async regValue() {
            console.log(this.nama)
            console.log(this.lokasi)
            console.log(this.material)
            console.log(this.bentuk)

            let pond = {'nama' : this.nama, 'lokasi' : this.lokasi, 'material' : this.material, 'bentuk' : this.bentuk}
            console.log(pond)
            const store = new Storage();
            store.create();
            store.set('Pond', pond);

            var pond_copy = await store.get('Pond');
            console.log(pond_copy)
        }
        //alert(this.inputEAN);
    },
});
</script>

<style scoped>
#container {
    text-align: center;

    position: absolute;
    left: 0;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
}

#container strong {
    font-size: 20px;
    line-height: 26px;
}

#container p {
    font-size: 16px;
    line-height: 22px;

    color: #8c8c8c;

    margin: 0;
}

#container a {
    text-decoration: none;
}

a:visited {
    color: white;
}

ion-button {
    --background: #1B7C1A;
}

ion-card,
ion-card-title,
ion-card-subtitle {
    color: black;
}

ion-card-title {
    font-weight: bold;
    font-size: 18px !important;
}

ion-card {
    border-radius: 16px;
    margin-bottom: 20px !important;
}

.deactive {
    --background: #952229;
}

.fixedButton {
    /* --border-radius : 50%; */
    position: fixed;
    bottom: 0px;
    right: 0px;
    width: 100px;
    height: auto;
}

ion-item{
    margin-top: 10px !important;
}
.input{
    margin: 0 20px;
}

ion-input{
    --background : #2F2C40;
    border-radius: 10px;
    padding-left: 20px;
    text-indent: 20px;
}

ion-select{
    background-color: #2F2C40;
    border-radius: 10px;
    padding-left: 20px;
    margin: auto;
    width: 90%;
}

.label-input{
    font-size: 20px;
    margin-bottom: 15px;
    /* text-align: center; */
}

.label-input-select{
    margin-left: 22px;
    font-size: 20px;
    margin-bottom: 15px;
}

.btn-container{
    margin-top: 40px;
    margin-right: 40px;
    margin-left: 38px;
}

ion-button{
    width: 100%;
    --border-radius: 12px;
    --background:#6C5ECF;
}
</style>

function lokasi(lokasi: any) {
  throw new Error("Function not implemented.");
}
