# spotify-bot

import time
import random
from selenium  import webdriver
from selenium.webdriver import Keys
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By

rastgele_gun = random.randint(1,31)

rastgele_yıl = random.randint(1985,2004)
ay = ["Ocak","Şubat","Mart","Nisan","Mayıs","Haziran","Temmuz","Ağustos","Eylül","Ekim","Kasım","Aralık"]

rastgele_ay = random.choice(ay)
                      
cinsyet = ["//span[text()='Erkek']","//span[text()='Kadın']"]

cinsiyeti = random.choice(cinsyet)

ad = ["Halaf","Casim","Hüseyin","Cabbar"]
soy_ad = ["Casimi","Muhammed caviş","Hachussein"]
    
adı = random.choice(ad)
soy_adı = random.choice(soy_ad)

service = Service("./chormedriver.exe")
driver = webdriver.Chrome(service=service)
driver.get("https://www.spotify.com/tr/signup")

eposta = driver.find_element(By.ID, "email")
eposta.send_keys("schoolcavus@gmail.com")
eposta.send_keys(Keys.ENTER)


eposta_onayla = driver.find_element(By.ID, "confirm")
eposta_onayla.send_keys("schoolcavus@gmail.com")
eposta_onayla.send_keys(Keys.ENTER)

sifre = driver.find_element(By.ID, "password")
sifre.send_keys("Muhammedcavus0")
sifre.send_keys(Keys.ENTER)

kulanıcı_adı = driver.find_element(By.ID, "displayname")
kulanıcı_adı.send_keys(adı," ",soy_adı)
kulanıcı_adı.send_keys(Keys.ENTER)

dogum_gun = driver.find_element(By.ID, "day")
dogum_gun.send_keys(rastgele_gun)
dogum_gun.send_keys(Keys.ENTER)

dogum_ay = driver.find_element(By.ID, "month")
dogum_ay.send_keys(rastgele_ay)
dogum_ay.send_keys(Keys.ENTER)

dogum_yıl = driver.find_element(By.ID, "year")
dogum_yıl.send_keys(rastgele_yıl)
dogum_yıl.send_keys(Keys.ENTER)

driver.find_element(By.XPATH,cinsiyeti).click()
