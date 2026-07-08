# Casos de Prueba — Módulo Login BCI

| Campo | Detalle |
|---|---|
| **Módulo** | Autenticación / Login |
| **Sistema** | App BCI (escenario de práctica) |
| **Autor** | Mario Felipe Busqués Araya |
| **Fecha** | 2025-07-08 |
| **Versión** | 1.0 |

---

## TC-001 — Login exitoso con credenciales válidas

| Campo | Detalle |
|---|---|
| **Tipo** | Happy Path — Funcional |
| **Prioridad** | Alta |
| **Precondición** | Usuario registrado en el sistema con RUT 12.345.678-9 |

**Pasos:**
1. Ingresar a bci.cl y hacer clic en "Ingresar"
2. Ingresar RUT: `12345678-9`
3. Ingresar contraseña correcta
4. Hacer clic en "Ingresar"

**Resultado esperado:** Sistema redirige al dashboard mostrando saldo y últimas transacciones.

**Resultado actual:** _(completar al ejecutar)_

**Estado:** ⬜ Pendiente

---

## TC-002 — Login con contraseña incorrecta muestra error

| Campo | Detalle |
|---|---|
| **Tipo** | Negativo — Funcional |
| **Prioridad** | Alta |
| **Precondición** | Usuario registrado en el sistema |

**Pasos:**
1. Ingresar RUT válido: `12345678-9`
2. Ingresar contraseña incorrecta: `Password123`
3. Hacer clic en "Ingresar"

**Resultado esperado:** Mensaje de error visible: "RUT o contraseña incorrectos". Sin acceso al sistema.

**Resultado actual:** _(completar al ejecutar)_

**Estado:** ⬜ Pendiente

---

## TC-003 — Cuenta se bloquea tras 5 intentos fallidos

| Campo | Detalle |
|---|---|
| **Tipo** | Seguridad |
| **Prioridad** | Alta |
| **Severidad** | Crítico |
| **Precondición** | Usuario registrado en el sistema |

**Pasos:**
1. Ingresar credenciales incorrectas 5 veces consecutivas
2. Intentar ingresar una 6ta vez

**Resultado esperado:** Cuenta bloqueada temporalmente. Mensaje: "Tu cuenta ha sido bloqueada. Intenta en 15 minutos."

**Resultado actual:** _(completar al ejecutar)_

**Estado:** ⬜ Pendiente

**Nota de seguridad:** Sin límite de intentos → vulnerabilidad de fuerza bruta. Incumple normativas CMF.

---

## TC-004 — MFA funciona correctamente

| Campo | Detalle |
|---|---|
| **Tipo** | Seguridad — Funcional |
| **Prioridad** | Alta |
| **Severidad** | Crítico |

**Pasos:**
1. Ingresar credenciales correctas
2. Sistema solicita código MFA (SMS/email)
3. Ingresar código correcto → debe acceder
4. Ingresar código incorrecto → debe rechazar
5. Dejar expirar el código → debe solicitar uno nuevo

**Resultado esperado:** Solo el código correcto y vigente permite el acceso.

**Estado:** ⬜ Pendiente

---

## TC-005 — Campo RUT valida formato

| Campo | Detalle |
|---|---|
| **Tipo** | Edge Case — Funcional |
| **Prioridad** | Media |

**Pasos:**
1. Ingresar RUT con puntos: `12.345.678-9` → debe aceptar
2. Ingresar RUT sin guion: `123456789` → debe aceptar o normalizar
3. Ingresar texto: `abc-xyz` → debe mostrar error de formato
4. Ingresar caracteres especiales: `'; DROP TABLE--` → debe sanitizar (SQL Injection)

**Resultado esperado:** Solo formatos válidos de RUT son aceptados. Inputs maliciosos son sanitizados.

**Estado:** ⬜ Pendiente

**Nota de seguridad:** El caso de SQL Injection es crítico en entornos bancarios.
