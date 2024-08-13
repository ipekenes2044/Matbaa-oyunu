import time

class Makine():
    def __init__(self):
        self.devir = 0
        self.mürekkep = 100
        self.şarj = 100
        self.dergiler = []

    def çalış(self):
        if self.mürekkep <= 0:
            print("Hata! Mürekkep yetersiz!")
            time.sleep(2)
        elif self.şarj <= 0:
            print("Hata! Şarj yetersiz!")
            time.sleep(2)
        else:
            self.devir += 1
            if (self.mürekkep<3):
                self.mürekkep = 0
            else:
                self.mürekkep -= 3
            if  (self.şarj<6):
                self.şarj = 0
            else:
                self.şarj -= 6
            print("Makine çalışıyor, lütfen bekleyin...")
            time.sleep(0.5)
            if self.devir == 20:
                self.devir = 0
                self.yeniDergi()

    def yeniDergi(self):
        print("Yeni dergi çıktı, hayırlı olsun!")
        a = input("Derginin ismi ne olsun: ")
        self.dergiler.append(a)
        time.sleep(2)

    def şarjDoldur(self):
        if self.şarj < 100:
            self.şarj += 10
            if self.şarj > 100:  # Şarjın 100'ü geçmesini engelle
                self.şarj = 100
            print("Şarj dolduruldu. Mevcut şarj ->", self.şarj)
            time.sleep(2)

    def mürekkepDoldur(self):
        if self.mürekkep < 100:
            self.mürekkep += 10
            if self.mürekkep > 100:  # Mürekkebin 100'ü geçmesini engelle
                self.mürekkep = 100
            print("Mürekkep dolduruldu. Mevcut mürekkep ->", self.mürekkep)

    def mevcutDurum(self):
        print("MAKİNENİN MEVCUT DURUMU:")
        print("Kalan mürekkep:", self.mürekkep)
        print("Kalan şarj:", self.şarj)
        print("Toplam çıkarılan dergi sayısı:", len(self.dergiler))
        if len(self.dergiler) > 0:
            print("Çıkarılan dergiler:")
            for i in self.dergiler:
                print(i)
        print("Yeni çıkacak derginin %", self.devir * 5, "kısmı tamamlandı")
        time.sleep(4)

Makine1 = Makine()

print("Matbaamıza hoşgeldiniz!")
while True:
    print("-" * 15)
    print("Makineyi çalıştırmak için -> 1\n"
          "Mevcut durumu öğrenmek için -> 2\n"
          "Şarjı doldurmak için -> 3\n"
          "Mürekkebi doldurmak için -> 4")

    komut = input()

    if komut == "1":
        Makine1.çalış()

    elif komut == "2":
        Makine1.mevcutDurum()

    elif komut == "3":
        Makine1.şarjDoldur()

    elif komut == "4":
        Makine1.mürekkepDoldur()

    else:
        print("Geçersiz komut. Lütfen tekrar deneyin.")
