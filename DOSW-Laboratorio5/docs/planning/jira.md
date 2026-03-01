# 📄 Planeación del Sistema en Jira

## Desglose de trabajo: Épicas, Historias de Usuario y Tareas

La implementación de los requerimientos identificados de Bankify se desglosa de la siguiente manera:

### 1. Épica:

**DLC-1: Gestión de Cuentas Bancarias**

![Épica creada en Jira](../../images/Epica.png)

---

### 2. Historias de usuario:

#### DLC-2: Crear cuenta bancaria validada

![Historia de Usuario HU-01](../../images/cuenta.png)

---

#### DLC-3: Activar e inactivar cuenta bancaria

![Historia de Usuario HU-02](../../images/Activar.png)

---

#### DLC-4: Consultar saldo de cuenta bancaria

![Historia de Usuario HU-03](../../images/consultar.png)

---

#### DLC-5: Actualizar información de cuenta bancaria

![Historia de Usuario HU-04](../../images/actualizar.png)

---

### 3. Tareas:

#### Tareas de DLC-2:

**DLC-6: Implementar validación del número de cuenta**

![Tarea TR-01](../../images/validar.png)

---

**DLC-7: Implementar validación del banco asociado**

![Tarea TR-02](../../images/asociado.png)

---

**DLC-8: Crear endpoint REST para registro de cuenta**

![Tarea TR-03](../../images/crear.png)

---

#### Tareas de DLC-3:

**DLC-9: Implementar lógica de cambio de estado de cuenta**

![Tarea TR-04](DOSW-Laboratorio5/docs/images/implementar.png) 

---

**DLC-10: Controlar permisos por rol para activar/inactivar**

![Tarea TR-05](../../images/Controlar.png)

---

**DLC-11: Crear endpoint REST para cambio de estado de cuenta**

![Tarea TR-06](../../images/endpoint.png)

---

#### Tareas de DLC-4:

**DLC-12: Implementar servicio de consulta de saldo**

![Tarea TR-07](../../images/ConsultaSaldo.png)

---

**DLC-13: Controlar acceso a la consulta por propietario**

![Tarea TR-08](../../images/ConsultaPropietario.png)

---

**DLC-14: Crear endpoint REST para consulta de saldo**

![Tarea TR-09](../../images/ConsultarEnd.png)

---

#### Tareas de DLC-5:

**DLC-15: Definir campos actualizables de la cuenta**

![Tarea TR-10](../../images/ActuCuenta.png)

---

**DLC-16: Implementar servicio de actualización de cuenta**

![Tarea TR-11](../../images/ImplementarCue.png)

---

**DLC-17: Crear endpoint REST para actualización de cuenta**

![Tarea TR-12](../../images/endpointREST.png)

---

### 4. Cronograma:

![Cronograma en Jira](../../images/TimeLine.png)

---

### 5. Backlog:

![Backlog en Jira](../../images/BackLog.png)

---

### 6. Sprint Backlog:

![Sprint 1 en Jira](../../images/sprint1.png)

#### Justificación de la planeación del Sprint 1:

Para el primer sprint decidimos incluir las historias **DLC-2** (Crear cuenta bancaria - 8 puntos) y **DLC-4** (Consultar saldo - 3 puntos), totalizando **11 puntos de historia**.

**Razones de esta decisión:**

1. **DLC-2 es bloqueante:** Sin la capacidad de crear cuentas, ninguna otra funcionalidad puede operar. Es la base del sistema.

2. **DLC-4 complementa el MVP:** Después de crear cuentas, consultar saldo es la funcionalidad más básica que los usuarios esperan.

3. **Capacidad del equipo:** Con 2 desarrolladores y asumiendo una velocidad inicial conservadora, 11 puntos es una carga razonable para un sprint de 2 semanas.

4. **DLC-3 se pospone:** Aunque tiene prioridad alta, depende de DLC-2 y agregar sus 5 puntos (total 16) sobrecarga el sprint inicial.

5. **DLC-5 es prioridad media:** Se desarrollará en sprints posteriores.

**Asignación de tareas:**

- **Rafael Moreno:** DLC-6, DLC-7, DLC-12
- **Cristian Gonzalez:** DLC-8, DLC-13, DLC-14
