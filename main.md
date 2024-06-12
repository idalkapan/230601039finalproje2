from Personel import Personel
from Doktor import Doktor
from Hemsire import Hemsire
from Hasta import Hasta
import pandas as pd

try:
    # Personel sınıfı için örnekler oluşturulması
    personel1 = Personel("001", "Ahmet", "Yılmaz", "Muhaberat", 8000)
    personel2 = Personel("002", "Ayşe", "Kaya", "Cerrahi", 6000)

    # Doktor sınıfı için örnekler oluşturulması
    doktor1 = Doktor("101", "Mehmet", "Demir", "Cerrahi", 12000, "Kardiyoloji", 10, "Memorial Hastanesi")
    doktor2 = Doktor("102", "Fatma", "Yılmaz", "Dahiliye", 16000, "Göğüs Hastalıkları", 8, "City Hospital")
    doktor3 = Doktor("103", "Ali", "Kara", "KBB", 25000, "Kulak Burun Boğaz", 3, "City Hospital")

    # Hemşire sınıfı için örnekler oluşturulması
    hemsire1 = Hemsire("201", "Ayşegül", "Yıldız", "Acil", 4000, 40, "İlkyardım", "City Hospital")
    hemsire2 = Hemsire("202", "Murat", "Çelik", "Yoğun Bakım", 4500, 36, "Yoğun Bakım", "Memorial Hastanesi")
    hemsire3 = Hemsire("203", "Zeynep", "Arslan", "Cerrahi", 4200, 38, "Hasta Bakım", "City Hospital")

    # Hasta sınıfı için örnekler oluşturulması
    hasta1 = Hasta("111", "Kübra", "Yıldırım", "01/01/1980", "Ateş", "Antibiyotik")
    hasta2 = Hasta("222", "Selin", "Kaya", "15/03/1995", "Baş Ağrısı", "Ağrı Kesici")
    hasta3 = Hasta("333", "Mehmet", "Demir", "10/07/1988", "Yüksek Tansiyon", "Tansiyon İlacı")

    # DataFrame oluşturulması
    data = {
        "Hasta No": [hasta1.get_hasta_no(), hasta2.get_hasta_no(),hasta3.get_hasta_no()],
        "Hasta Adı": [hasta1.get_ad(), hasta2.get_ad(), hasta3.get_ad()],
        "Hasta Soyadı": [hasta1.get_soyad(), hasta2.get_soyad(), hasta3.get_soyad()],
        "Doğum Tarihi": [hasta1.get_dogum_tarihi(), hasta2.get_dogum_tarihi(), hasta3.get_dogum_tarihi()],
        "Hastalık": [hasta1.get_hastalik(), hasta2.get_hastalik(), hasta3.get_hastalik()],
        "Tedavi": [hasta1.get_tedavi(), hasta2.get_tedavi(), hasta3.get_tedavi()],
        "Departman": [0, 0, 0], # Boş olan ücret alanlarına sıfır atama
        "Çalışma Saati":[0,0,0],
        "Uzmanlık":[0,0,0],
        "Hatane":[0,0,0], 
        "Tedavi Süresi": [hasta1.tedavi_suresi_hesapla(), hasta2.tedavi_suresi_hesapla(), hasta3.tedavi_suresi_hesapla()]


    }

    df = pd.DataFrame(data)

    # Hasta adına göre DataFrame'i alfabetik olarak sıralama
    df_hasta_sirali = df.sort_values(by=["Hasta Adı", "Hasta Soyadı"])
    print("\nSıralanmamış DataFrame:")
    print(df)


except Exception as e:
    print(f"Hata oluştu: {e}")

try:
    # Doktor uzmanlık alanına göre toplam sayıların hesaplanması
    uzmanliklar = [doktor1.get_uzmanlik(), doktor2.get_uzmanlik(), doktor3.get_uzmanlik()]
    uzmanlik_sayisi = {}
    for uzmanlik in uzmanliklar:
        if uzmanlik in uzmanlik_sayisi:
            uzmanlik_sayisi[uzmanlik] += 1
        else:
            uzmanlik_sayisi[uzmanlik] = 1

    print("\nDoktorların Uzmanlık Alanlarına Göre Toplam Sayılar:")
    for uzmanlik, sayi in uzmanlik_sayisi.items():
        print(f"{uzmanlik}: {sayi} doktor")

except Exception as e:
    print(f"Hata oluştu: {e}")

try:
    # 5 yıldan fazla deneyime sahip doktor sayısının hesaplanması
    deneyim_yili = sum(d.get_deneyim_yili() > 5 for d in [doktor1, doktor2, doktor3])
    print(f"\nToplam 5 Yıldan Fazla Deneyime Sahip Doktor Sayısı: {deneyim_yili}")

except Exception as e:
    print(f"Hata oluştu: {e}")

try:
    # Personel Bilgileri
    personeller = [personel1, personel2]

    # Personel maaşı 7000 TL üzerinde olanların bilgilerini içeren bir liste oluşturma
    yuksek_maas_personeller = [p for p in personeller if p.get_maas() > 7000]
    
    # Sonuçları yazdırma
    print("\nMaaşı 7000 TL Üzerinde Olan Personellerin Bilgileri:")
    for personel in yuksek_maas_personeller:
        print(f"Personel No: {personel.get_personel_no()}, Ad: {personel.get_ad()}, Soyad: {personel.get_soyad()}, Departman: {personel.get_departman()}, Maaş: {personel.get_maas()}\n")
        
except Exception as e:
    print(f"Hata oluştu: {e}")

try:
    # Doğum tarihi 1990 ve sonrası olan hastaların bilgilerini içeren bir liste oluşturma
    genc_hastalar = [hasta for hasta in [hasta1, hasta2, hasta3] if int(hasta.get_dogum_tarihi()[-4:]) >= 1990]
    
    # Sonuçları yazdırma
    print("\nDoğum Tarihi 1990 ve Sonrası Olan Hastaların Bilgileri:")
    for hasta in genc_hastalar:
        print(f"Hasta No: {hasta.get_hasta_no()},Hasta Adı: {hasta.get_ad()}, Hasta Soyadı: {hasta.get_soyad()}, Doğum Tarihi: {hasta.get_dogum_tarihi()}, Hastalık: {hasta.get_hastalik()}, Tedavi: {hasta.get_tedavi()}\n")
        
    print("Hasta Adına Göre Alfabetik Sıralanmış Yeni DataFrame:\n")
    print(df_hasta_sirali)    
except Exception as e:
    print(f"Hata oluştu: {e}")

  
