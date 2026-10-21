const NOMBRE_BD = 'fondo-video';
const TABLA = 'datos';
const CLAVE = 'video';

const video = document.getElementById('video');
const vacio = document.getElementById('vacio');
const controles = document.getElementById('controles');
const estado = document.getElementById('estado');
const archivo = document.getElementById('archivo');

let urlActual = null;

function abrirBD() {
  return new Promise((ok, fallo) => {
    const pedido = indexedDB.open(NOMBRE_BD, 1);
    pedido.onupgradeneeded = () => pedido.result.createObjectStore(TABLA);
    pedido.onsuccess = () => ok(pedido.result);
    pedido.onerror = () => fallo(pedido.error);
  });
}

async function leer() {
  const bd = await abrirBD();
  return new Promise((ok, fallo) => {
    const q = bd.transaction(TABLA).objectStore(TABLA).get(CLAVE);
    q.onsuccess = () => ok(q.result || null);
    q.onerror = () => fallo(q.error);
  });
}

async function guardar(blob) {
  const bd = await abrirBD();
  return new Promise((ok, fallo) => {
    const tx = bd.transaction(TABLA, 'readwrite');
    tx.objectStore(TABLA).put(blob, CLAVE);
    tx.oncomplete = () => ok();
    tx.onerror = () => fallo(tx.error);
  });
}

async function borrar() {
  const bd = await abrirBD();
  return new Promise((ok, fallo) => {
    const tx = bd.transaction(TABLA, 'readwrite');
    tx.objectStore(TABLA).delete(CLAVE);
    tx.oncomplete = () => ok();
    tx.onerror = () => fallo(tx.error);
  });
}

function mostrar(blob) {
  if (urlActual) URL.revokeObjectURL(urlActual);
  urlActual = null;
  if (!blob) {
    video.removeAttribute('src');
    video.load();
    vacio.hidden = false;
    controles.hidden = true;
    return;
  }
  urlActual = URL.createObjectURL(blob);
  video.src = urlActual;
  vacio.hidden = true;
  controles.hidden = false;
  video.play().catch(() => {});
}

document.getElementById('elegir').addEventListener('click', () => archivo.click());
document.getElementById('cambiar').addEventListener('click', () => archivo.click());

document.getElementById('quitar').addEventListener('click', async () => {
  try {
    await borrar();
    mostrar(null);
  } catch (e) {
    estado.textContent = 'No se pudo quitar el video. Intenta de nuevo.';
  }
});

archivo.addEventListener('change', async () => {
  const elegido = archivo.files[0];
  archivo.value = '';
  if (!elegido) return;
  try {
    await guardar(elegido);
    mostrar(elegido);
  } catch (e) {
    vacio.hidden = false;
    estado.textContent = 'No se pudo guardar el video. Prueba con uno más ligero.';
  }
});

document.addEventListener('visibilitychange', () => {
  if (document.hidden) video.pause();
  else if (video.src) video.play().catch(() => {});
});

leer().then(mostrar).catch(() => mostrar(null));
