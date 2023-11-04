Nama : Robby firmansyah

NIM : 312210643

Kelas : TI.22.A5

Mata Kuliah : Pemrograman Mobile 1

Dosen Pengampu : Donny Maulana, S.Kom.,M.M.S.I.

Tugas : Buatlah Method Program java Toast Number, dengan menghasilkan Bilangan Fibonacci

# Layout
Pada layout ini, saya membuat tiga button dan satu textview :

button_limit, berfungsi sebagai tombol “Set Limit” yang nantinya ketika di tekan akan muncul sebuah pop-up untuk masukan limit angka yang ingin 
kita hitung.

button_count, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya sesuai dengan yang kita limit. Juga berbeda warna pada setiap angka, agar tidak keliru.

button_back, berfungsi sebagai tombol restart yang nantinya angka akan kembali ke awal.

Textview show_count, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.
Berikut adalah coding pada menu layout :

# activity_main.xml

![gambar]<https://github.com/IDOYGAMING/Pemrogram-mobile-/blob/main/gambar/ss1.png>

# Strings.xml

<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">Fibonacci</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">0</string>
    <string name="coast_message">Welcome Toast</string>
    <string name="Reset">Reset</string>
</resources>

# Colors.xml

<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="colorPrimary">#0000FF</color>
    <color name="yellow">#FFFF00</color>
    <color name="muda">#00BCD4</color>
    <color name="green">#4CAF50</color>
</resources>/

# Java class

Pada Java class MainActivity.java berisi semua coding untuk menjalankan aplikasi. Seperti fungsi untuk tombol-tombol, dialog set limit, warna yang berbeda pada setiap angka, lalu warna background yang bisa berubah dan rumus bilangan fibonacci.

package com.example.fibonacci;

import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    private int count = 1;
    private TextView showCount;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        showCount = findViewById(R.id.show_count);
    }

    public void showToast(View view) {
        Toast toast = Toast.makeText(this, "Welcome Toast!", Toast.LENGTH_SHORT);
        toast.show();
    }

    @SuppressLint("SetTextI18n")
    public void CountUP(View view) {
        if (count < 0) {
            count = 0;
        }

        int result = generateFibonacci(count);

        if (result <= 1000) {
            showCount.setText(Integer.toString(result));
            count++;
        }
    }


    private int generateFibonacci(int n) {
        if (n <= 0) {
            return 0;
        } else if (n == 1) {
            return 1;
        }

        int first = 0;
        int second = 1;
        for (int i = 2; i <= n;  i++) {
            int next = first + second;
            first = second;
            second = next;
        }
        return first;

    }
    public void Reset(View view) {
        count = 1;
        showCount.setText("0");
    }
},