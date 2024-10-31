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

Kode ini mengimpor modul `socket`, yaitu modul yang menyediakan akses ke interface jaringan dasar di Python. Modul socket memungkinkan kita untuk bekerja dengan soket jaringan, seperti mengirim dan menerima data melalui jaringan.

```python
def print_machine_info():
    host_name = socket.gethostname()
    ip_address = socket.gethostbyname(host_name)
    print("Host name: %s" % host_name)
    print("IP address: %s" % ip_address)
```
Bagian ini menjalankan fungsi print_machine_info() yang melakukan beberapa hal seperti:

`host_name = socket.gethostname()` berfungsi untuk mendapatkan nama host dari mesin yang menjalankan program.

`ip_address = socket.gethostbyname(host_name)` menggunakan nama host untuk mendapatkan alamat IP yang sesuai dengan mesin ini.

`print("Host name: %s" % host_name)` berfungsi untuk mencetak nama host ke layar.

`print("IP address: %s" % ip_address)` berfungsi untuk mencetak alamat IP ke layar.

```python
if __name__ == '__main__':
    print_machine_info()
```

Bagian ini adalah titik awal eksekusi program. Kondisi if `__name__ == '__main__':` digunakan untuk memastikan bahwa `print_machine_info()` hanya dijalankan jika skrip ini dijalankan langsung, bukan jika diimpor sebagai modul di skrip lain. Jika benar, maka fungsi `print_machine_info()` akan dipanggil.

### Output
Jika program dijalankan, outputnya akan menampilkan nama host dan alamat IP mesin yang menjalankan program, berikut adalah hasil screenshot-nya:

```cmd
Host name: my-computer
IP address: 192.168.1.5
```

## SOCKET02_GETINFO.PY

Kode ini berfungsi untuk mendapatkan alamat IP dari suatu nama domain (hostname) secara sederhana yang bisa digunakan untuk troubleshooting jaringan atau untuk aplikasi yang perlu mendapatkan alamat IP dari suatu domain tertentu. berikut adalah penjelsannya

```python
# Nama=
# NIM=

import socket

def get_remote_machine_info():
    remote_host = 'www.python.org'
    try:
        print("IP address of %s: %s" % 
              (remote_host, socket.gethostbyname(remote_host)))
    except socket.error as err_msg:
        print("%s: %s" % (remote_host, err_msg))

if __name__ == '__main__':
    get_remote_machine_info()
```

Kode tersebut menggunakan modul `socket` sama seperti kode sebelumnya untuk mendapatkan informasi tentang nama host dan alamat IP dari mesin yang menjalankan program.

```python
def get_remote_machine_info():
    remote_host = 'www.python.org'
    try:
        print("IP address of %s: %s" % 
              (remote_host, socket.gethostbyname(remote_host)))
    except socket.error as err_msg:
        print("%s: %s" % (remote_host, err_msg))
```

Bagian ini mendefinisikan fungsi `get_remote_machine_info()` yang melakukan berfungsi untuk menjalankan fungsi berikut:

`remote_host = 'www.python.org'` berfungsi untuk menetapkan remote_host sebagai nama domain www.python.org, yang alamat IP-nya ingin kita dapatkan.

Blok `try` akan mencoba mengeksekusi kode di dalam blok try.

`socket.gethostbyname(remote_host)` digunakan untuk mendapatkan alamat IP dari nama host remote_host. Jika berhasil, alamat IP dari www.python.org akan dicetak ke layar.

`print("IP address of %s: %s" % (remote_host, socket.gethostbyname(remote_host))):` Baris ini mencetak nama host `(remote_host)` dan alamat IP yang dikembalikan oleh `socket.gethostbyname()`.

Blok `except socket.error as err_msg:` berlaku jika terjadi kesalahan dalam menghubungi `remote_host` atau kode tidak dapat menemukan alamat IP, blok `except` akan menangani kesalahan tersebut dan mencetak pesan kesalahan.

`print("%s: %s" % (remote_host, err_msg)):` baris ini mencetak nama host beserta pesan kesalahan `(err_msg)` jika terjadi error.

```python
if __name__ == '__main__':
    get_remote_machine_info()
```
sama seeprti sebelumnya, Bagian ini adalah titik awal eksekusi program. Kondisi `if __name__ == '__main__':` memastikan bahwa `get_remote_machine_info()` hanya dipanggil jika skrip ini dijalankan langsung dan bukan jika diimpor sebagai modul di skrip lain. Jika benar, maka fungsi `get_remote_machine_info()` akan dijalankan.

### Output
Jika program dijalankan dan berhasil mendapatkan alamat IP, outputnya akan terlihat seperti ini:

```cmd
IP address of www.python.org: 138.197.63.241
```

Jika terjadi kesalahan, seperti masalah koneksi atau nama host yang tidak ditemukan, output akan menampilkan pesan kesalahan seperti berikut:

```cmd
www.python.org: [Errno -2] Name or service not known
```

## SOCKET03_SERVICENAME.PY

Kode ini berguna untuk memetakan nomor port tertentu ke nama layanan yang terkait, menggunakan protokol TCP atau UDP. Ini bisa digunakan dalam konteks troubleshooting jaringan atau analisis layanan jaringan. berikut adalah penjelsannya.

```python
# Nama=
# NIM=

import socket

def find_service_name():
    protocolname = 'tcp'
    for port in [80, 25]:
        print("Port: %s => service name: %s" % 
              (port, socket.getservbyport(port, protocolname)))
    print("Port: %s => service name: %s" % 
          (53, socket.getservbyport(53, 'udp')))

if __name__ == '__main__':
    find_service_name()
```

Fungsi `find_service_name()` pada kode diatas dapat melakukan fungsi sebagai berikut:

`protocolname = 'tcp'` berfungsi untuk menetapkan protokol yang akan digunakan sebagai tcp untuk mengecek layanan yang berjalan pada port-port tertentu.

`for port in [80, 25]` berfungsi untuk melakukan iterasi pada daftar port `[80, 25]`.

`socket.getservbyport(port, protocolname)` digunakan untuk mendapatkan nama layanan berdasarkan nomor port (`port`) dan protokol (`protocolname`). Dalam hal ini, protokolnya adalah `tcp`.

`print("Port: %s => service name: %s" % (port, socket.getservbyport(port, protocolname)))` bertujuan untuk mencetak nomor port dan nama layanan yang berjalan pada port tersebut.

`print("Port: %s => service name: %s" % (53, socket.getservbyport(53, 'udp')))` Baris ini mencetak nama layanan untuk port 53 menggunakan protokol udp.

Secara keseluruhan, fungsi ini menampilkan nama layanan yang berjalan pada:

Port 80 dengan protokol TCP (umumnya digunakan untuk HTTP).

Port 25 dengan protokol TCP (umumnya digunakan untuk SMTP).

Port 53 dengan protokol UDP (umumnya digunakan untuk DNS).

### Output
Jika program dijalankan, outputnya akan menampilkan nama layanan berdasarkan port yang ditentukan seperti berikut:

```cmd
Port: 80 => service name: http
Port: 25 => service name: smtp
Port: 53 => service name: domain
```

## SOCKET04_SOCKETTIMEOUT.PY

```python
# Nama=
# NIM=

import socket

def test_socket_timeout():
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    print("Default socket timeout: %s" % s.gettimeout())
    s.settimeout(100)
    print("Current socket timeout: %s" % s.gettimeout())

if __name__ == '__main__':
    test_socket_timeout()
```

Fungsi test_socket_timeout() melakukan hal berikut:

`s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)` berfungsi untuk membuat objek soket s menggunakan alamat `AF_INET (IPv4)` dan tipe soket `SOCK_STREAM` (untuk protokol TCP).

`s.gettimeout()` dapat mengecek dan mendapatkan nilai waktu tunggu (timeout) default dari soket. Nilai timeout awalnya adalah `None`, yang berarti soket tidak memiliki waktu tunggu (tidak ada batas waktu untuk operasi yang memblokir, seperti menerima data).

`print("Default socket timeout: %s" % s.gettimeout())` mencetak nilai waktu tunggu default dari soket.

`s.settimeout(100)` mengatur waktu tunggu soket menjadi 100 detik. Ini berarti operasi yang memblokir pada soket ini (misalnya, menerima data) akan gagal jika tidak selesai dalam 100 detik.

`print("Current socket timeout: %s" % s.gettimeout())` mencetak nilai waktu tunggu saat ini setelah perubahan.

### Output
Jika program dijalankan, outputnya akan menampilkan nilai waktu tunggu default dan waktu tunggu baru setelah diubah, berikut adalah hasilnya:

```cmd
Default socket timeout: None
Current socket timeout: 100
```

## SOCKET05_SOCKETBUFFERSIZE.PY

```python
# Nama=
# NIM=

import socket

SEND_BUF_SIZE = 4096
RECV_BUF_SIZE = 4096

def modify_buff_size():
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    # Get the size of the socket's send buffer
    bufsize = sock.getsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF)
    print("Buffer size [Before]:%d" % bufsize)
    
    sock.setsockopt(socket.SOL_TCP, socket.TCP_NODELAY, 1)
    sock.setsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF, SEND_BUF_SIZE)
    sock.setsockopt(socket.SOL_SOCKET, socket.SO_RCVBUF, RECV_BUF_SIZE)
    
    bufsize = sock.getsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF)
    print("Buffer size [After]:%d" % bufsize)

if __name__ == '__main__':
    modify_buff_size()
```
Variabel SEND_BUF_SIZE dan RECV_BUF_SIZE digunakan untuk menyimpan ukuran buffer yang akan digunakan dalam program. Dalam hal ini, keduanya diatur ke 4096 byte.

Fungsi `modify_buff_size()` melakukan hal berikut:

`sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)` ebrfungsi untuk membuat objek soket sock menggunakan alamat `AF_INET` (IPv4) dan tipe soket `SOCK_STREAM` (untuk protokol TCP).

`sock.getsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF)` mengambil ukuran buffer pengiriman (`SO_SNDBUF`) dari soket sebelum modifikasi. Nilai ini disimpan dalam variabel `bufsize`
.
`print("Buffer size [Before]:%d" % bufsize)` mencetak ukuran buffer pengiriman sebelum modifikasi.

`sock.setsockopt(socket.SOL_TCP, socket.TCP_NODELAY, 1)` mengatur opsi TCP_NODELAY untuk menonaktifkan algoritma Nagle, sehingga data dikirim segera tanpa menunggu buffer penuh.

`sock.setsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF, SEND_BUF_SIZE)` mengatur ukuran buffer pengiriman (SO_SNDBUF) menjadi nilai SEND_BUF_SIZE (4096 byte).

`sock.setsockopt(socket.SOL_SOCKET, socket.SO_RCVBUF, RECV_BUF_SIZE)` mengatur ukuran buffer penerimaan (SO_RCVBUF) menjadi nilai RECV_BUF_SIZE (4096 byte).

`sock.getsockopt(socket.SOL_SOCKET, socket.SO_SNDBUF)` mendapatkan ukuran buffer pengiriman setelah modifikasi, dan menyimpan nilainya dalam bufsize.

`print("Buffer size [After]:%d" % bufsize)` mencetak ukuran buffer pengiriman setelah modifikasi.
















