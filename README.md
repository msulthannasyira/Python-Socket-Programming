# Python Socket Programming

## SOCKET01_PRINTNAMEADDRESS.PY

Kode ini berguna untuk mendapatkan informasi dasar mengenai mesin saat ini, seperti nama host dan alamat IP, yang bisa berguna dalam berbagai aplikasi jaringan atau debugging. berikut adalah penjelasannya.

```python
# Nama=
# NIM=

import socket

def print_machine_info():
    host_name = socket.gethostname()
    ip_address = socket.gethostbyname(host_name)
    print("Host name: %s" % host_name)
    print("IP address: %s" % ip_address)

if __name__ == '__main__':
    print_machine_info()
```

Kode tersebut menggunakan modul `socket` untuk mendapatkan informasi tentang nama host dan alamat IP dari mesin yang menjalankan program.

```python
import socket
```

Kode ini mengimpor modul `socket`, yaitu modul yang menyediakan akses ke antarmuka jaringan dasar di Python. Modul socket memungkinkan kita untuk bekerja dengan soket jaringan, seperti mengirim dan menerima data melalui jaringan.

```python
def print_machine_info():
    host_name = socket.gethostname()
    ip_address = socket.gethostbyname(host_name)
    print("Host name: %s" % host_name)
    print("IP address: %s" % ip_address)
```
Bagian ini menjalankan fungsi print_machine_info() yang melakukan beberapa hal seperti:

`host_name = socket.gethostname()`: Mendapatkan nama host dari mesin yang menjalankan program.

`ip_address = socket.gethostbyname(host_name)`: Menggunakan nama host untuk mendapatkan alamat IP yang sesuai dengan mesin ini.

`print("Host name: %s" % host_name)`: Mencetak nama host ke layar.

`print("IP address: %s" % ip_address)`: Mencetak alamat IP ke layar.

```python
if __name__ == '__main__':
    print_machine_info()
```

Bagian ini adalah titik awal eksekusi program. Kondisi if `__name__ == '__main__':` digunakan untuk memastikan bahwa `print_machine_info()` hanya dijalankan jika skrip ini dijalankan langsung, bukan jika diimpor sebagai modul di skrip lain. Jika benar, maka fungsi `print_machine_info()` akan dipanggil.

## Output
Jika program dijalankan, outputnya akan menampilkan nama host dan alamat IP mesin yang menjalankan program, berikut adalah hasil screenshot-nya:

```cmd
Host name: my-computer
IP address: 192.168.1.5
```





