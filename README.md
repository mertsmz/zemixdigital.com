# Zemix Digital Website

Bu website, Zemix Digital ve Three Realms uygulaması için oluşturulmuştur.

## Sayfalar

- **Ana Sayfa** (`index.html`) - Zemix Digital ana sayfası
- **Three Realms** (`three-realms.html`) - Uygulama sayfası
- **Privacy Policy** (`privacy-policy.html`) - Gizlilik politikası
- **Data Deletion Request** (`data-deletion-request.html`) - Veri silme talebi
- **Terms of Service** (`terms-of-service.html`) - Kullanım şartları

## AdMob Doğrulama

AdMob doğrulaması için `admob.txt` dosyası oluşturulmuştur. AdMob hesabınızdan aldığınız doğrulama kodunu bu dosyaya ekleyin.

## Deploy Talimatları

### 1. Domain Satın Alma

**Türkiye'de Domain Satın Alma:**
- **Turhost** (turhost.com) - Türkçe destek, uygun fiyatlar
- **Natro** (natro.com) - Popüler Türk hosting firması
- **Namecheap** (namecheap.com) - Uluslararası, güvenilir
- **GoDaddy** (godaddy.com) - Dünya çapında popüler

**Adımlar:**
1. Yukarıdaki sitelerden birine gidin
2. İstediğiniz domain adını arayın (örn: zemixdigital.com)
3. Sepete ekleyip ödeme yapın
4. Domain yönetim paneline giriş yapın

### 2. Hosting Seçimi

**Önerilen Hosting Seçenekleri:**

**A) Ücretsiz Seçenekler:**
- **GitHub Pages** (pages.github.com) - Ücretsiz, kolay
- **Netlify** (netlify.com) - Ücretsiz, otomatik deploy
- **Vercel** (vercel.com) - Ücretsiz, hızlı

**B) Ücretli Seçenekler (Türkiye):**
- **Turhost** - Türkçe destek, ~50-100 TL/ay
- **Natro** - Türkçe destek, ~50-100 TL/ay
- **DigitalOcean** - $5/ay, güçlü

### 3. GitHub Pages ile Deploy (Ücretsiz - Önerilen)

**Adımlar:**

1. **GitHub'da Repository Oluştur:**
   ```bash
   # Terminal'de proje klasöründe:
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **GitHub'da yeni repository oluştur:**
   - github.com'a gidin
   - "New repository" tıklayın
   - Repository adı verin (örn: zemixdigital-website)
   - "Create repository" tıklayın

3. **Kodu GitHub'a yükleyin:**
   ```bash
   git remote add origin https://github.com/KULLANICI_ADI/zemixdigital-website.git
   git branch -M main
   git push -u origin main
   ```

4. **GitHub Pages Aktifleştir:**
   - Repository'de "Settings" > "Pages" bölümüne gidin
   - Source: "main" branch seçin
   - Save tıklayın
   - 5 dakika içinde site yayında: `https://KULLANICI_ADI.github.io/zemixdigital-website`

5. **Domain Bağlama:**
   - GitHub Pages Settings'te "Custom domain" alanına domain adınızı yazın (örn: zemixdigital.com)
   - Domain sağlayıcınızda DNS ayarları:
     - **A Record:** `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
     - **CNAME Record:** `www` -> `KULLANICI_ADI.github.io`

### 4. Netlify ile Deploy (Ücretsiz - Alternatif)

**Adımlar:**

1. **Netlify'e gidin:** netlify.com
2. **Sign up** yapın (GitHub ile giriş yapabilirsiniz)
3. **"Add new site" > "Deploy manually"** seçin
4. **Tüm dosyaları sürükle-bırak** ile yükleyin
5. **Site otomatik yayınlanır:** `https://RANDOM-NAME.netlify.app`
6. **Domain bağlama:**
   - Site ayarları > Domain settings
   - Custom domain ekleyin
   - DNS ayarlarını takip edin

### 5. VPS/Server ile Deploy (Linux)

**Adımlar:**

1. **SSH ile sunucuya bağlanın:**
   ```bash
   ssh kullanici@sunucu-ip
   ```

2. **Nginx kurulumu:**
   ```bash
   sudo apt update
   sudo apt install nginx -y
   ```

3. **Dosyaları yükleyin:**
   ```bash
   # SCP ile dosya transferi (yerel bilgisayardan):
   scp -r * kullanici@sunucu-ip:/var/www/html/
   
   # Veya Git ile:
   cd /var/www/html
   git clone https://github.com/KULLANICI_ADI/zemixdigital-website.git
   ```

4. **Nginx yapılandırması:**
   ```bash
   sudo nano /etc/nginx/sites-available/default
   ```
   
   ```nginx
   server {
       listen 80;
       server_name zemixdigital.com www.zemixdigital.com;
       root /var/www/html;
       index index.html;
       
       location / {
           try_files $uri $uri/ =404;
       }
   }
   ```
   
   ```bash
   sudo nginx -t
   sudo systemctl reload nginx
   ```

5. **SSL Sertifikası (Let's Encrypt):**
   ```bash
   sudo apt install certbot python3-certbot-nginx -y
   sudo certbot --nginx -d zemixdigital.com -d www.zemixdigital.com
   ```

### 6. AdMob Doğrulama

1. **AdMob Console'a giriş yapın**
2. **App settings > App verification** bölümüne gidin
3. **Website verification** seçeneğini seçin
4. **Verilen kodu** `admob.txt` dosyasına ekleyin
5. **Dosyayı website root'una yükleyin** (örn: `https://zemixdigital.com/admob.txt`)
6. **AdMob'da doğrulamayı tamamlayın**

### 7. İçerik Güncelleme

Privacy Policy, Terms of Service ve diğer sayfalardaki placeholder metinleri gerçek içeriklerle değiştirin:

- `privacy-policy.html` - Privacy Policy metnini ekleyin
- `data-deletion-request.html` - Data Deletion Request metnini ekleyin
- `terms-of-service.html` - Terms of Service metnini ekleyin
- `three-realms.html` - Uygulama açıklamasını ekleyin

## DNS Ayarları (Domain Sağlayıcısında)

Domain sağlayıcınızın DNS yönetim panelinde:

**GitHub Pages için:**
- Type: A, Name: @, Value: 185.199.108.153
- Type: A, Name: @, Value: 185.199.109.153
- Type: A, Name: @, Value: 185.199.110.153
- Type: A, Name: @, Value: 185.199.111.153
- Type: CNAME, Name: www, Value: KULLANICI_ADI.github.io

**Netlify için:**
- Netlify size özel DNS bilgileri verecektir

**VPS için:**
- Type: A, Name: @, Value: SUNUCU_IP_ADRESI
- Type: A, Name: www, Value: SUNUCU_IP_ADRESI

## Notlar

- DNS değişiklikleri 24-48 saat içinde yayınlanabilir
- HTTPS için SSL sertifikası kullanın (Let's Encrypt ücretsiz)
- `admob.txt` dosyası website root'unda erişilebilir olmalı
