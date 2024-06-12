class Hasta:
    def __init__(self, hasta_no, ad, soyad, dogum_tarihi, hastalik, tedavi):
        self.__hasta_no = hasta_no
        self.__ad = ad
        self.__soyad = soyad
        self.__dogum_tarihi = dogum_tarihi
        self.__hastalik = hastalik
        self.__tedavi = tedavi
      

    def get_hasta_no(self):
        return self.__hasta_no

    def set_hasta_no(self, hasta_no):
        self.__hasta_no = hasta_no

    def get_ad(self):
        return self.__ad

    def set_ad(self, ad):
        self.__ad = ad

    def get_soyad(self):
        return self.__soyad

    def set_soyad(self, soyad):
        self.__soyad = soyad

    def get_dogum_tarihi(self):
        return self.__dogum_tarihi

    def set_dogum_tarihi(self, dogum_tarihi):
        self.__dogum_tarihi = dogum_tarihi

    def get_hastalik(self):
        return self.__hastalik

    def set_hastalik(self, hastalik):
        self.__hastalik = hastalik

    def get_tedavi(self):
        return self.__tedavi

    def set_tedavi(self, tedavi):
        self.__tedavi = tedavi

    def tedavi_suresi_hesapla(self):
        # Tedavi süresini hesaplamak için gereken kodu buraya yazabilirsiniz
        # Örneğin:
        return len(self.__tedavi) * 2  # Tedavi süresini tedavi uzunluğunun iki katı olarak hesaplar


    def __str__(self):
        return f"Hasta No: {self.__hasta_no}\nAd: {self.__ad}\nSoyad: {self.__soyad}\nDoğum Tarihi: {self.__dogum_tarihi}\nHastalık: {self.__hastalik}\nTedavi: {self.__tedavi}\n"


# Test
if __name__ == "__main__":
    hasta1 = Hasta("1234", "Ali", "Yılmaz", "01/01/1980", "Ateş", "Antibiyotik")
    print(hasta1.tedavi_suresi_hesapla())
    print(hasta1)
    print("Tedavi Süresi:", hasta1.tedavi_suresi_hesapla())
