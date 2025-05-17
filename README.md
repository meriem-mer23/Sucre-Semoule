<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Sucre & Semoule</title>
  <link rel="manifest" href="manifest.json" />
  <meta name="theme-color" content="#f0c987" />
  <style>
    body { font-family: Arial, sans-serif; direction: rtl; background: #fff8f0; color: #4b2e05; margin: 0; padding: 0; }
    header { background: #f0c987; padding: 20px; text-align: center; font-size: 2.5em; font-weight: bold; }
    nav { background: #d19c3d; padding: 10px; text-align: center; }
    nav a { color: white; text-decoration: none; margin: 0 15px; font-weight: bold; }
    main { padding: 20px; max-width: 800px; margin: auto; }
    .sweets { display: flex; flex-wrap: wrap; gap: 20px; justify-content: center; }
    .sweet { background: white; border-radius: 8px; box-shadow: 0 0 8px #d9b382; width: 220px; padding: 15px; text-align: center; }
    .sweet img { max-width: 100%; border-radius: 8px; }
    .order-btn { margin-top: 10px; background: #25d366; color: white; padding: 10px 15px; border: none; border-radius: 5px; cursor: pointer; font-size: 1em; text-decoration: none; display: inline-block; }
    footer { background: #f0c987; text-align: center; padding: 15px; margin-top: 30px; font-size: 0.9em; }
  </style>
</head>
<body>
  <header>Sucre & Semoule</header>
  <nav>
    <a href="#home">الرئيسية</a>
    <a href="#sweets">الحلويات</a>
    <a href="#contact">اتصل بنا</a>
  </nav>

  <main>
    <section id="home">
      <h2>مرحبا بكم في Sucre & Semoule</h2>
      <p>الحلويات الطازجة واللذيذة من القلب إلى طبقك!</p>
      <img src="https://via.placeholder.com/800x400?text=Sucre+%26+Semoule" alt="حلويات Sucre & Semoule" style="width:100%; border-radius:10px;" />
    </section>

    <section id="sweets">
      <h2>الحلويات</h2>
      <div class="sweets">
        <div class="sweet">
          <img src="https://via.placeholder.com/220x150?text=كعكة+الفانيليا" alt="كعكة الفانيليا" />
          <h3>كعكة الفانيليا</h3>
          <p>كعكة ناعمة بطعم الفانيليا الأصلي.</p>
          <a href="https://wa.me/212676428995" target="_blank" class="order-btn">اطلب الآن عبر واتساب</a>
        </div>
        <div class="sweet">
          <img src="https://via.placeholder.com/220x150?text=بسكويت+اللوز" alt="بسكويت اللوز" />
          <h3>بسكويت اللوز</h3>
          <p>بسكويت مميز بنكهة اللوز المميزة.</p>
          <a href="https://wa.me/212676428995" target="_blank" class="order-btn">اطلب الآن عبر واتساب</a>
        </div>
      </div>
    </section>

    <section id="contact" style="margin-top: 40px;">
      <h2>اتصل بنا</h2>
      <p>يمكنك الطلب أو الاستفسار عبر الواتساب على الرقم التالي:</p>
      <p><strong><a href="https://wa.me/212676428995" target="_blank" style="color:#25d366;">0676428995</a></strong></p>
    </section>
  </main>

  <footer>
    &copy; 2025 Sucre & Semoule | جميع الحقوق محفوظة
  </footer>

  <script>
    if ('serviceWorker' in navigator) {
      navigator.serviceWorker.register('service-worker.js')
        .then(() => console.log('Service Worker registered.'))
        .catch((error) => console.log('Service Worker registration failed:', error));
    }
  </script>
</body>
</html>
{
  "name": "Sucre & Semoule",
  "short_name": "SucreSemoule",
  "start_url": "./index.html",
  "display": "standalone",
  "background_color": "#fff8f0",
  "theme_color": "#f0c987",
  "icons": [
    {
      "src": "icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
const CACHE_NAME = 'sucre-semoule-cache-v1';
const urlsToCache = [
  './',
  './index.html',
  './manifest.json',
  // ممكن تضيف هنا روابط الصور والملفات اللي تحتاج تخزينها
];

self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => {
      return cache.addAll(urlsToCache);
    })
  );
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
