# Konfigurasi ESLint

## Installation and Setup
Untuk memasang ESLint kita dapat menggunakan *yarn* atau *npm*:
```bash
npm install eslint --save-dev
# or
yarn add eslint --dev
```
Untuk menggunakannya kita harus mengeksekusi `npm-init` atau `yarn-init` terlebih dahulu.  
Lalu jalankan konfigurasi `eslint` berikut:
```bash
npx eslint --init
# or
yarn run eslint --init
```
Jalankan kode dibawah untuk menjalankan ESLint pada file atau direktori kita:
```bash
npx eslint yourfile.js / .
# or
yarn run eslint yourfile.js / .
```
kita dapat memasang ESLint secara global `npm install eslint --global` tetapi sangat tidak disarankan.  
Kita juga dapat menginstall ESLint extension pada *VSCode*.

## Usage
### Membuat Kode Sederhana
Mari kita buat program sederhana untuk memahami cara kerja ESLint.
```javascript
const subject = "Belajar Konfigurasi ESLint"

console.log(subject);

const printSubject=(value) => {
  console.log('masuk fungsi');
    console.log(`Mari ${value}`);
}

printSubject("Belajar Javascript")
```
Dapat kita lihat kode di atas akan berjalan sebagaimana mestinya (tidak error). Akan tetapi terdapat sesuatu yang tidak konsisten seperti titik koma, indentasi, dan kutip satu/kutip dua. Terdapat juga penggunaan `console.log` sebagai testing yang membuat project jadi terlihat kurang profesional.

### Membuat Kode Menjadi Mengikuti Standard
Pastikan kita sudah mengikuti bagian *InstInstallation and Setup*. Berikut adalah caranya:
1. Ketikan `npx eslint --init`
2. Akan muncul pilihan maksud penggunaan ESLint (pilih sesuai kebutuhan), tekan *enter* untuk memilih:
    ```bash
    ? How would you like to use ESLint?
      To check syntax only
    ▸ To check syntax and find problems
      To check syntax, find problems, and enforce code style
    ```
3.  Menentukan penggunaan `import module`:
    ```bash
    ? What type of modules does your project use? … 
    ▸ JavaScript modules (import/export)
      CommonJS (require/exports)
      None of these
    ```
4. Menentukan *Framework* yang digunakan:
    ```bash
    ? Which framework does your project use? … 
      React
      Vue.js
    ▸ None of these
    ```
5. Menentukan penggunaan *TypeScript*:
    ```bash
    ? Does your project use TypeScript? ‣ No / Yes
    ```
6. Menentukan tempat pengeksekusian kode:
    ```bash
    ? Where does your code run? …  (Press <space> to select, <a> to toggle all, <i> to invert selection)
    ✔ Browser
    ✔ Node
    ```
7. Menentukan *Standard* kode project kita:
    ```bash
    ? How would you like to define a style for your project? … 
    ▸ Use a popular style guide
      Answer questions about your style
      Inspect your JavaScript file(s)
    ```
8. Jika kita memilih *popular style guide* maka akan muncul pilihan:
    ```bash
    ? Which style guide do you want to follow? … 
    ▸ Airbnb: https://github.com/airbnb/javascript
      Standard: https://github.com/standard/standard
      Google: https://github.com/google/eslint-config-google
    ```
9. Menentukan bentuk file untuk menyimpan konfigurasi sebelumnya:
    ```bash
    ? What format do you want your config file to be in? … 
    ▸ JavaScript
      YAML
      JSON
    ```
10. Terakhir melakukan installasi konfigurasi yang sudah kita tentukan
    ```bash
    ? Would you like to install them now with npm? ‣ No / Yes
    ```

### Melakukan Pengecekan Kode
Untuk melakukan pengecekan kita dapat menggunakan
```bash
npx eslint .
# or
npx eslint namaFile.js
```
Kita juga dapat menambahkan *script* (`"lint": "npx eslint ."`) di `package.json`.  
Dari kode yang sudah kita buat akan muncul error dan warning sebagai berikut:
```bash
  1:17  error    Strings must use singlequote                   quotes
  1:45  error    Missing semicolon                              semi
  3:1   warning  Unexpected console statement                   no-console
  5:19  error    Operator '=' must be spaced                    space-infix-ops
  6:1   error    Expected indentation of 2 spaces but found 4   indent
  6:5   warning  Unexpected console statement                   no-console
  7:2   error    Missing semicolon                              semi
  9:14  error    Strings must use singlequote                   quotes
  9:35  error    Newline required at end of file but not found  eol-last
  9:35  error    Missing semicolon                              semi

✖ 10 problems (8 errors, 2 warnings)
  8 errors and 0 warnings potentially fixable with the `--fix` option.
```
Jika kita sudah menginstall ESLint di *VSCode* kita dapat mengetahui langsung tanpa harus menjalankan command `npx eslint .` dengan cara arahkan kursor ke bagian line 1 pojok kiri atas dalam hal kode di atas adalah `const` dan klik bubble lalu pilih `ESLint: Manage Library Execution`.  
Untuk melakukan pembetulan atau *fix* kita dapat membuat *script* `"lint-fix": "npx eslint . --fix"` atau kita dapat menambahkan konfigurasi untuk *fix* saat save:
```json
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true
}
```
Perlu di ingat pemberitahuan pada `console.log` hanya berupa warning saja.

### Menambahkan Aturan Konfigurasi 
Kita dapat menambahkan aturan konfigurasi sesuai apa yang kita inginkan pada `.eslintrc` pada bagian `rules`, seperti mematikan warning pada `console.log`:
```json
"rules": {
    "no-console": "off"
}
```

## Daftar Pustaka
- ESLint. [Getting Started with ESLint](https://eslint.org/docs/user-guide/getting-started) (diakses tanggal 31 Januari 2021).
- Hudoro, Prawito. 2020. [Cara Setup Eslint di Javascript, ReactJS dan React Native](https://www.youtube.com/watch?v=4AsOTDdmx_I). (diakses tanggal 31 Januari 2021).
- Baeumer, Dirk. 2020. [VS Code ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint). (diakses tanggal 31 Januari 2021).