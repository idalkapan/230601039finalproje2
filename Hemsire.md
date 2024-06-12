from Personel import Personel  # Personel sınıfını içe aktarıyoruz

class Hemsire(Personel):
    def __init__(self, personel_no, ad, soyad, departman, maas, calisma_saati, sertifika, hastane):
        super().__init__(personel_no, ad, soyad, departman, maas)
        self.__calisma_saati = calisma_saati
        self.__sertifika = sertifika
        self.__hastane = hastane

    def get_calisma_saati(self):
        return self.__calisma_saati

    def set_calisma_saati(self, calisma_saati):
        self.__calisma_saati = calisma_saati

    def get_sertifika(self):
        return self.__sertifika

    def set_sertifika(self, sertifika):
        self.__sertifika = sertifika

    def get_hastane(self):
        return self.__hastane

    def set_hastane(self, hastane):
        self.__hastane = hastane

    def maas_arttir(self, yuzde):
        self.set_maas(self.get_maas() * (1 + yuzde / 100))

    def __str__(self):
        return f"Personel No: {self.get_personel_no()}\nAd: {self.get_ad()}\nSoyad: {self.get_soyad()}\nDepartman: {self.get_departman()}\nMaaş: {self.get_maas()}\nÇalışma Saati: {self.__calisma_saati}\nSertifika: {self.__sertifika}\nHastane: {self.__hastane}"


# Test
if __name__ == "__main__":
    hemsire1 = Hemsire("789", "Fatma", "Yılmaz", "Acil", 6000, 40, "İlkyardım", "City Hospital")
    print(hemsire1)
