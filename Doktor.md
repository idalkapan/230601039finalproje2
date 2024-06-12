from Personel import Personel  # Personel sınıfını içe aktarıyoruz

class Doktor(Personel):
    def __init__(self, personel_no, ad, soyad, departman, maas, uzmanlik, deneyim_yili, hastane):
        super().__init__(personel_no, ad, soyad, departman, maas)
        self.__uzmanlik = uzmanlik
        self.__deneyim_yili = deneyim_yili
        self.__hastane = hastane

    def get_uzmanlik(self):
        return self.__uzmanlik

    def set_uzmanlik(self, uzmanlik):
        self.__uzmanlik = uzmanlik

    def get_deneyim_yili(self):
        return self.__deneyim_yili

    def set_deneyim_yili(self, deneyim_yili):
        self.__deneyim_yili = deneyim_yili

    def get_hastane(self):
        return self.__hastane

    def set_hastane(self, hastane):
        self.__hastane = hastane

    def maas_arttir(self, yuzde):
        self.set_maas(self.get_maas() * (1 + yuzde / 100))

    def __str__(self):
        return f"Personel No: {self.get_personel_no()}\nAd: {self.get_ad()}\nSoyad: {self.get_soyad()}\nDepartman: {self.get_departman()}\nMaaş: {self.get_maas()}\nUzmanlık: {self.__uzmanlik}\nDeneyim Yılı: {self.__deneyim_yili}\nHastane: {self.__hastane}"


# Test
if __name__ == "__main__":
    doktor1 = Doktor("456", "Ayşe", "Kaya", "Cerrahi", 8000, "Kalp Cerrahisi", 10, "Memorial Hastanesi")
    print(doktor1)
