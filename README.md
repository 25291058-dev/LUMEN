# 🕯️ LUMEN | Gaming Marketplace on Solana

¡Bienvenidos a **LUMEN**! Este es mi proyecto para la certificación de Solana. Es una infraestructura descentralizada diseñada para gestionar inventarios de videojuegos en la blockchain, priorizando la seguridad y el ahorro de recursos (Rent Efficiency).

---

## 🌟 ¿Qué es LUMEN?
LUMEN permite a los usuarios registrar sus videojuegos en la red de forma soberana. Cada producto es una cuenta única que vive en la blockchain, permitiendo un comercio transparente, inmutable y sin intermediarios.

### Funciones Principales:
* **Añadir productos:** Registra títulos con nombre, precio y disponibilidad.
* **Actualizar listados:** Modifica el precio o cambia el estado a "Agotado" en tiempo real.
* **Eliminar con reembolso:** Si retiras un producto, el programa cierra la cuenta y **te devuelve los SOL** que tenías retenidos por la renta.

---

## 🛠️ El Corazón del Proyecto (Arquitectura)

Para este proyecto, decidí usar **PDAs (Program Derived Addresses)**. Esto significa que no guardo todo en una lista gigante, sino que cada juego tiene su propio "espacio" seguro derivado matemáticamente a partir del título y la wallet del creador.

### ¿Por qué este proyecto es sólido?
1.  **Seguridad de Dueño:** Implementé una validación donde solo el creador del producto tiene el permiso firmado para editarlo o borrarlo.
2.  **Eficiencia de Renta:** Al usar la función de cierre de cuentas (`close = owner`), el costo de uso es prácticamente cero a largo plazo, ya que el capital se libera al terminar el ciclo de venta.
3.  **Código Modular:** Separé la lógica en archivos específicos para que sea un proyecto limpio y profesional.

---

## 📊 Eficiencia y Benchmarking
LUMEN está diseñado para ser **"Gas-Neutral"**. Al vender o retirar un producto, el programa libera el espacio en la blockchain, recuperando el 100% del depósito de renta inicial. Esto lo hace ideal para mercados con mucho movimiento de inventario.

---

## 🚀 Despliegue y Validación

### Entorno de Desarrollo
Para correr este proyecto, asegúrate de tener:
* **Solana CLI** 1.18.x
* **Anchor CLI** 0.30.x
* **Node.js** 20.x

### Comandos Críticos
Para instalar y probar la integridad del contrato, usa estos comandos:

```bash
# 1. Instalar dependencias
yarn install

# 2. Compilar el programa
anchor build

# 3. Ejecutar pruebas de integración
anchor test

Gemini ha dicho
¡Entendido! Aquí tienes el contenido completo del README.md listo para que lo copies y pegues. Tiene el balance perfecto: se ve profesional, es fácil de entender y demuestra que dominas la técnica de Solana.

Markdown
# 🕯️ LUMEN | Gaming Marketplace on Solana

¡Bienvenidos a **LUMEN**! Este es mi proyecto para la certificación de Solana. Es una infraestructura descentralizada diseñada para gestionar inventarios de videojuegos en la blockchain, priorizando la seguridad y el ahorro de recursos (Rent Efficiency).

---

## 🌟 ¿Qué es LUMEN?
LUMEN permite a los usuarios registrar sus videojuegos en la red de forma soberana. Cada producto es una cuenta única que vive en la blockchain, permitiendo un comercio transparente, inmutable y sin intermediarios.

### Funciones Principales:
* **Añadir productos:** Registra títulos con nombre, precio y disponibilidad.
* **Actualizar listados:** Modifica el precio o cambia el estado a "Agotado" en tiempo real.
* **Eliminar con reembolso:** Si retiras un producto, el programa cierra la cuenta y **te devuelve los SOL** que tenías retenidos por la renta.

---

## 🛠️ El Corazón del Proyecto (Arquitectura)

Para este proyecto, decidí usar **PDAs (Program Derived Addresses)**. Esto significa que no guardo todo en una lista gigante, sino que cada juego tiene su propio "espacio" seguro derivado matemáticamente a partir del título y la wallet del creador.

### ¿Por qué este proyecto es sólido?
1.  **Seguridad de Dueño:** Implementé una validación donde solo el creador del producto tiene el permiso firmado para editarlo o borrarlo.
2.  **Eficiencia de Renta:** Al usar la función de cierre de cuentas (`close = owner`), el costo de uso es prácticamente cero a largo plazo, ya que el capital se libera al terminar el ciclo de venta.
3.  **Código Modular:** Separé la lógica en archivos específicos para que sea un proyecto limpio y profesional.

---

## 📊 Eficiencia y Benchmarking
LUMEN está diseñado para ser **"Gas-Neutral"**. Al vender o retirar un producto, el programa libera el espacio en la blockchain, recuperando el 100% del depósito de renta inicial. Esto lo hace ideal para mercados con mucho movimiento de inventario.

---

## 🚀 Despliegue y Validación

### Entorno de Desarrollo
Para correr este proyecto, asegúrate de tener:
* **Solana CLI** 1.18.x
* **Anchor CLI** 0.30.x
* **Node.js** 20.x

### Comandos Críticos
Para instalar y probar la integridad del contrato, usa estos comandos:

```bash
# 1. Instalar dependencias
yarn install

# 2. Compilar el programa
anchor build

# 3. Ejecutar pruebas de integración
anchor test
## 📁 Estructura del Repositorio
LUMEN/
├── programs/lumen/src/
│   ├── lib.rs     # Lógica principal e instrucciones
│   ├── state.rs   # Definición de datos del juego
│   └── errors.rs  # Mensajes de error personalizados
└── tests/         # Suite de pruebas en TypeScript (Mocha/Chai)
