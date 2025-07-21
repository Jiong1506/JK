<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UAS Jaringan Komputer - Dark Mode</title>
    <style>
        /* Global Box Sizing for consistent layout */
        *, *::before, *::after {
            box-sizing: border-box;
        }

        :root {
            --primary-bg: #1a1a2e; /* Dark Purple-Blue */
            --secondary-bg: #22223b; /* Darker Purple-Blue */
            --text-color: #e0e0e0; /* Light Grey */
            --header-color: #e94560; /* Vibrant Red */
            --accent-color: #00bcd4; /* Cyan */
            --button-bg: #e94560; /* Vibrant Red for buttons */
            --button-hover: #d82b45; /* Darker Red on hover */
            --border-color: #3e206f; /* Deep Purple */
            --card-bg: #282846; /* Slightly lighter than secondary-bg */
            --shadow-color: rgba(0, 0, 0, 0.3);
            --correct-bg: #388e3c; /* Dark Green */
            --correct-text: #e8f5e9; /* Light Green */
            --incorrect-bg: #c62828; /* Dark Red */
            --incorrect-text: #ffebee; /* Light Red */
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: var(--primary-bg);
            color: var(--text-color);
            line-height: 1.6;
            -webkit-tap-highlight-color: transparent;
            word-wrap: break-word; /* Ensure long words break to prevent overflow */
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: var(--secondary-bg);
            border-radius: 12px;
            box-shadow: 0 8px 25px var(--shadow-color);
            padding: 25px;
            border: 1px solid var(--border-color);
        }

        h1 {
            color: var(--header-color);
            text-align: center;
            margin-bottom: 30px;
            font-size: 2em;
            position: relative;
            padding-bottom: 10px;
            letter-spacing: 0.05em;
        }

        h1::after {
            content: '';
            position: absolute;
            left: 50%;
            bottom: 0;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background-color: var(--accent-color);
            border-radius: 5px;
        }

        .button-group {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap; /* Allow buttons to wrap on smaller screens */
        }

        .action-button {
            display: block;
            flex-grow: 1; /* Allow buttons to grow and fill space */
            min-width: 150px; /* Ensure minimum width for readability */
            padding: 12px 25px;
            background-color: var(--button-bg);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
            box-shadow: 0 5px 15px rgba(233, 69, 96, 0.4);
        }

        .action-button:hover {
            background-color: var(--button-hover);
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(233, 69, 96, 0.6);
        }

        .action-button:active {
            transform: translateY(0);
            box-shadow: 0 2px 5px rgba(233, 69, 96, 0.2);
        }

        .question-card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 10px;
            margin-bottom: 20px;
            padding: 20px;
            box-shadow: 0 4px 15px var(--shadow-color);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .question-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
        }

        .question-card p {
            font-weight: 600;
            color: var(--text-color);
            margin-bottom: 15px;
            font-size: 1.05em;
        }

        .question-card ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .question-card li {
            padding: 10px 15px;
            border-top: 1px dashed #3a3a5a; /* Slightly lighter dashed line for options */
            cursor: pointer;
            transition: background-color 0.2s ease, color 0.2s ease, transform 0.1s ease;
            border-radius: 6px; /* Rounded corners for options */
            margin-bottom: 5px; /* Space between options */
            line-height: 1.4; /* Adjust line height for better readability on mobile */
        }

        .question-card li:first-child {
            border-top: none;
        }

        .question-card li:hover {
            background-color: #323250; /* Darker hover background */
            transform: translateX(5px);
        }

        .question-card li.selected {
            font-weight: bold;
            color: var(--accent-color);
        }

        .question-card li.correct {
            background-color: var(--correct-bg);
            color: var(--correct-text);
            font-weight: bold;
            box-shadow: 0 2px 8px rgba(56, 142, 60, 0.4); /* Green shadow for correct */
        }

        .question-card li.incorrect {
            background-color: var(--incorrect-bg);
            color: var(--incorrect-text);
            font-weight: bold;
            box-shadow: 0 2px 8px rgba(198, 40, 40, 0.4); /* Red shadow for incorrect */
        }

        .answer-reveal {
            margin-top: 15px;
            font-style: italic;
            color: var(--accent-color); /* Use accent color for answer text */
            font-size: 0.95em;
            border-top: 1px solid var(--border-color);
            padding-top: 10px;
            font-weight: bold;
        }

        /* Mobile specific adjustments */
        @media (max-width: 600px) {
            body {
                padding: 10px; /* Reduce global padding slightly */
            }

            .container {
                padding: 15px; /* Reduce container padding */
            }

            h1 {
                font-size: 1.6em; /* Slightly smaller for very small screens */
                margin-bottom: 20px;
            }

            h1::after {
                width: 60px; /* Adjust underline width */
            }

            .button-group {
                flex-direction: column; /* Stack buttons vertically on small screens */
                gap: 10px;
            }

            .action-button {
                width: 100%; /* Full width buttons */
                max-width: none; /* Remove any max-width constraints if they exist */
                padding: 12px 15px;
                font-size: 0.95em;
            }

            .question-card {
                padding: 15px;
            }

            .question-card p {
                font-size: 0.98em; /* Slightly smaller question text */
                margin-bottom: 10px;
            }

            .question-card li {
                padding: 10px 12px;
                font-size: 0.9em; /* Slightly smaller option text */
                margin-bottom: 4px; /* Reduce space between options slightly */
            }

            .answer-reveal {
                font-size: 0.9em;
                padding-top: 8px;
            }
        }

        /* Further adjustments for extremely small screens (e.g., iPhone SE) */
        @media (max-width: 380px) {
            body {
                padding: 8px;
            }
            .container {
                padding: 12px;
            }
            h1 {
                font-size: 1.5em;
            }
            .action-button {
                font-size: 0.9em;
                padding: 10px 12px;
            }
            .question-card p {
                font-size: 0.95em;
            }
            .question-card li {
                font-size: 0.88em;
                padding: 8px 10px;
            }
            .answer-reveal {
                font-size: 0.85em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🌌 UAS Jaringan Komputer Review 💻</h1>
        <div class="button-group">
            <button class="action-button" onclick="loadRandomQuestions()">🔄 Muat Ulang Soal</button>
            <button class="action-button" onclick="toggleAutoReveal()">👁️ Tampilkan Semua Jawaban</button>
        </div>
        <div id="questions-container">
            </div>
    </div>

    <script>
        // Use the fetched content if available, otherwise use default
        const allQuestions = [
            { question: "Contoh internet pada grup jaringan regional adalah ....", options: ["NSFNET", "EBONE", "jaringan kampus", "jaringan antar kampus"], answer: "EBONE" },
            { question: "Contoh dari layer aplikasi adalah ....", options: ["IP", "Telnet", "ICMP", "ATM"], answer: "Telnet" },
            { question: "Layer pada Protokol TCP/IP yang merupakan perangkat keras pada jaringan adalah layer ....", options: ["aplikasi", "transport", "internetwork", "network interface"], answer: "network interface" },
            { question: "ARP merupakan salah satu contoh layer ....", options: ["aplikasi", "transport", "internetwork", "network interface"], answer: "network interface" },
            { question: "Perangkat atau aplikasi yang memberikan pelayanan kepada user internet adalah ....", options: ["client", "server", "hosting", "route"], answer: "server" },
            { question: "Perangkat yang berfungsi untuk menghubungkan jaringan pada layer internetwork dan mengarahkan jalur paket data adalah ....", options: ["router", "bridge", "gateway", "switch"], answer: "router" },
            { question: "Internet dapat digunakan pertama kali secara komersial pada tahun ....", options: ["1991", "1992", "1993", "1994"], answer: "1992" },
            { question: "OSI model (ISO 7498) dibagi menjadi ....", options: ["4 layer", "5 layer", "6 layer", "7 layer"], answer: "7 layer" },
            { question: "Perangkat yang menghubungkan jaringan pada layer network interface dan meneruskan frame adalah ....", options: ["NSFNET", "ARPANET", "CERFNet", "AUP"], answer: "AUP" },
            { question: "Perangkat yang menghubungkan jaringan pada layer network interface dan meneruskan frame adalah ....", options: ["router", "bridge", "gateway", "switch"], answer: "bridge" },
            { question: "Model OSI terdiri dari 7 layer, yang dibagi menjadi dua layer utama, yaitu layer atas dan bawah. Layer yang difokuskan untuk pelayanan dari suatu aplikasi adalah layer ....", options: ["1, 2, dan 3", "2, 3, dan 4", "4, 5, dan 6", "5, 6, dan 7"], answer: "5, 6, dan 7" },
            { question: "Contoh dari Layer Transport adalah ....", options: ["TCP dan SQL", "JPEG dan ASCII", "UDP dan SPX", "IP dan IEEE"], answer: "UDP dan SPX" },
            { question: "Apabila ada program komputer yang melakukan akses jaringan maka pada layer OSI tugas ini dilakukan oleh layer ....", options: ["aplikasi", "presentasi", "session", "transport"], answer: "aplikasi" },
            { question: "Layer pada OSI yang bertugas untuk mengurutkan atau melakukan error-recovery pada saat mengurutkan data yang datang adalah layer ....", options: ["aplikasi", "presentasi", "session", "transport"], answer: "transport" },
            { question: "RJ45 merupakan contoh dari layer ....", options: ["aplikasi", "presentasi", "physical", "data link"], answer: "physical" },
            { question: "Layer yang bertugas untuk mengurusi format data yang dapat dipahami oleh berbagai macam media adalah layer ....", options: ["aplikasi", "presentasi", "physical", "data link"], answer: "presentasi" },
            { question: "Data yang dikirim diubah dalam bentuk segmen. Hal ini terjadi pada layer ....", options: ["transport", "network", "data link", "physical"], answer: "transport" },
            { question: "Langkah yang dilakukan ketika melaksanakan enkapsulasi data ada ....", options: ["4", "5", "6", "7"], answer: "7" },
            { question: "Perbedaan model referensi OSI dan TCP/IP salah satunya terdapat pada network interface yang setara pada OSI di layer ....", options: ["physical dan data link", "data link dan network", "network dan transport", "transport dan session"], answer: "physical dan data link" },
            { question: "Ukuran MAC atau Media Access Control yang ditanamkan pada pengalamatan perangkat jaringan adalah ....", options: ["32 bit", "48 bit", "64 bit", "128 bit"], answer: "48 bit" },
            { question: "Berikut ini yang termasuk ke dalam area WAN adalah ....", options: ["kampus", "gedung", "kota", "negara"], answer: "negara" },
            { question: "Contoh dari Layer Transport adalah ....", options: ["hub", "bridge", "switch", "router"], answer: "router" },
            { question: "Pada teknologi Ethernet digunakan format [ x ][ y ][ z ], di mana x merupakan simbol dari ....", options: ["kecepatan", "jenis teknologi", "jenis media", "kabel"], answer: "kecepatan" },
            { question: "Terdapat dua media transmisi, yaitu media terarah dan media tidak terarah, yang termasuk dalam media tidak terarah adalah ....", options: ["transmisi radio", "ciaxial", "twisted pair", "fiber"], answer: "transmisi radio" },
            { question: "Gambar berikut merupakan jenis kabel .... Inti Tembaga Bahan Isolator Kabel Serabut Pelindung Plastik", options: ["UTP", "coaxial", "fiber", "STP"], answer: "coaxial" },
            { question: "Urutan pemasangan kabel jenis TIA/EIA-586-B adalah ....", options: ["putih orange, orange, putih hijau, biru, putih biru hijau, putih coklat coklat", "putih orange, orange, putih hijau, putih biru, biru, hijau, putih coklat coklat", "putih hijau, hijau, putih orange, biru, putih biru, orange, putih coklat, coklat", "putih hijau, hijau, putih orange, putih biru, biru, orange, putih coklat, coklat"], answer: "putih orange, orange, putih hijau, putih biru, biru, hijau, putih coklat coklat" },
            { question: "Jenis konektor berikut adalah ....", options: ["LC", "MT Array", "SC", "SC Duplex"], answer: "SC Duplex" },
            { question: "Salah satu ciri dari kabel Straight-Through adalah ....", options: ["kedua ujung mempunyai aturan yang sama", "kedua ujung mempunyai aturan yang berbeda", "digunakan pada perangkat sejenis", "menggunakan kabel coaxial"], answer: "kedua ujung mempunyai aturan yang sama" },
            { question: "Gambar berikut merupakan aturan pemasangan kabel berdasarkan ....", options: ["TIA/EIA-586-B", "TIA/EIA-586-A", "TIA/EIA-568-B", "TIA/EIA-568-A"], answer: "TIA/EIA-568-A" },
            { question: "Salah satu ciri dari kabel kategori CAT 3 adalah ....", options: ["1 Mbps", "4 Mbps", "16 Mbps", "30 Mbps"], answer: "16 Mbps" },
            { question: "Bilangan biner dari IP address 243.123.111.6 adalah ....", options: ["11110011.01111011.01101110.00000110", "11110011.01111011.01101111.00000110", "11110011.10000000.01101110.00000110", "11110011.01111011.01101111.00001000"], answer: "11110011.01111011.01101110.00000110" },
            { question: "Jumlah jaringan yang dapat ditampung IP address kelas A adalah ....", options: ["126", "127", "128", "129"], answer: "126" },
            { question: "Kelas IP address yang dapat menampung host paling banyak adalah ....", options: ["Kelas A", "Kelas B", "Kelas C", "Kelas D"], answer: "Kelas A" },
            { question: "IP address yang digunakan untuk alamat jaringan adalah ....", options: ["192.168.10.4", "192.168.10.5", "192.168.10.0", "192.168.10.255"], answer: "192.168.10.0" },
            { question: "Apabila kita menggunakan subnetmask 255.255.255.192, maka jumlah host yang bisa kita dapatkan sebanyak ....", options: ["60", "61", "62", "63"], answer: "63" },
            { question: "Apabila menggunakan subneting 255.255.255.128, maka jumlah subnet yang bisa didapatkan adalah ....", options: ["2", "4", "6", "8"], answer: "2" },
            { question: "Apabila menggunakan subneting 255.255.255.252, maka jumlah subnet yang bisa didapatkan adalah ....", options: ["16", "32", "64", "128"], answer: "128" },
            { question: "Metode pengiriman data dengan tujuan semua alamat berada dalam 1 jaringan adalah ....", options: ["broadcast", "unicast", "multycast", "anycast"], answer: "broadcast" },
            { question: "Kemampuan berbeda-beda yang dimiliki interface dalam mengirimkan frame data adalah ....", options: ["minimum transfer unit (MTU)", "maximum transfer unit (MTU)", "fragmentasi", "time to live (TTL)"], answer: "maximum transfer unit (MTU)" },
            { question: "Salah satu ciri dari metode pengiriman multicast adalah ....", options: ["data dikirim ke semua alamat yang berada pada jaringan", "menggunakan alamat kelas D", "menggunakan Private IP", "tidak perlu mendaftarkan alamat IP"], answer: "menggunakan alamat kelas D" },
            { question: "Jenis pesan ICMP dengan nomor 30 adalah ....", options: ["IPv6 Where-are-you", "Timestamp request", "Traceroute", "Router solicitation"], answer: "Traceroute" },
            { question: "Pesan berasal dari suatu router di mana memberitahukan bahwa host tujuan tidak dapat dicapai adalah ....", options: ["echo", "destination unreachable", "source quench", "time exceeded"], answer: "destination unreachable" },
            { question: "Pesan dari router yang dikirim karena sudah kehabisan waktu sesuai batas TTL adalah ....", options: ["destination unreachable", "router solicitation", "router advertisement", "time exceeded"], answer: "time exceeded" },
            { question: "Pada ICMP terdapat beberapa penjelasan pada setiap pesannya. Salah satu pesan yang digunakan untuk mendapatkan IP address adalah ....", options: ["timestamp request", "information request", "address mask request", "parameter problem"], answer: "address mask request" },
            { question: "Broadcast oleh client untuk menemukan server adalah ....", options: ["DHCPDISCOVER", "DHCPOFFER", "DHCPREQUEST", "DHCPACK"], answer: "DHCPDISCOVER" },
            { question: "Pesan dari client yang menyatakan bahwa dia sedang menggunakan informasi dari server adalah ....", options: ["DHCPACK", "DHCPNACK", "DHCPDECLINE", "DHCPRELEASE"], answer: "DHCPRELEASE" },
            { question: "Sebuah protokol yang digunakan untuk mengecek apakah suatu host dapat bergabung dengan IP Multicast adalah ....", options: ["ICMP", "IGMPs", "ARP", "RARP"], answer: "IGMPs" },
            { question: "Protokol yang digunakan untuk mengubah pengalamatan pada layer yang lebih atas (IP address) menjadi alamat fisik jaringan adalah ....", options: ["ARP", "RARP", "ICMP", "IGMPs"], answer: "ARP" },
            { question: "Sebuah perintah yang mengirimkan IP datagram ke suatu host dan mengukur waktu round trip dan menerima respon adalah ....", options: ["PING", "TRACEROUTE", "ARP", "BOOTP"], answer: "PING" },
            { question: "Jenis pesan ICMP yang digunakan untuk mengecek keaktifan dari suatu host adalah ....", options: ["echo", "destination unreachable", "source quench", "redirect"], answer: "echo" },
            { question: "Contoh dari External Gateway Protocol (EGP) adalah ....", options: ["OSPF", "IGP", "BGP", "OSPF"], answer: "BGP" },
            { question: "Jenis routing yang menggunakan algoritma Bellman-Ford adalah ....", options: ["static routing", "distance vector routing", "hybrid routing", "link state routing"], answer: "distance vector routing" },
            { question: "Salah satu contoh dari aplikasi RouteD adalah ....", options: ["OSPF", "RIP", "BGP-4", "RIPng"], answer: "RIP" },
            { question: "Algoritma yang dapat membuat perangkat router untuk menentukan jalur routingnya secara otomatis adalah ....", options: ["static routing", "atomatic routing", "dynamic routing", "direct routing"], answer: "dynamic routing" },
            { question: "Contoh penggunaan algoritma pada hybrid routing adalah ....", options: ["distance vector", "Bellman-Ford", "Dijkstra", "EIGRP"], answer: "EIGRP" },
            { question: "Cara yang bisa digunakan untuk membangun table routing ada ....", options: ["1", "2", "3", "4"], answer: "3" },
            { question: "Jenis routing yang menggabungkan antara distance vector dan link state routing adalah ....", options: ["static routing", "hybrid routing", "dynamik routing", "combined routing"], answer: "hybrid routing" },
            { question: "Pemilihan jalan pada saat routing dilakukan pada ....", options: ["host", "hop", "router", "IP"], answer: "router" },
            { question: "Route yang dilakukan oleh seorang administrator untuk mengatur jalur dari sebuah paket data adalah ....", options: ["static routing", "distance vector", "link state", "hybrid"], answer: "static routing" },
            { question: "Algortima Bellman-Ford pertama kali dikenalkan pada tahun ....", options: ["1959", "1969", "1979", "1988"], answer: "1959" },
            { question: "Telnet merupakan salah satu aplikasi yang menggunakan jaringan. Untuk menjalankan telnet memerlukan port ke ....", options: ["21", "22", "23", "24"], answer: "23" },
            { question: "Segmen TCP yang digunakan untuk pilihan lain pada datagram adalah ....", options: ["padding", "options", "checksum", "window"], answer: "options" },
            { question: "Pada gambar berikut, fungsi dari Length adalah ....", options: ["port yang digunakan untuk mengirimkan data", "panjang data paket keseluruhan", "port yang digunakan untuk tujuan data", "16 bit komplemen-1 dari pseudo-ip-header yang merupakan error check dari paket data"], answer: "panjang data paket keseluruhan" },
            { question: "Segmen TCP yang berfungsi mengaktifkan titik yang darurat pada suatu segmen adalah ....", options: ["URG", "ACK", "PSH", "SYN"], answer: "URG" },
            { question: "Well-known port memiliki range antara ....", options: ["1 sampai dengan 1023", "1 sampai dengan 1024", "1 sampai dengan 1025", "1 sampai dengan 1026"], answer: "1 sampai dengan 1023" },
            { question: "Menerima dan meng-copy data kepada buffer milik pengguna yang digunakan pada komunikasi TCP merupakan fungsi dari ....", options: ["Open", "Send", "Receive", "Close"], answer: "Receive" },
            { question: "Penulisan socket pada terminologi asosiasi yang benar adalah ....", options: ["<tcp, 193.168.123.4, 1500, 193.168.123.5>", "<tcp, 193.168.123.4, 1500, 193.168.123.5, 21>", "<tcp, 193.168.123.4, 1500, 21>", "<tcp, 193.44.234.3, 12345>"], answer: "<tcp, 193.168.123.4, 1500, 193.168.123.5, 21>" },
            { question: "Jumlah tipe port yang digunakan untuk komunikasi host-to-host adalah ....", options: ["1", "2", "3", "4"], answer: "2" },
            { question: "Untuk mengetahui lebih lengkap dari spesifikasi UDP dapat dilihat pada standar ....", options: ["RFC 768", "RFC 867", "RFC667", "RFC 767"], answer: "RFC 768" },
            { question: "Aplikasi jaringan pada TCP yang digunakan sebagai protokol untuk melakukan transfer file adalah ....", options: ["Telnet", "FTP", "SMTP", "HTTP"], answer: "FTP" },
            { question: "Salah satu aplikasi yang digunakan untuk mengakses remote host melalui terminal yang interaktif adalah ....", options: ["TELNET", "FTP", "SMTP", "UDP"], answer: "TELNET" },
            { question: "Pada script di bawah ini penulisan 'in' mempunyai arti ....", options: ["Intranet", "Internet", "Internetworking", "Input"], answer: "Internet" },
            { question: "Fungsi perubahan network ke host dengan sistem short digunakan perintah ....", options: ["htons()", "htonl()", "ntohs()", "ntohl()"], answer: "ntohs()" },
            { question: "System call yang digunakan untuk mengakses suatu remote host adalah ....", options: ["socket", "bind", "connect", "listen"], answer: "connect" },
            { question: "System call yang digunakan untuk menunggu koneksi dari suatu host ....", options: ["listen", "accept", "send", "recy"], answer: "accept" },
            { question: "System call yang digunakan mengetahui informasi tentang tujuan adalah ....", options: ["recyfrom", "sendto", "close", "getpeername"], answer: "getpeername" },
            { question: "Pada script di bawah ini perintah h_aliases menunjukkan ....", options: ["nama resmi dari suatu host", "nama alternatif dari suatu host", "type dari alamat, contoh AF_INET", "panjang dari data alamat IP"], answer: "nama alternatif dari suatu host" },
            { question: "Contoh penggunaan inet_addr() yang benar adalah ....", options: ["inet_addr('10.252.102.23');", "addr.s_addr = inet_addr('10.252.102.23');", "ina.sin_addr.s_addr = inet_addr;", "ina.sin_addr.s_addr = inet_addr('10.252.102.23');"], answer: "ina.sin_addr.s_addr = inet_addr('10.252.102.23');" },
            { question: "Perbedaan antara SOCK_STREAM dan SOCK_DGRAM adalah ....", options: ["SOCK_STREAM digunakan apabila menggunakan protokol TCP", "SOCK_DGRAM digunakan untuk protokol TCP", "SOCK_STREAM digunakan apabila menggunakan protokol UDP", "Type berisikan SOCK_STREAM atau SOCK_DGRAM dan protocol berisikan angka 1"], answer: "SOCK_STREAM digunakan apabila menggunakan protokol TCP" },
            { question: "Pertukaran data protokol berbasis connectionless-oriented menggunakan fungsi ....", options: ["send()", "recv()", "sendto()", "close()"], answer: "sendto()" },
            { question: "Berikut yang merupakan nama domain untuk organisasi internasional adalah ....", options: ["com", "edu", "gov", "int"], answer: "int" },
            { question: "Singapura menggunakan nama domain dengan kode ....", options: ["sp", "sg", "SI", "sa"], answer: "sg" },
            { question: "Format dari resource record yang berfungsi untuk mengidentifikasikan nama protokol adalah ....", options: ["Nama", "TTL", "Class", "Tipe"], answer: "Tipe" },
            { question: "CNAME merupakan salah satu tipe dari resource record yang mempunyai arti ....", options: ["Canonical Name, nama alias dari suatu host", "CPU dan OS yang digunakan suatu host, bersifat komentar", "Nameserver yang memiliki authority untuk suatu domain", "Pointer untuk nama domain"], answer: "Canonical Name, nama alias dari suatu host" },
            { question: "Pesan DNS dikirimkan melalui UDP dan TCP menggunakan port ke ....", options: ["50", "51", "52", "53"], answer: "53" },
            { question: "Protokol yang digunakan untuk mengirimkan pesan kepada namaserver untuk mencatat IP dan nama host adalah ....", options: ["DHCP", "FTP", "IP", "UDP"], answer: "DHCP" },
            { question: "Sistem NIS yang berfungsi mengelola peta atau database dari password pengguna adalah ....", options: ["NIS master server", "NIS slave server", "NIS Client", "NIS Host"], answer: "NIS master server" },
            { question: "Untuk mengetahui lebih lengkap tentang DNS maka kita bisa melihat penjelasan tersebut pada ....", options: ["RFC 1035", "RFC 1036", "RFC 1037", "RFC 1038"], answer: "RFC 1035" },
            { question: "Tipe PRT pada resource record mempunyai arti ....", options: ["Mail Exchange untuk suatu domain", "Start of Authority", "Pointer untuk nama domain", "Canonical Name, nama alias dari suatu host"], answer: "Pointer untuk nama domain" },
            { question: "Nama domain yang menunjukkan arti organisasi non-profit adalah ....", options: ["org", "gov", "id", "net"], answer: "org" },
            { question: "Port yang digunakan untuk REXECD adalah ....", options: ["128", "256", "512", "650"], answer: "512" },
            { question: "Port yang digunakan untuk SSH adalah ....", options: ["22", "23", "24", "25"], answer: "22" },
            { question: "SSH mulai dikembangkan pada tahun ....", options: ["1992", "1993", "1994", "1995"], answer: "1994" },
            { question: "VNC pada Windows menggunakan port ....", options: ["5900", "5901", "5902", "5903"], answer: "5900" },
            { question: "Salah satu keunggulan penggunaan Remote Desktop Protocol adalah ....", options: ["mendukung penggunaan warna 32bit", "enkripsi 128bit", "File System Direction", "tidak berbagi sumber hard disk dengan komputer remote"], answer: "File System Direction" },
            { question: "TELNET merupakan standar protokol yang dijelaskan pada standar ....", options: ["RFC 855", "RFC 856", "RFC 857", "RFC 858"], answer: "RFC 855" },
            { question: "Port yang digunakan untuk RSHD adalah ....", options: ["512", "513", "514", "515"], answer: "512" },
            { question: "Penggunaan SSH yang digabungkan dengan SFTP dapat melakukan ....", options: ["transfer file", "mirror backup", "pengamanan data", "tunneling"], answer: "transfer file" },
            { question: "Salah satu keunggulan penggunaan VNC adalah ....", options: ["MIT License", "BSD License", "Unlicense", "GPL"], answer: "GPL" },
            { question: "Contoh aplikasi yang bisa digunakan untuk Remote Desktop Protocol adalah ....", options: ["TeamViewer", "Filezilla", "XAMPP", "AeroClien"], answer: "TeamViewer" },
            { question: "FTP menggunakan TCP dengan menggunakan port ....", options: ["20 dan 21", "22 dan 23", "20 dan 22", "21 dan 23"], answer: "20 dan 21" },
            { question: "Ketika melakukan login TELNET pada FTP menggunakan port ....", options: ["19", "20", "21", "22"], answer: "20" },
            { question: "Perintah operasional yang digunakan untuk mengambil file pada FTP adalah ....", options: ["dir", "ls", "get", "mget"], answer: "get" },
            { question: "Perintah operasional yang digunakan untuk menunjuk ke direktori yang dituju adalah ....", options: ["open", "cd", "dir", "ls"], answer: "cd" },
            { question: "Ketika TFTP melakukan inisialisasi dengan mengirimkan permintaan maka operasi tersebut menggunakan port ....", options: ["66", "67", "68", "69"], answer: "69" },
            { question: "Standar FTP dijelaskan juga pada ....", options: ["FC 949", "FC 969", "FC 959", "FC 929"], answer: "FC 959" },
            { question: "Mekanisme yang bisa dilakukan untuk melakukan transfer file ada ....", options: ["1", "2", "3", "4"], answer: "3" },
            { question: "Operasi yang digunakan untuk mengambil file dengan jumlah lebih dari satu adalah ....", options: ["get", "mget", "put", "cd"], answer: "mget" },
            { question: "Sebuah perintah pada TFTP yang berfungsi untuk menentukan mode pengiriman adalah ....", options: ["Connect <host>", "Mode <ascii/binary>", "Get <nama file remote> [<nama file lokal>]", "Verbose"], answer: "Mode <ascii/binary>" },
            { question: "Sebuah perintah pada TFTP yang berfungsi untuk menentukan tujuan adalah ....", options: ["Connect <host>", "Mode <ascii/binary>", "Get <nama file remote> [<nama file lokal>]", "Verbose"], answer: "Connect <host>" },
            { question: "Port yang digunakan oleh SMTP untuk melayani pengguna adalah ....", options: ["23", "24", "25", "26"], answer: "25" },
            { question: "Header yang biasanya digunakan untuk tujuan kedua dari email (carbon-copy) adalah ....", options: ["to", "cc", "reply-to", "return-path"], answer: "cc" },
            { question: "Port yang digunakan POP3 untuk melayani pengguna adalah port ....", options: ["100", "110", "120", "130"], answer: "110" },
            { question: "Protokol yang didisain untuk pengguna dengan jaringan yang sebentar-bentar harus dimatikan adalah ....", options: ["SMTP", "POP3", "IMAP", "MIME"], answer: "POP3" },
            { question: "Metode yang digunakan untuk pengiriman pada email adalah ....", options: ["8bit", "quoted-printable", "base128", "digest"], answer: "quoted-printable" },
            { question: "Standar untuk pertukaran email antar komputer atau standar SMTP terdapat pada ....", options: ["RFC 820", "RFC 821", "RFC 921", "RFC 830"], answer: "RFC 821" },
            { question: "Port yang digunakan IMAP dalam proses pengiriman email adalah ....", options: ["110", "145", "143", "146"], answer: "143" },
            { question: "Port yang digunakan SMTP dalam proses pengiriman email adalah ....", options: ["22", "23", "24", "25"], answer: "25" },
            { question: "E-mail adalah singkatan dari ....", options: ["Elektric Mail", "Extra Mail", "Elektronic Mail", "Elect Mail"], answer: "Elektronic Mail" },
            { question: "Penulisan alamat e-mail yang benar adalah ....", options: ["Siswa yahoo.com", "Siswa $yahoo.com", "siswa @yahoo.com", "siswa@yahoo.com"], answer: "siswa@yahoo.com" },
            { question: "World Wide Web pertama kali dikembangkan pada tahun ....", options: ["1989", "1991", "1992", "1993"], answer: "1989" },
            { question: "Jenis web browser berbasis grafik user interface bernama ....", options: ["NCSA", "Mosaic", "Particle Physic", "Berners Lee"], answer: "Mosaic" },
            { question: "Metode yang digunakan untuk transfer suatu informasi melalui World Wide Web adalah ....", options: ["HTTP", "FTP", "MIME", "SMTP"], answer: "HTTP" },
            { question: "Request method yang berfungsi meminta sumber daya yang spesifik, dan digunakan untuk mengakses halaman web adalah ....", options: ["HEAD", "GET", "POST", "PUT"], answer: "GET" },
            { question: "Kode status yang menunjukkan not found adalah ....", options: ["401", "402", "403", "404"], answer: "404" },
            { question: "Kode status yang menunjukkan internal server error adalah ....", options: ["500", "501", "502", "503"], answer: "500" },
            { question: "Web browser yang dikeluarkan oleh Macintosh adalah ....", options: ["Opera", "Apple Safari", "Mozilla", "Netscape"], answer: "Apple Safari" },
            { question: "Fitur fundamental yang harus didukung web browser antara lain ....", options: ["autocompletition dari URL", "filter iklan", "book mark", "cookie"], answer: "book mark" },
            { question: "Fasilitas penghilang pengganggu yang harus dimiliki oleh web browser adalah ....", options: ["HTML, XML dan XHTML", "Navigasi spasial", "Screen Reader", "Pop-Up advertisement"], answer: "Pop-Up advertisement" },
            { question: "Request method yang digunakan untuk proxy apabila mengakses suatu site yang mendukung SSL adalah ....", options: ["DELETE", "TRACE", "OPTIONS", "CONNECT"], answer: "CONNECT" },
            { question: "SNMP termasuk contoh protokol yang berada pada layer ke ....", options: ["4", "5", "6", "7"], answer: "7" },
            { question: "Perangkat lunak pada SNMP yang bertujuan untuk merespon permintaan dari SNMP dari management station adalah ....", options: ["Master Agent", "Subagent", "Manajemen Station", "MIB"], answer: "Subagent" },
            { question: "PDU dari SNMP yang digunakan untuk melakukan perubahan terhadap subsistem adalah ....", options: ["GET REQUEST", "GETNEXT REQUEST", "GET RESPONSE", "SET"], answer: "SET" },
            { question: "Ketika berjalan, SNMP membutuhkan port pada UDP, port yang digunakan untuk manajer adalah ....", options: ["161", "162", "163", "164"], answer: "161" },
            { question: "Simple Network Management Protocol version 3 dikeluarkan pada tahun ....", options: ["2001", "2002", "2003", "2004"], answer: "2003" },
            { question: "Perangkat lunak yang berjalan pada perangkat yang mendukung SNMP dan mengimplementasikan MIB adalah ....", options: ["Master Agent", "Subagent", "Manajemen Station", "MIS"], answer: "Subagent" },
            { question: "PDU dari SNMP yang digunakan untuk melakukan pelaporan terhadap subsistem manajemen adalah ....", options: ["TRAP", "GETNEXT REQUEST", "GET RESPONSE", "SET"], answer: "TRAP" },
            { question: "RFC untuk SNMP yang mempunyai kode RFC 1067 dikenal dengan nama ....", options: ["Management information base for network management of TCP/IP-based internets", "A Simple Network Management Protocol", "Structure and identification of management information for TCP/IP-based internets", "Management information base for network management of TCP/IP-based internets"], answer: "A Simple Network Management Protocol" },
            { question: "Contoh SNMP yang digunakan untuk berkomunikasi antara manajement station adalah ....", options: ["console", "router", "gateway", "switch"], answer: "router" },
            { question: "Router Graphing Software umumnya digunakan untuk menampilkan informasi pada suatu alat jaringan seperti ....", options: ["router", "hub", "modem", "access point"], answer: "router" },
            { question: "Jaringan komputer yang menghubungkan beberapa perangkat dengan menggunakan distribusi nirkabel adalah ....", options: ["MAC", "WLAN", "PHY", "WNIC"], answer: "WLAN" },
            { question: "Teknologi yang digunakan dalam Wireless Local Area Network adalah ....", options: ["Spread-spectrum", "IEEE 802.11", "PHY", "WNIC"], answer: "IEEE 802.11" },
            { question: "Sebuah standardisasi yang mengatur Media Access Control dan Layer Fisik untuk implementasi WLAN adalah ....", options: ["ISO 9001", "ISO 27001", "IEEE 802.11", "Tidak ada jawaban yang benar"], answer: "IEEE 802.11" },
            { question: "Teknologi WLAN pada tahun 2009 menggunakan protokol ....", options: ["802.11a", "802.11b", "802.11g", "802.11n"], answer: "802.11n" },
            { question: "Teknologi WLAN dengan protokol 802.11ac memiliki spesifikasi ....", options: ["Data rate 54 Mbps", "Frekuensi 2.4 GHz", "Modulasi 256 QAM", "Antena 1x1 SISO"], answer: "Modulasi 256 QAM" },
            { question: "Sekumpulan station yang dapat berkomunikasi satu dengan lainnya pada jaringan nirkabel yang sama adalah ....", options: ["station", "basic service set", "extended service set", "access point"], answer: "basic service set" },
            { question: "Sebuah komponen yang melengkapi setiap station adalah ....", options: ["spread-spectrum", "IEEE 802.11", "PHY", "WNIC"], answer: "WNIC" },
            { question: "Dalam arsitektur WLAN, terdapat perangkat nirkabel yang digunakan untuk menyambungkan jaringan kabel dengan jaringan nirkabel, yaitu ....", options: ["access point", "wireless NIC", "antena", "signal splitter"], answer: "access point" },
            { question: "Perangkat yang digunakan di sisi penerima yang berupa wireless PCMCIA, Wireless PCI, Wireless USB adalah ....", options: ["Amplifier", "PoE", "CATS", "Wireless NIC"], answer: "Wireless NIC" },
            { question: "Sistem autentikasi dalam keamanan WLAN menggunakan ....", options: ["RADIUS", "WLAN security", "Amplifier", "Lightning Protector"], answer: "RADIUS" }
        ];

        let autoRevealEnabled = false; // State for auto-reveal feature

        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }

        function loadRandomQuestions() {
            shuffleArray(allQuestions);
            const selectedQuestions = allQuestions.slice(0, 50);
            const questionsContainer = document.getElementById('questions-container');
            questionsContainer.innerHTML = ''; // Clear previous questions

            selectedQuestions.forEach((q, index) => {
                const questionCard = document.createElement('div');
                questionCard.classList.add('question-card');
                questionCard.innerHTML = `<p>${index + 1}. ${q.question}</p><ul></ul><div class="answer-reveal" style="display:none;">Jawaban: <strong>${q.answer}</strong></div>`;

                const optionsList = questionCard.querySelector('ul');
                shuffleArray(q.options); // Shuffle options for each question
                q.options.forEach(option => {
                    const listItem = document.createElement('li');
                    listItem.textContent = option;
                    listItem.onclick = () => selectOption(listItem, q.answer);
                    optionsList.appendChild(listItem);
                });
                questionsContainer.appendChild(questionCard);

                // If auto-reveal is enabled, show answer immediately
                if (autoRevealEnabled) {
                    showAnswer(questionCard, q.answer);
                }
            });
        }

        function selectOption(selectedListItem, correctAnswer) {
            const parentUl = selectedListItem.parentElement;
            const questionCard = parentUl.closest('.question-card'); // Get the parent question-card
            const answerRevealDiv = questionCard.querySelector('.answer-reveal');

            // Remove previous selections and feedback for THIS question
            Array.from(parentUl.children).forEach(li => {
                li.classList.remove('selected', 'correct', 'incorrect');
            });

            // Mark selected option
            selectedListItem.classList.add('selected');

            // Apply correct/incorrect styling
            if (selectedListItem.textContent === correctAnswer) {
                selectedListItem.classList.add('correct');
            } else {
                selectedListItem.classList.add('incorrect');
            }

            // Show answer
            answerRevealDiv.style.display = 'block';
        }

        function showAnswer(questionCard, correctAnswer) {
            const optionsList = questionCard.querySelector('ul');
            const answerRevealDiv = questionCard.querySelector('.answer-reveal');

            // Ensure previous selections/feedback are cleared before revealing
            Array.from(optionsList.children).forEach(li => {
                li.classList.remove('selected', 'correct', 'incorrect');
            });

            // Find and mark the correct option
            Array.from(optionsList.children).forEach(li => {
                if (li.textContent === correctAnswer) {
                    li.classList.add('correct');
                }
            });

            // Display the answer reveal div
            answerRevealDiv.style.display = 'block';
        }


        function toggleAutoReveal() {
            autoRevealEnabled = !autoRevealEnabled; // Toggle the state
            const button = document.querySelector('.button-group button:last-child'); // Get the 'Tampilkan Semua Jawaban' button
            if (autoRevealEnabled) {
                button.textContent = '🙈 Sembunyikan Semua Jawaban';
                // Iterate through all questions and show answers
                document.querySelectorAll('.question-card').forEach(card => {
                    const questionText = card.querySelector('p').textContent;
                    // Extract the question part without the number
                    const cleanedQuestion = questionText.substring(questionText.indexOf('.') + 2).trim();
                    const questionData = allQuestions.find(q => q.question === cleanedQuestion);
                    if (questionData) {
                        showAnswer(card, questionData.answer);
                    }
                });
            } else {
                button.textContent = '👁️ Tampilkan Semua Jawaban';
                // Iterate through all questions and hide answers
                document.querySelectorAll('.question-card').forEach(card => {
                    card.querySelector('.answer-reveal').style.display = 'none';
                    // Also clear correct/incorrect styling
                    Array.from(card.querySelectorAll('li')).forEach(li => {
                        li.classList.remove('selected', 'correct', 'incorrect');
                    });
                });
            }
        }

        // Load questions when the page loads
        document.addEventListener('DOMContentLoaded', loadRandomQuestions);
    </script>
</body>
</html>
