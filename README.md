// Importar las herramientas necesarias desde worker_threads
const { parentPort, workerData } = require('worker_threads');
 
// Extraer los datos enviados desde el hilo principal
const { vectorA, vectorB } = workerData;
 
// Verificar que los vectores tengan la misma longitud
if (vectorA.length !== vectorB.length) {
    throw new Error('Los vectores deben tener la misma longitud.');
}
 
// Realizar la suma elemento por elemento
const result = vectorA.map((value, index) => value + vectorB[index]);
 
// Enviar el resultado al hilo principal
parentPort.postMessage(result);# child.js
