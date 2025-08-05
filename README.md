# 🔁 Multi-Container Nginx Proxy + Static Website with Docker Compose

Bu proje, iki ayrı Docker container'ı kullanarak bir statik web sitesini Nginx üzerinden yayınlayan basit bir reverse proxy mimarisini göstermektedir.

## 📁 Proje Yapısı

```
.
├── docker-compose.yml
├── app/
│   ├── Dockerfile         # Statik web sayfasını barındıran container
│   └── index.html         # Yayınlanan HTML dosyası
└── nginx/
    ├── Dockerfile         # Reverse proxy için Nginx container
    └── nginx.conf         # Nginx yönlendirme konfigürasyonu
```

## 🧩 Kullanılan Teknolojiler

- Docker
- Docker Compose
- Nginx (Alpine)
- HTML, CSS, JS (statik içerik)

## 🚀 Kurulum ve Çalıştırma

Aşağıdaki adımları izleyerek projeyi çalıştırabilirsiniz:

```bash
# 1. Proje dizinine girin
cd Alistirma1.6

# 2. Docker image'larını build edin ve container'ları başlatın
docker-compose up --build
```

Ardından tarayıcınızdan `http://localhost` adresine giderek statik sayfayı görebilirsiniz.

## 🧪 Test

İstekleri test etmek için:

```bash
# Proxy üzerinden test
curl http://localhost

# Statik web container'ına doğrudan erişim (isteğe bağlı)
curl http://localhost:8080
```

## ⚙️ nginx.conf Özeti

`nginx/nginx.conf` dosyasında gelen tüm istekler `app` isimli container'a yönlendirilir:

```nginx
location / {
    proxy_pass http://app:80;
}
```

## 🧼 Temizlik

Proje çalışmasını durdurmak ve container'ları silmek için:

```bash
docker-compose down
```

## 📦 Geliştirme Notları

- `app` container'ı, `index.html` içeriğini `nginx:alpine` imajı kullanarak yayınlar.
- `nginx` container'ı, `proxy_pass` direktifi ile gelen istekleri `app` container'ına yönlendirir.

## 👩‍💻 Katkı

Bu proje öğrenme ve deneyim kazanma amaçlıdır. Katkıda bulunmak isterseniz fork'layarak geliştirme yapabilirsiniz.

## 📝 Lisans

MIT License.