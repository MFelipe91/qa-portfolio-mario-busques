# BUG-001 — Falla de Rendimiento: API supera SLA definido

| Campo | Detalle |
|---|---|
| **ID** | BUG-001 |
| **Fecha** | 2025-07-08 |
| **Reporter** | Mario Felipe Busqués Araya |
| **Severidad** | Alto |
| **Prioridad** | Alta |
| **Estado** | Abierto |
| **Módulo** | API REST — Endpoint POST |

---

## Título
API POST `/post` responde en **44.310ms** — supera el SLA definido de 5.000ms

---

## Entorno
- **URL:** `https://httpbin.org/post`
- **Método:** POST
- **Herramienta:** Postman v12
- **OS:** Windows 11
- **Fecha/hora:** 2025-07-08 02:55 hrs

---

## Precondiciones
- Conexión a internet activa
- Request POST con body JSON válido

---

## Pasos para reproducir

1. Abrir Postman
2. Crear request POST a `https://httpbin.org/post`
3. Body → raw → JSON:
```json
{
    "email": "mario@teckware.cl",
    "password": "test123"
}
```
4. Enviar request
5. Observar tiempo de respuesta en la barra inferior de Postman

---

## Resultado actual
```
Tiempo de respuesta: 44.310ms (44 segundos)
Status: 200 OK
```

El test automatizado detectó la falla:
```
failed | Respuesta en menos de 5000ms
AssertionError: expected 44310 to be below 5000
```

---

## Resultado esperado
```
Tiempo de respuesta: < 5.000ms según SLA definido
Status: 200 OK
```

---

## Impacto de negocio
En un entorno bancario como BCI, una API que tarda 44 segundos en responder:
- Genera **timeout** en la interfaz del cliente
- Produce **experiencia de usuario inaceptable**
- Puede causar **reintentos automáticos** que saturan el servidor
- Incumple **SLA contractual** con el cliente

---

## Evidencia
- Captura de Postman mostrando `44310ms` y test fallido
- Script de test con assertion documentada

---

## Causa probable
- Servidor público con alta carga de tráfico
- Sin caché configurado
- Sin balanceo de carga

---

## Recomendación
1. Revisar métricas de rendimiento del servidor
2. Implementar timeout en el cliente (no esperar más de 10s)
3. Configurar monitor de Postman para alertas automáticas cuando supere 2000ms
