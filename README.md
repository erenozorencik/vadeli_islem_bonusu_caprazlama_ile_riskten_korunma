# 💱 Vadeli İşlem Bonusu Çaprazlama

Bu çalışmada, kripto para borsalarının yeni kayıt olan kullanıcılara sunduğu vadeli işlem bonuslarını hedge işlemleriyle nasıl riske girmeden en etkili şekilde çekilebilir kâra dönüştürebileceğimizi analiz ediyoruz.

---

## 📋 Kurallar

- Her KYC doğrulayan hesap için **50 USDT** vadeli işlemler bonusu verilir.
- Bonus çekilemez; yalnızca işlemlerden elde edilen kâr çekilebilir.
- Bakiye çekildiğinde bonus silinir.

---

## 🔄 Strateji

- Hesaplara tanımlanan vadeli işlem bonusunu hedge ederek riske girmeden bakiyenin bir kısmı çekilebilir.
- Bakiyeyi eşit miktarlara ayırıp yarısı ile **LONG**, yarısı ile **SHORT** işlem açılır.
- Pozisyonu açarken zincirleme tetiklenmesi için birinin likide olduğu fiyata diğerinin kar alma noktası ayarlanır.
- Ayrıca pozisyon açarken olabilecek en yüksek kaldıraç seçilmelidir.

```text
                       50 USDT ==> 25 USDT LONG | 25 USDT SHORT
```
Pozisyonlardan biri likide olurken diğeri kar alma noktasına gelir ve pozisyonlar kapanır.
```text
                                 WİN             LOSE
                           25x2 USDT LONG | 25x0 USDT SHORT  
                               +25 USDT   |    -25 USDT
                                     25 USDT PNL
```
Gerçek piyasalarda vadeli bonuslarda aynı parite üzerinde hedge işlem açmanıza engel koyulacaktır ancak bunları aşmanın basit yolları var.

## 🤝 Çoklu Hesap ile Çaprazlama

Her hesabı kendi içinde çaprazlamak yerine hesapları birbirleri ile çaprazlarsanız, hesap sayısı (n) arttıkça hesap başına çekilebilir bakiye artacaktır.

Örneğin 4 hesap:

```text
                        WİN         WİN        LOSS        LOSS
                       ACC 1   |   ACC 2   |   ACC 3   |   ACC 4  
                      50 USDT     50 USDT     50 USDT     50 USDT
                        LONG   |    LONG   |   SHORT   |   SHORT
                      100 USDT    100 USDT     0 USDT      0 USDT
                
                                     WİN        LOSS
                                    ACC 1  |   ACC 2 
                                  100 USDT    100 USDT     
                                    LONG   |   SHORT 
                                  200 USDT    0 USDT
                
                          ACC 1 BALANCE=200 USDT BONUS=50 USDT
                               BALANCE - BONUS = 150 USDT 
                PNL PER ACC = TOTAL PNL / ACC COUNT(n) = 150/4 = 37.5 USDT
```
Örnekte görüldüğü gibi 4 hesabı kendi aralarında çaprazladığımızda hesap başına düşen çekilebilir miktar %50 artış gösterdi.

Şimdi kaç hesap ile çaprazlarsak , hesap başına düşen çekilebilir bakiye kaç olur ona bakalım :

---

## 📊 Hesap Başına Çekilebilir Bakiye Grafiği

![grafik](https://github.com/user-attachments/assets/4a00247a-91d8-4977-b76b-e6cb41709c7e)

---
