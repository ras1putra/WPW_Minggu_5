<template>
    <form @submit.prevent="handleSubmit">
        <div class="flex mx-auto px-4 bg-gradient-to-r from-purple-700 to-blue-500">
            <div class="flex w-1/4 items-center flex-col">
                <img src="src/assets/LOGO.svg">
                <div>
                    <div class="font-bold text-white text-4xl text-center">
                        Hai!
                    </div>
                    <div class="font-bold text-white text-2xl overflow-hidden text-center">
                        {{ datap.nama }}
                    </div>
                    <div class="font-bold text-white text-2xl overflow-hidden text-center">
                        Usia {{ datap.umur }} Tahun ({{ datap.isClicked }})<br>Pelamar {{ kategori.text }}
                    </div>
                    <div class="font-bold text-white text-2xl overflow-hidden text-center">
                        Deskripsi diri :<br>{{ datap.deskripsi }}
                    </div>
                </div>
            </div>
            <div class="w-3/4 p-4 rounded-3xl bg-gray-200 m-4 items-center justify-center shadow-2xl shadow-cyan-500/40">
                <div class="font-bold text-2xl text-center py-4">
                    Apply as Employee
                </div>
                <input-component type="text" v-model="datap.nama" label="Nama Lengkap" placeholder="Nama Lengkap Anda"
                    :error="errors['nama']"></input-component>
                <input-component type="number" v-model="datap.umur" label="Umur" placeholder="Umur Anda"
                    :error="errors['umur']"></input-component>
                <div class="flex justify-between px-4 font-bold items-center my-2">
                    <label for="desk">Deskripsi Singkat Diri</label>
                    <textarea class="w-3/4 ml-4 rounded-md p-2" rows="5" placeholder="Deskripsi Diri"
                        v-model="datap.deskripsi"></textarea>
                </div>
                <div class="flex justify-between px-4 font-bold my-2 items-center">
                    <label for="cv">CV Anda</label>
                    <input type="file"
                        class="w-3/4 text-slate-500 file:font-semibold file:text-violet-700 file:border-0 file:rounded-md file:px-4 file:py-2 file:bg-violet-50">
                </div>
                <select-component label="Category" v-model="kategori.text" :options="kategori"
                    placeholder="Pilih Posisi Yang Dilamar" :error="errors['pilihan']"></select-component>
                <div class="flex justify-between px-4 font-bold my-2">
                    <div class="w-1/4">
                        Kewarganegaraan
                    </div>
                    <div class="w-3/4 flex flex-row">
                        <radio-component label="WNI" :value="1" v-model="datap.isClicked"></radio-component>
                        <radio-component label="WNA" :value="0" v-model="datap.isClicked"></radio-component>
                    </div>
                </div>
                <div class="flex px-4 font-semibold my-2 mt-4 items-center">
                    <input type="checkbox" id="agree">
                    <label for="agree" class="flex ml-2 text-sm font-base text-slate-500">Saya menyetujui kebijakan dan
                        privasi perusahaan.</label>
                </div>
                <button class="mt-4 ml-2 p-2 px-4 rounded-md bg-green-500 text-white font-bold text-lg hover:opacity-50" type="submit">
                    DAFTAR
                </button>
            </div>
        </div>
    </form>
</template>
<script>
import InputComponent from './InputComponent.vue'
import SelectComponent from './SelectComponent.vue'
import RadioComponent from './RadioComponent.vue'
export default {
    components: {
        InputComponent,
        SelectComponent,
        RadioComponent
    },
    data() {
        return {
            datap: {
                nama: '',
                umur: '',
                deskripsi: '',
                isClicked: ''
            },
            kategori: [
                { value: 1, text: 'Supervisor' },
                { value: 2, text: 'Sales' },
                { value: 3, text: 'Head Officer' },
                { value: 4, text: 'Clown Officer' }
            ],
            errors: {},
        };
    },
    methods: {
        handleSubmit() {
            this.errors = {
                nama: ["Masukkan nama"],
                umur: ["Masukkan umur"],
                pilihan: ["Pilihan harus dipilih"]
            }
        }
    }
};
</script>