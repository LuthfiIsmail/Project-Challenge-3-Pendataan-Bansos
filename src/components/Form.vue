<template>
    <v-card
        elevation="4"
        class="mx-auto ma-4 pa-4"
        max-width="720"
    >
        <v-card-title>Data Penerima Bansos</v-card-title>
        <v-form
            v-model="valid"
            @submit.prevent="onSubmit"
        >
            <v-container>
                <v-text-field
                    v-model="nama"
                    :rules="namaRules"
                    label="Nama"
                    required
                ></v-text-field>

                <v-text-field
                    type="number"
                    v-model="nik"
                    :rules="nikRules"
                    label="NIK"
                    required
                ></v-text-field>

                <v-text-field
                    type="number"
                    v-model="no_kk"
                    :rules="nokkRules"
                    label="Nomor Kartu Keluarga"
                    required
                ></v-text-field>

                <v-file-input
                    v-model="ktp"
                    accept="image/jpg, image/jpeg, image/png, image/bmp"
                    show-size
                    :rules="ktpRules"
                    label="Foto KTP"
                    hint="File Size Kurang dari 2 MB"
                    prepend-icon="mdi-camera"
                    required
                ></v-file-input>

                <v-file-input
                    v-model="kk"
                    accept="image/jpg, image/jpeg, image/png, image/bmp"
                    show-size
                    :rules="kkRules"
                    label="Foto Kartu Keluarga"
                    hint="File Size Kurang dari 2 MB"
                    prepend-icon="mdi-camera"
                    required
                ></v-file-input>

                <v-text-field
                    type="number"
                    v-model="umur"
                    :rules="umurRules"
                    label="Umur"
                    suffix="tahun"
                    required
                ></v-text-field>

                <v-select
                    :items="jenis_kelamin_list"
                    v-model="jenis_kelamin"
                    :rules="jenisKelaminRules"
                    label="Jenis Kelamin"
                    required
                ></v-select>

                <v-textarea
                    v-model="alamat"
                    :rules="alamatRules"
                    label="Alamat"
                ></v-textarea>

                <v-btn v-on:click="handle">Submit</v-btn>
            </v-container>
        </v-form>
    </v-card>
</template>
<script>
export default {
    data: () => ({
        valid: false,
        nama: '',
        nik: '',
        no_kk: '',
        ktp: [],
        kk: [],
        umur: '',
        jenis_kelamin_list: ['Laki-laki', 'Perempuan'],
        jenis_kelamin: '',
        alamat: '',

        namaRules: [
            v => !!v || 'Nama tidak boleh kosong'
        ],

        nikRules: [
            v => !!v || 'NIK tidak boleh kosong',
            v => (v && v.length <= 16) || 'NIK tidak boleh lebih dari 16 karakter'
        ],

        nokkRules: [
            v => !!v || 'Nomor KK tidak boleh kosong',
            v => (v && v.length <= 16) || 'Nomor KK tidak boleh lebih dari 16 karakter'
        ],

        umurRules: [
            v => !!v || 'Umur tidak boleh kosong',
            v => (v && v.length <= 25) || 'Umur peserta minimal 25 tahun'
        ],

        jenisKelaminRules: [
            v => !!v || 'Jenis Kelamin tidak boleh kosong'
        ],

        alamatRules: [
            v => !!v || 'Alamat tidak boleh kosong'
        ],
    }),
    computed : {
        ktpRules() {
            let rules = []
            rules = ['Foto KTP tidak boleh kosong']
            if (this.ktp) {
                rules = [v => v.size <= 2097152 || 'Ukuran file maksimal 2 MB']
            }
            return rules
        },

        kkRules() {
            let rules = []
            rules = ['Foto Kartu Keluarga tidak boleh kosong']
            if (this.kk) {
                rules = [v => v.size <= 2097152 || 'Ukuran file maksimal 2 MB']
            }
            return rules
        }
    },
    methods: {
        onSubmit() {
            console.log('submit')
        }
    }
}
</script>