## Ujian AKhir Semester Pemograman Mobile 2

## API Daftar Stasiun Kereta Api di Indonesia

## Profil
| #               | Biodata                  |
| --------------- | --------------------     |
| **Nama**        | Muhamad Suryanegara      |
| **NIM**         | 312110447                |
| **Kelas**       | TI.21.A.1                |
| **Mata Kuliah** | Pemrograman Mobile 2     |

A new Flutter project.

# Tutorial
buka aplikasi `Visual Studio Code`  , kemudian buat project baru dengan mengklik `Ctrl + Shift + P`  
```

- Lalu, pada direktori lib > main.dart hapus semua kode, kemudian ubah dengan kode ini:

```
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

```

- Kemudian, tambahkan `APIKEY` kalian dalam url.

```dart
       (Uri.parse('https://booking.kai.id/api/stations2'));
```

- Dan jangan lupa menambahkan Library http pada file `pubspec.yaml`.

```dart
dependencies:
  flutter:
    sdk: flutter
  http: ^0.13.4
```

- Buka terminal, Kemudian run command `flutter run`.
- Maka hasilnya akan seperti ini :>

## Berikut adalah hasilnya

![Screenshot 2023-07-05 114823](https://github.com/Muhamadsuryanegara/UAS_P.Mobile.2/assets/92678339/c6a19c21-c8b1-49f4-9305-35de658ef6c1)


- Kode diatas dapat kalian improvisasi dengan kreasi kalian sendiri.

## Terima Kasih!



