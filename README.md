# DOSW_Lab5_CR - Bankify

## INTEGRANTES
Cristian Jose Gonzalez Rodriguez
Rafael Santiago Moreno velasquez

## Objetivo del Laboratorio
El objetivo principal de este laboratorio es implementar la **estructura base y el núcleo funcional** de la plataforma Bankify utilizando **Maven** como herramienta de gestión de dependencias y construcción. 

A través de este ejercicio se busca:
1.  **Lógica de Negocio:** Implementar las reglas de validación para la creación de cuentas bancarias (10 dígitos, códigos de banco 01/02) y la gestión de saldos.
2.  **Interoperabilidad:** Preparar el sistema para la generación de reportes tributarios en formatos diversos (PDF para clientes y JSON para entes gubernamentales como la DIAN).

## ROLES EQUIPO SCRUM
1. **Cristian Gonzalez:** Product Owner
2. **Rafael Moreno:** Scrum Master
**Ambos:** Desarrollador

---

## Estimación con Planning Poker

### ¿Cuál fue la mayor dificultad a la hora de estimar?

La mayor dificultad fue evaluar la complejidad de las validaciones de negocio, especialmente en la historia DLC-2 (Crear cuenta bancaria validada). No teníamos claridad sobre cuánto esfuerzo requeriría implementar las validaciones del número de cuenta de 10 dígitos y la verificación de los códigos de banco. Además, surgieron dudas sobre si debíamos considerar el tiempo de configuración de Maven y las dependencias necesarias dentro de la estimación.

### ¿Fue fácil llegar a un consenso?

En general sí, aunque hubo discrepancias en 2 de las 4 historias. Para DLC-2 y DLC-4, las estimaciones iniciales variaron entre 5 y 8 puntos. Después de discutir los criterios de aceptación y aclarar el alcance técnico, logramos consenso. Las historias DLC-3 y DLC-5 fueron más directas y alcanzamos acuerdo en la primera ronda de votación.

### ¿Cómo resolvieron los escenarios donde las estimaciones para la misma historia de usuario no fueron cercanas?

Cuando las estimaciones no fueron cercanas, aplicamos la dinámica estándar de Planning Poker: los integrantes con las estimaciones más altas y más bajas explicaron su razonamiento. Por ejemplo, en DLC-2, quien votó 8 puntos argumentó la complejidad de las validaciones y el manejo de excepciones, mientras quien votó 5 consideraba que las validaciones eran relativamente simples. Después de la discusión, identificamos que faltaba considerar las pruebas unitarias, lo que nos llevó a un consenso de 8 puntos.