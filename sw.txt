const CACHE_NAME = 'gtfs-demo-cache-v1';
const ASSETS = [
  '.', 'index.html', 'manifest.json', 'routes.geojson', 'stops.geojson',
  'https://unpkg.com/leaflet/dist/leaflet.css',
  'https://unpkg.com/leaflet/dist/leaflet.js'
];
self.addEventListener('install', e =>
  e.waitUntil(caches.open(CACHE_NAME).then(cache=>cache.addAll(ASSETS)))
);
self.addEventListener('fetch', e =>
  e.respondWith(caches.match(e.request).then(r=>r||fetch(e.request)))
);
