#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LENGTH 2024
#define MIN_LENGTH 1945

void lessThanRequired (int* lengthOfText){
    printf("The length of your text is less than specified, please update your text\n");
    *lengthOfText = MIN_LENGTH;
}

void equalThanRequired (int* lengthOfText){
    printf("Thank you, Your text length is correct\n");
}

void moreThanRequired (int* lengthOfText){
    printf("Your text is too long, please reduce the text\n");
    *lengthOfText = MIN_LENGTH;
}

int checkLenghtRequirement(char* text){
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}

int main() {
    int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];

    fptr = fopen("ilham.txt", "r");

    if(fptr == NULL){
        printf("Error");
        exit(1);
    }

    fgets(text, MAX_LENGTH, fptr);

    fclose(fptr);

    selectOption = checkLenghtRequirement(text);

    printf("\nThe Length is updated to %d", lengthOfText);

    return 0;
}
PENJELASANNYA :

#include <stdio.h>: Mengimpor standar input-output library untuk fungsi printf() dan fgets().

#include <stdlib.h>: Mengimpor library standar untuk alokasi memori dinamis dan fungsi umum lainnya seperti exit().

#include <string.h>: Mengimpor library standar untuk fungsi-fungsi yang berhubungan dengan string seperti strlen().

#define MAX_LENGTH 2024: Mendefinisikan konstanta MAX_LENGTH yang menyimpan panjang maksimum dari teks yang dapat diterima.

#define MIN_LENGTH 1945: Mendefinisikan konstanta MIN_LENGTH yang menyimpan panjang minimum dari teks yang diharapkan.

void lessThanRequired (int* lengthOfText): Mendefinisikan fungsi lessThanRequired yang mengambil pointer ke variabel integer yang mewakili panjang teks. Fungsi ini mencetak pesan bahwa panjang teks kurang dari yang diharapkan dan mengubah panjang teks menjadi nilai minimum.

void equalThanRequired (int* lengthOfText): Mendefinisikan fungsi equalThanRequired yang juga mengambil pointer ke variabel integer yang mewakili panjang teks. Fungsi ini mencetak pesan bahwa panjang teks sudah sesuai dengan yang diharapkan.

void moreThanRequired (int* lengthOfText): Mendefinisikan fungsi moreThanRequired yang mengambil pointer ke variabel integer yang mewakili panjang teks. Fungsi ini mencetak pesan bahwa panjang teks terlalu panjang dan mengubah panjang teks menjadi nilai minimum.

int checkLengthRequirement(char* text): Mendefinisikan fungsi checkLengthRequirement yang mengambil string sebagai argumen dan mengembalikan nilai berdasarkan panjang string tersebut. Jika panjangnya kurang dari MIN_LENGTH, kembali 0. Jika sama dengan MIN_LENGTH, kembali 1. Jika lebih besar dari MIN_LENGTH, kembali 2.

int main() {...}: Fungsi utama dari program.

int lengthOfText, selectOption;: Deklarasi dua variabel integer lengthOfText dan selectOption.

FILE *fptr = NULL;: Deklarasi pointer ke objek FILE dan inisialisasi dengan NULL.

char text[MAX_LENGTH];: Deklarasi array karakter text dengan panjang maksimum MAX_LENGTH.

fptr = fopen("ilham.txt", "r");: Membuka file "ilham.txt" untuk dibaca.

if(fptr == NULL){...}: Memeriksa apakah file berhasil dibuka atau tidak. Jika tidak, mencetak pesan kesalahan dan keluar dari program.

fgets(text, MAX_LENGTH, fptr);: Membaca isi file ke dalam array text.

fclose(fptr);: Menutup file setelah selesai membacanya.

selectOption = checkLengthRequirement(text);: Memanggil fungsi checkLengthRequirement untuk memeriksa apakah panjang teks sesuai dengan persyaratan.

void (*functionArray[3])(int*) = {lessThanRequired, equalThanRequired, moreThanRequired};: Mendefinisikan array dari pointer fungsi yang masing-masing menunjuk ke fungsi yang sesuai. Ada tiga elemen dalam array ini, masing-masing untuk kasus panjang teks kurang dari, sama dengan, dan lebih dari yang diharapkan.

functionArray[selectOption](&lengthOfText);: Memanggil fungsi yang sesuai dari array functionArray berdasarkan nilai selectOption.

printf("\nThe Length is updated to %d", lengthOfText);: Mencetak panjang teks yang telah diubah, baik itu menjadi nilai minimum atau tidak.

OUTPUT


<img width="772" alt="312400119-8929b8e9-c7ba-47ca-a1b0-da4003e4af0a" src="https://github.com/Adminsego/OTS-week-4/assets/154228064/4530e819-be51-4b34-ad2b-7a00551f52e4">
