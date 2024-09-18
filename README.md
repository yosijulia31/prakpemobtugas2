TUGAS PERTEMUAN 2 PEMROGRAMAN MOBILE

Nama		: Yosi Julia Utami

NIM		: H1D021022

Shift Baru	: D

A.	SCREENSHOT
  
ada di file di atas


B.	Proses Passing Data dari Form Menuju Tampilan 
1.	Di halaman FormData, user menginputkan data di form yang berisikan Nama, NIM, dan Tahun Lahir.
2.	Data yang sudah di-inputkan diterima TextField di setiap nama, nim, dan tahun. Di sini setiap TextField memiliki TextEditingController. Controller ini dugunakan untuk mengambil nilai input dari TextField.
3.	User menekan tombol Simpan yang di dalamnya ada handler “onPressed” yang didalamnya digunakan untuk mengambil data dari controller.

Codenya ini:

onPressed: () {

  // Mengambil nilai dari masing-masing controller
  
  String nama = _namaController.text; //untuk mengambil teks yg diinput pada TextField Nama
  
  String nim = _nimController.text; //untuk mengambil teks yg diinput pada TextField NIM
  
  int tahun = int.parse(_tahunController.text); //untuk mengambil teks yg diinput pada TextField tahun lahir, dan kemudian di konversi menjadi int menggunakan int.parse

4.	Setelah data diambil dari form, aplikasi menggunakan navigasi ke halaman lain, yaitu halaman tampil_data, menggunakan Navigator.push(). Data yang diambil nama, nim, dan tahun yang juga ikut dikirim ke halaman tampil_data. 

Codenya ini:

Navigator.of(context).push(MaterialPageRoute(
 
  builder: (context) => TampilData(nama: nama, nim: nim, tahun: tahun)

)

);

5.	Data yang dikirim dari form_data diterima tampil_data melalui konstruktor widget dan setelah diterima lalu diinisialisasi melalui konstruktor TampilData, sehingga dapat digunakan dalam widget untuk ditampilkan.
6.	Setekah data diterima oleh halaman tampil_data, data tersebut diolah sesuai kebutuhan. Disini yang perlu di olah seperti umur. Umur dihitung berdasarkan tahun saat ini dikurangi tahun lahir, dan hasilnya ditampilkan di layer.

Codenya ini:

final int umur = DateTime.now().year - tahun; //menghitung umur berdasarkan tahun saat ini dikurangi tahun lahir yang diinput

7.	Setelah data selesai di olah maka data ditampilkan dengan code berikut ini:

@override

Widget build(BuildContext context) {

  return Scaffold(
  
    appBar: AppBar(
    
      title: const Text("Perkenalan"),
    
    ),
    
    body: Container(
    
      margin: const EdgeInsets.all(10),
      
      child: Column(
      
        children: [
        
          // Menampilkan data yang sudah di-pass dari halaman sebelumnya
          
          Text("Hallo, nama saya $nama, lalu NIM saya $nim, dan umur saya tahun ini adalah $umur tahun"),
        
        ],
      
      ),
    
    ),
  
  );

}
