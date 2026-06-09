var CACHE='cbn-v1';
var ASSETS=[
  '/',
  '/index.html',
  'https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@2.44.0/tabler-icons.min.css',
  'https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@2.44.0/fonts/tabler-icons.woff2'
];

self.addEventListener('install',function(e){
  e.waitUntil(
    caches.open(CACHE).then(function(cache){
      return cache.addAll(ASSETS);
    })
  );
  self.skipWaiting();
});

self.addEventListener('activate',function(e){
  e.waitUntil(
    caches.keys().then(function(keys){
      return Promise.all(keys.filter(function(k){return k!==CACHE;}).map(function(k){return caches.delete(k);}));
    })
  );
  self.clients.claim();
});

self.addEventListener('fetch',function(e){
  e.respondWith(
    caches.match(e.request).then(function(cached){
      return cached||fetch(e.request).then(function(response){
        if(response&&response.status===200&&response.type!=='opaque'){
          var clone=response.clone();
          caches.open(CACHE).then(function(cache){cache.put(e.request,clone);});
        }
        return response;
      }).catch(function(){return cached;});
    })
  );
});
