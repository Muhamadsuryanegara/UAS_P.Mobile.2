# flutter_uas_mobile_akhir
API Daftar Stasiun Kereta Api di Indonesia
Profil
<table>
<thead>
<tr>
<th>#</th>
<th>Biodata</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Nama</strong></td>
<td>Muhamad Suryanegara</td>
</tr>
<tr>
<td><strong>NIM</strong></td>
<td>312110447</td>
</tr>
<tr>
<td><strong>Kelas</strong></td>
<td>TI.21.A.1</td>
</tr>
<tr>
<td><strong>Mata Kuliah</strong></td>
<td>Pemrograman Mobile 2</td>
</tr>
</tbody>
</table>

<h3> Tutorial </h3>
buka aplikasi Visual Studio Code , kemudian buat project baru dengan mengklik Ctrl + Shift + P


- Lalu, pada direktori lib > main.dart hapus semua kode, kemudian ubah dengan kode ini:

import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';

void main() {
  runApp(MyApp());
}

class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  List<dynamic> stationData = [];

  Future<void> fetchStationData() async {
    var response = await http.get(Uri.parse('https://booking.kai.id/api/stations2'));
    if (response.statusCode == 200) {
      setState(() {
        stationData = json.decode(response.body) as List<dynamic>;
      });
    } else {
      print('Failed to fetch data from API.');
    }
  }

  @override
  void initState() {
    super.initState();
    fetchStationData();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'API Demo',
      home: Scaffold(
        appBar: AppBar(
          title: Text(
            'Nama-Nama Stasiun',
            style: TextStyle(color: Colors.white),
          ),
          backgroundColor: Colors.black,
        ),
        body: ListView.builder(
          itemCount: stationData.length,
          itemBuilder: (BuildContext context, int index) {
            return ListTile(
              title: Text(stationData[index]['name']),
              subtitle: Text(stationData[index]['city']),
            );
          },
        ),
      ),
    );
  }
}

- Kemudian, tambahkan `APIKEY` kalian dalam url.

```dart
        (Uri.parse('https://booking.kai.id/api/stations2'));

Dan jangan lupa menambahkan Library http pada file pubspec.yaml.

dependencies:
  flutter:
    sdk: flutter
  http: ^0.13.4

Buka terminal, Kemudian run command flutter run.
Maka hasilnya akan seperti ini :>

![Screenshot 2023-07-05 114823](https://github.com/Muhamadsuryanegara/UAS_P.Mobile.2/assets/92678339/10a5f35f-7f87-4ffd-bf39-76adeb87d5a5)

Kode diatas dapat kalian improvisasi dengan kreasi kalian sendiri.
Terima Kasih!
