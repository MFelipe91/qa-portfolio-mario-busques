# 👨‍💻 QA Portfolio — Mario Felipe Busqués Araya

> **Ingeniero en Informática | QA Engineer | Ciberseguridad**  
> Google Cybersecurity Professional Certificate · ISTQB Foundation (en preparación)  
> 📍 Santiago, Chile · 📧 mariofelipebusques@gmail.com · 🔗 [LinkedIn](https://linkedin.com/in/mariofelipebusques)

---

## 🎯 Sobre este portafolio

Soy Ingeniero Informático con más de 6 años de experiencia en TI, actualmente especializándome en **QA Engineering** con foco en **API Testing** y **Security Testing**.

Mi background en ciberseguridad me permite pensar el testing desde una perspectiva diferente: no solo verifico que el software *funciona*, sino que verifica que *no puede ser comprometido*.

Este portafolio documenta mi práctica real con herramientas QA modernas.

---

## 🛠 Stack técnico

| Categoría | Herramientas |
|---|---|
| **API Testing** | Postman, Newman |
| **Automatización** | Selenium + Python, Pytest |
| **Gestión de bugs** | Jira (Kanban/Scrum) |
| **Seguridad** | OWASP Top 10, Wireshark, Nmap |
| **CI/CD** | Jenkins, GitHub Actions |
| **Lenguajes** | Python, JavaScript, SQL, Bash |
| **Certificaciones** | Google Cybersecurity Professional (2025) |

---

## 📁 Contenido del portafolio

### 🔌 [/postman](./postman/)
Colecciones de Postman con tests automatizados para APIs REST.
- Flujo completo de autenticación (login → token → request autenticado)
- Tests funcionales, de rendimiento y de seguridad
- Scripts con assertions en JavaScript

### 📋 [/casos-de-prueba](./casos-de-prueba/)
Casos de prueba documentados con formato estándar ISTQB.
- Login y autenticación
- Transferencias bancarias (escenario BCI)
- Testing de seguridad: MFA, bloqueo por intentos, SQL injection

### 🐛 [/bug-reports](./bug-reports/)
Bug reports profesionales con formato Jira estándar.
- BUG-001: Falla de rendimiento — API responde en 44s (SLA: 5s)
- BUG-002: Sin bloqueo tras 5 intentos fallidos de login

---

## 🧪 Ejemplo de test real en Postman

```javascript
// TC-001: Verificar respuesta exitosa
pm.test("Status 200 OK", function () {
    pm.response.to.have.status(200);
});

// TC-002: Tiempo de respuesta dentro del SLA
pm.test("Respuesta bajo SLA de 5000ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(5000);
});

// TC-003: Estructura del body correcta
pm.test("Body tiene campos obligatorios", function () {
    var json = pm.response.json();
    pm.expect(json).to.have.property("data");
    pm.expect(json.data).to.have.property("balance");
});
```

---

## 📈 Lo que estoy aprendiendo ahora

- ✅ Postman — API Testing y automatización con Newman
- ✅ Selenium + Python — Automatización de pruebas web
- 🔄 ISTQB Foundation Level — Certificación internacional QA
- 🔄 Parasoft SOAtest/SOAvirt — Testing enterprise de APIs
- 🔄 Jenkins CI/CD — Integración continua con pipelines

---

## 🏢 Experiencia relevante

**TECKWARE** — Fundador & Técnico TI (2019 – Presente)  
Diagnóstico de sistemas, redes, automatización con Python/Bash, desarrollo web.

**Aulas Conectadas – UFRO (MINEDUC)** — Analista Técnico de Redes (2022–2024)  
Infraestructura de red en establecimientos educativos, documentación técnica.

**Clínica Elqui** — Práctica Profesional (2017)  
Aplicación web PHP+Bootstrap para trazabilidad de biopsias. Nota: 7.0

---

*Portafolio en construcción activa — actualizaciones semanales*
