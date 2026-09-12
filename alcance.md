# Alcance comprometido — KoiCloud

**Categoría:** Base de Datos como Servicio (DBaaS) · PostgreSQL  
**Superficie:** únicamente interfaz web  
**Realidad del equipo:** un estudiante implementa y defiende el sistema

No hay división en núcleo / deseable / ambicioso. Lo que aparece abajo es el compromiso completo del semestre. Lo que no aparece está en *Fuera de alcance*.

## Compromiso

1. **Cuentas:** registro, verificación de correo, recuperación de contraseña, inicio de sesión con JWT + refresh; roles Cliente y Administrador.
2. **Suscripciones:** catálogo Sandbox / Micro / Pro (nombre, descripción, precio, vigencia); contratación con pago simulado; historial; renovación y cancelación.
3. **Catálogo DBaaS:** crear, consultar estado, obtener cadena de conexión y eliminar instancias PostgreSQL 16 en contenedores Docker reales.
4. **Configuración básica al crear:** nombre del pond, versión del motor (16), plan asociado a la suscripción.
5. **Consola SQL en el navegador:** modo lectura por defecto, timeout y límite de filas; modo escritura con confirmación.
6. **Respaldos:** copia diaria automática y restauración bajo demanda (`pg_dump` / `pg_restore`).
7. **Uso:** horas de instancia y almacenamiento estimados a partir de muestras del agente; vista mensual simple.
8. **Administración:** el Administrador consulta usuarios, suscripciones e instancias.
9. **Arquitectura:** monolito modular FastAPI (control plane) + node-agent (data plane) + PostgreSQL interno; cola de trabajos en la misma base; un solo nodo VPS.

## Fuera de alcance

- CLI e infraestructura declarativa.
- Servidor MCP / acceso para agentes de IA / llaves de agente.
- Auto-curación como garantía de producto o demostración de caos (recuperación automática ante `docker kill`).
- Validación empírica de hipótesis de precio o de factura local con NIT (requiere usuarios reales pagando).
- Otros motores (MySQL, MongoDB), branching, réplicas, connection pooler, extensiones.
- Organizaciones / equipos / invitaciones.
- Cobro real, pasarelas de pago, facturación electrónica ante la SAT, SLA.
- Alta disponibilidad, multi-nodo, migración de instancias.
- Roles Soporte técnico y Operador de infraestructura; página pública de estado; panel de flota.
- Sandbox sin registro (puede explorarse si sobra tiempo; no forma parte del compromiso).
- OAuth 2.1 para agentes y autenticación de dos factores.

## Problemas que el proyecto sí aborda

| Problema | Cómo se verifica |
|---|---|
| Poner en marcha Postgres exige operación que el cliente no quiere hacer | Tiempo desde “crear pond” hasta URI utilizable |
| El estado del servicio es opaco | El panel muestra estado y health del contenedor |
| No hay cliente SQL a mano | Consola web ejecuta `SELECT` y muestra filas |
| Hay que demostrar suscripción/pago académicos | Flujo simulado con historial e factura PDF simple |

## Hipótesis de negocio (no comprometidas)

El posicionamiento comercial (hueco de precio ~USD 5 vs. ~USD 25; factura con NIT) orienta el catálogo, pero **no** se evalúa ni se promete como resultado del semestre.
