1. **Tiempo Implementado y Recursos Utilizados**
**Tiempo Implementado:**
- **Revisión y Ajustes Previos:** 2 horas.

	- Adaptación del diagrama de arquitectura.

	- Integración de permisos jerárquicos en el modelo de datos.

- **Actualización de Numerales Afectados:** 3 horas.

	- Numeral 2.6. Tests.

	- Numeral 3. Modelo de Datos.

- **Análisis y Verificación Final:** 1 hora.

**Recursos Utilizados:**

1. **Tecnologías Involucradas:**

	- Firebase (Realtime Database, Authentication, Storage).

	- Node.js con Express.

	- Herramientas de diseño como Mermaid para diagramas técnicos.

2. **Metodologías:**

	- Patrón MVC para backend.

	- Validación cruzada de pruebas unitarias y funcionales.

3. **Documentación Referenciada:**

- Guías oficiales de Firebase sobre autenticación y reglas de seguridad.

- Lineamientos estructurales de nuestro proyecto.

---

2. **Resultado de las Comparaciones y Estrategias Utilizadas**
Se compararon tres enfoques principales para gestionar permisos y jerarquías:

|            Enfoque               |                               Ventajas                            |                                        Desventajas	                            |      **Resultado**      |
|----------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------------------------|-------------------------|
|Jerarquías en el Backend          |Escalabilidad y fácil integración.                                 |Mayor complejidad en el backend inicial.                                        |Seleccionado.            |
|Reglas Dinámicas en Firebase      |Gestión automática de accesos según roles, con menos código manual.|Más dependencias de reglas personalizadas en Firebase (limitado para consultas).|Seleccionado (parcial).  |
|Sistema Híbrido (Frontend-Backend)|Combina validaciones en frontend y backend para mayor flexibilidad.|Mayor complejidad en la sincronización entre frontend y backend.                |Rechazado en esta etapa. |
|----------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------------------------|-------------------------|

**Estrategía Utilizada:** Decidimos emplear un enfoque Jerárquico en el Backend combinado con Reglas en Firebase, debido a su flexibilidad y escalabilidad. Esto permitió una gestión granular de permisos sin comprometer la seguridad.


# Curso Práctico: Gestión de Permisos y Jerarquías con Firebase y Node.js

### **Módulo 1: Comprender la Arquitectura**
- **Objetivo**: Entender cómo interactúan los usuarios, dispositivos y eventos en nuestro sistema.
- **Ejercicio**: Dibuja un diagrama de flujo para reflejar las interacciones entre:
  1. Usuarios principales y auxiliares.
  2. Dispositivos asignados y generadores de eventos.
  3. Base de datos y almacenamiento en Firebase.

### **Módulo 2: Implementación de Firebase Authentication**
- **Pasos**:
  1. Configura Firebase Authentication en tu proyecto.
     ```bash
     npm install firebase-admin
     ```
  2. Crea reglas de seguridad para controlar accesos jerárquicos.
     ```json
     {
       "rules": {
         "usuarios": {
           "$uid": {
             ".read": "auth != null",
             ".write": "auth != null && auth.uid == $uid"
           }
         }
       }
     }
     ```
- **Uso en el Proyecto**:
  - Valida que los usuarios auxiliares accedan únicamente a dispositivos asignados por su usuario principal.

### **Módulo 3: Construcción del Backend con Jerarquías**
- **Concepto**:
  El backend actúa como intermediario para validar permisos antes de interactuar con Firebase.

- **Ejemplo de Endpoint**:
  ```javascript
  app.get("/dispositivos/:id", (req, res) => {
      const userId = req.user.uid; // Obtenemos el ID del usuario autenticado.
      const dispositivoId = req.params.id;

      // Validar que el usuario tiene acceso al dispositivo.
      db.ref(`/dispositivos/${dispositivoId}`)
        .once("value")
        .then((snapshot) => {
            const dispositivo = snapshot.val();
            if (dispositivo.usuarioId === userId || dispositivo.accesoPermisosAux) {
                res.status(200).json(dispositivo);
            } else {
                res.status(403).json({ error: "Acceso no autorizado" });
            }
        });
  });
  ```
- **Uso en el Proyecto:**

Este endpoint verifica dinámicamente los permisos en tiempo real.

---

**Módulo 4: Pruebas y Validaciones**
- **Prueba de Jerarquías:**

	1. Crea usuarios principales y auxiliares en Firebase.

	2. Define dispositivos y asigna permisos auxiliares.

	3. Simula peticiones al backend con permisos válidos e inválidos.

- **Uso en el Proyecto:**

	- Asegurar que las pruebas de seguridad y roles cubran los casos de uso más relevantes.