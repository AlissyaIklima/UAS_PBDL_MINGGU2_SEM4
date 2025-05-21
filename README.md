# UAS_PBDL_MINGGU2_SEM4

# UAS latihan_soal

CREATE TABLE customer (
id_customer VARCHAR(7) NOT NULL,
nama_customer VARCHAR(30) NOT NULL,
alamat_customer VARCHAR(50),
kota_customer VARCHAR(15),
telp_customer VARCHAR(15),
PRIMARY KEY (id_customer)
);

CREATE TABLE produsen (
id_produsen VARCHAR(7) NOT NULL,
nama_produsen VARCHAR(30) NOT NULL,
alamat_produsen VARCHAR(50),
kota_produsen VARCHAR(50),
telepon_produsen VARCHAR(15),
email_produsen VARCHAR(30),
PRIMARY KEY (id_produsen)
);

CREATE TABLE pemasok (
id_pemasok VARCHAR(6) NOT NULL,
nama_pemasok VARCHAR(20) NOT NULL,
alamat_pemasok VARCHAR(50) NOT NULL,
kota_pemasok VARCHAR(15),
email_pemasok VARCHAR(50),
PRIMARY KEY (id_pemasok)
);

CREATE TABLE barang (
id_barang VARCHAR(7) NOT NULL,
nama_barang VARCHAR(50) NOT NULL,
tahun_produksi YEAR(4) NOT NULL,
id_produsen VARCHAR(7) NOT NULL,
id_pemasok VARCHAR(6) NOT NULL,
PRIMARY KEY (id_barang),
FOREIGN KEY (id_produsen) REFERENCES produsen(id_produsen),
FOREIGN KEY (id_pemasok) REFERENCES pemasok(id_pemasok)
);

CREATE TABLE detail_barang (
id_barang VARCHAR(7) NOT NULL,
kategori_barang VARCHAR(25) NOT NULL,
jumlah SMALLINT(3) NOT NULL,
harga_pembelian INT NOT NULL,
FOREIGN KEY (id_barang) REFERENCES barang(id_barang)
);

CREATE TABLE pembelian (
id_pembelian VARCHAR(6) NOT NULL,
tgl_pembelian DATE NOT NULL,
id_customer VARCHAR(7) NOT NULL,
PRIMARY KEY (id_pembelian),
FOREIGN KEY (id_customer) REFERENCES customer(id_customer)
);

CREATE TABLE detail_pembelian (
id_pembelian VARCHAR(6) NOT NULL,
id_barang VARCHAR(7) NOT NULL,
status_pembelian VARCHAR(10) NOT NULL,
FOREIGN KEY (id_pembelian) REFERENCES pembelian(id_pembelian),
FOREIGN KEY (id_barang) REFERENCES barang(id_barang)
);

INSERT INTO customer (id_customer, nama_customer, alamat_customer, kota_customer, telp_customer)
VALUES
('A.1.001', 'Ronaldo', 'Jl. Kalimantan No.15', 'Yogyakarta', '543210'),
('A.1.002', 'Messi', 'Jl. Sulawesi No.25', 'Yogyakarta', '567890'),
('A.1.003', 'Bale', 'Jl. Arimbi No.18', 'Semarang', '565755'),
('A.1.004', 'Mbappe', 'Jl. Kurawa No.19', 'Surakarta', '435678'),
('A.1.005', 'Salah', 'Jl. Pandawa No.27', 'Surakarta', '765747'),
('A.1.006', 'Kane', 'Jl. Drupadi No.07', 'Semarang', '895647'),
('A.1.007', 'Modric', 'Jl. Sumatera No.12', 'Yogyakarta', '768584');

INSERT INTO produsen (id_produsen, nama_produsen, alamat_produsen, kota_produsen, telepon_produsen, email_produsen)
VALUES
('T1.01', 'PT Petkasa', 'Jl. Bromo no.10', 'Jakarta', '9534638', 'admin@petkasa.com'),
('T1.02', 'PT Jaya', 'Jl. Merapi no.5', 'Bandung', '9508867', 'admin@jaya.com'),
('T1.03', 'PT Makmur', 'Jl. Jaya Wijaya no.78', 'Jakarta', '58786676', 'kontak@makmur.com'),
('T1.04', 'PT Mandiri', 'Jl. Sunbing no.3', 'Bekasi', '65876746', 'sales@mandiri.com'),
('T1.05', 'PT Untung', 'Jl. Merhabu no.24', 'Bekasi', '33765748', 'kontak@untung.com');
    
INSERT INTO pemasok (id_pemasok, nama_pemasok, alamat_pemasok, kota_pemasok, email_pemasok)
VALUES
('P001', 'CV Cahaya', 'Jl. Mangkubumi no.16', 'Yogyakarta', 'panglima@cahaya.com'),
('P002', 'CV Matahari', 'Jl. Diponegoro no.65', 'Semarang', 'kasal@matahari.com'),
('P003', 'CV Bulan', 'Jl. Veteran no.85', 'Jakarta', 'letnan@bulan.com'),
('P004', 'CV Bintang', 'Jl. Soekarno no.35', 'Yogyakarta', 'kopral@bintang.com'),
('P005', 'CV Bumi', 'Jl. Supratman no.24', 'Semarang', 'prajurit@bumi.com'),
('P006', 'CV Laut', 'Jl. Radjiman no.14', 'Bandung', 'jendral@laut.com');

INSERT INTO barang (id_barang, nama_barang, tahun_produksi, id_produsen, id_pemasok)
VALUES
('B.2.001', 'Kemeja', 2018, 'T1.01', 'P002'),
('B.2.002', 'Gamis', 2018, 'T1.02', 'P001'),
('B.2.003', 'Mukena', 2016, 'T1.01', 'P003'),
('B.2.004', 'Seragam Sekolah', 2017, 'T1.01', 'P003'),
('B.2.005', 'Topi', 2017, 'T1.02', 'P004'),
('B.2.006', 'Panci', 2017, 'T1.03', 'P002');
    
INSERT INTO detail_barang (id_barang, kategori_barang, jumlah, harga_pembelian)
VALUES
('B.2.001', 'Fashion Pria', 5, 50000),
('B.2.002', 'Fashion Wanita', 4, 100000),
('B.2.003', 'Fashion Muslim', 5, 120000),
('B.2.004', 'Fashion Anak', 7, 80000),
('B.2.005', 'Aksesoris', 5, 30000),
('B.2.006', 'Dapur', 5, 150000);

INSERT INTO pembelian (id_pembelian, tgl_pembelian, id_customer)
VALUES
('S.101', '2016-02-03', 'A.1.002'),
('S.102', '2016-02-03', 'A.1.004'),
('S.103', '2016-02-05', 'A.1.003'),
('S.104', '2016-02-06', 'A.1.005');
    
INSERT INTO detail_pembelian (id_pembelian, id_barang, status_pembelian)
VALUES
('S.101', 'B.2.001', 'tunai'),
('S.102', 'B.2.006', 'tunai'),
('S.102', 'B.2.002', 'tunai'),
('S.102', 'B.2.003', 'kredit'),
('S.103', 'B.2.004', 'kredit'),
('S.104', 'B.2.005', 'kredit');

1. Buatlah trigger untuk mengurangi stock saat terjadi pembelian. Tampilkan !

DELIMITER //
CREATE TRIGGER pembelian
AFTER INSERT ON detail_pembelian
FOR EACH ROW
BEGIN

UPDATE detail_barang 
SET jumlah = jumlah - 1
WHERE id_barang = NEW.id_barang;

END //
DELIMITER ;

2. Buatlah trigger untuk menambah stock saat terjadi penjualan Tampilkan !

CREATE TABLE penjualan (
id_penjualan VARCHAR(7) NOT NULL,
id_pemasok VARCHAR(6) NOT NULL,
id_barang VARCHAR(7) NOT NULL,
jumlah INT NOT NULL,
PRIMARY KEY (id_penjualan),
FOREIGN KEY (id_pemasok) REFERENCES pemasok(id_pemasok),
FOREIGN KEY (id_barang) REFERENCES barang(id_barang)
);

DELIMITER //

CREATE TRIGGER penjualan
AFTER INSERT ON penjualan
FOR EACH ROW
BEGIN

UPDATE detail_barang
SET jumlah = jumlah + NEW.jumlah
WHERE id_barang = NEW.id_barang;

END //

DELIMITER ;

3. Buatlah trigger untuk menjumlahkan harga barang saat terjadi pembelian. Tampilkan !

ALTER TABLE pembelian ADD COLUMN total_harga INT DEFAULT 0;

DELIMITER //

CREATE TRIGGER update_total_harga
AFTER INSERT ON detail_pembelian
FOR EACH ROW
BEGIN

DECLARE total INT;

SELECT SUM(db.harga_pembelian)
INTO total
FROM detail_pembelian dp
JOIN detail_barang db ON dp.id_barang = db.id_barang
WHERE dp.id_pembelian = NEW.id_pembelian;

UPDATE pembelian
SET total_harga = IFNULL(total, 0)
WHERE id_pembelian = NEW.id_pembelian;

END //

DELIMITER ;

4. Buatlah fungsi untuk menghitung jumlah barang yang diproduksi tahun 2017. Tampilkan !

DELIMITER //
CREATE FUNCTION jumlah_barang_2017()
RETURNS INT
DETERMINISTIC
BEGIN

DECLARE total INT;
SELECT COUNT(*) INTO total FROM barang WHERE tahun_produksi = 2017;
RETURN total;

END //
DELIMITER ;


5. Buatlah fungsi untuk menghitung jumlah custumer dari kota Yogyakarta.Tampilkan !

DELIMITER //

CREATE FUNCTION jumlah_customer_yogyakarta()
RETURNS INT
DETERMINISTIC
BEGIN

DECLARE total INT;
SELECT COUNT(*) INTO total FROM customer WHERE kota_customer = 'Yogyakarta';
RETURN total;

END //

DELIMITER ;


6. Buatlah prosedur untuk mengupdate stock / jumlah barang. Tampilkan !

DELIMITER //

CREATE PROCEDURE update_stok_barang(
IN baru_id_barang VARCHAR(7),
IN baru_jumlah INT
)
BEGIN

UPDATE detail_barang
SET jumlah = baru_jumlah
WHERE id_barang = baru_id_barang;

END //

DELIMITER ;


7. Buatlah prosedur untuk menampilkan nama barang, katagori barang berdasarkan tahun produksi. Tampilkan !

DELIMITER //

CREATE PROCEDURE barang_per_tahun(IN tahun YEAR)
BEGIN

SELECT b.nama_barang, d.kategori_barang
FROM barang b
JOIN detail_barang d ON b.id_barang = d.id_barang
WHERE b.tahun_produksi = tahun;

END //

DELIMITER ;


8. Buatlah fungsi untuk menampilkan barang dan pajak pembelian untuk setiap barang. Pajak pembelian dihitung dengan Harga = Harga – (Harga * 11%). Tampilkan!

DELIMITER //

CREATE FUNCTION harga_setelah_pajak(harga INT)
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN

RETURN harga - (harga * 0.11);

END //

DELIMITER ;

SELECT 
id_barang, harga_pembelian, harga_setelah_pajak(harga_pembelian) AS harga_setelah_pajak
FROM detail_barang;



9. Buatlah fungsi untuk menampilkan barang jika stock kurang dari 2 maka akan tampil keterangan stock limit, jika lebih dari sama dengan dua maka akan tampil keterangan stock aman. Tampilkan!

DELIMITER //

CREATE FUNCTION status_stok(p_jumlah INT)
RETURNS VARCHAR(20)
DETERMINISTIC
BEGIN
IF p_jumlah < 2 THEN RETURN 'Stock Limit';
ELSE RETURN 'Stock Aman';
END IF;
END //

DELIMITER ;

SELECT 
id_barang, jumlah, status_stok(jumlah) AS keterangan
FROM detail_barang;

10. Buatlah prosedur untuk menghitung luas lingkaran. Tampilkan!

DELIMITER //
CREATE PROCEDURE luas_lingkaran(
IN jari2 DOUBLE, 
OUT luas DOUBLE
)
BEGIN

SET luas = 3.14 * jari2 * jari2;

END //
DELIMITER ;

CALL luas_lingkaran(10, @hasil);
SELECT @hasil;


11. Hapus Database lalu tampilkan !

HAPUS DEWEK
