# 🕯️ LUMEN — Decentralized Storefront on Solana

Un marketplace minimalista, eficiente y totalmente on‑chain para gestionar productos digitales mediante PDAs.

---

## ✨ Descripción General
LUMEN es un smart contract construido con Anchor sobre la red Solana, diseñado para ofrecer una infraestructura ligera y segura para administrar inventarios on‑chain. 

Cada producto registrado se almacena como una PDA única, garantizando integridad, soberanía del usuario y eficiencia en costos de renta. El objetivo del proyecto es demostrar cómo un sistema CRUD puede implementarse de forma profesional en Solana, manteniendo buenas prácticas, seguridad y claridad arquitectónica.

---

## 🧩 Características Principales

### 🛒 1. Registro de Productos
Los usuarios pueden listar artículos con:
* **Nombre:** Hasta 32 caracteres.
* **Precio:** Definido en lamports.
* **Estado de disponibilidad:** (is_available).
* **Propietario:** Wallet del creador.

Cada producto vive en su propia PDA derivada de la semilla:
`["item_v1", owner_pubkey, title]`

### 🔄 2. Actualización Segura
Solo el propietario puede:
* Cambiar el precio.
* Modificar la disponibilidad (ej. “En stock” / “Agotado”).
* La validación se realiza mediante `has_one = owner` y seeds verificadas directamente en el contrato.

### 🗑️ 3. Eliminación con Recuperación de Renta
Al eliminar un producto:
* La cuenta se cierra permanentemente.
* El depósito de renta se devuelve automáticamente al propietario.
* Esto convierte a LUMEN en un sistema **rent‑neutral**, ideal para inventarios dinámicos.

---

## 🏛️ Arquitectura del Programa
LUMEN está construido bajo una estructura modular y clara:

### 📦 Cuentas
* **StoreItem:** Modelo principal del producto. Incluye owner, título, precio, disponibilidad y bump.

### 🧭 Contextos
* **AddItem:** Inicializa la PDA del producto.
* **UpdateItem:** Valida propiedad y actualiza campos.
* **DeleteItem:** Cierra la cuenta y libera renta.

### 🧱 Diseño Basado en PDAs
El uso de PDAs garantiza direcciones determinísticas, seguridad sin necesidad de almacenar índices globales y escalabilidad total.

---

## 🔐 Seguridad y Buenas Prácticas
* **Validación de Propietario:** Solo el creador del producto puede modificarlo o eliminarlo.
* **Validación de Entradas:** Títulos limitados (1-32 caracteres) y precios siempre mayores a 0.
* **Gestión de Seeds:** Evita colisiones y asegura la integridad de los datos.
* **Cierre Seguro:** Uso de `close = owner` para garantizar el retorno de fondos.

---

## ⚡ Eficiencia y Costos
LUMEN no mantiene listas globales; cada producto es independiente. El costo de almacenamiento se recupera al eliminarlo, lo que lo hace ideal para marketplaces con alta rotación de inventario.

---

## 🧪 Pruebas y Calidad
El proyecto incluye una suite de pruebas (TypeScript + Mocha/Chai) que valida:
* Creación y persistencia de productos.
* Actualización de datos y restricciones de seguridad.
* Eliminación y recuperación total de renta.

---

## 🚀 Cómo Ejecutarlo Localmente

### Requisitos
* Solana CLI 1.18.x
* Anchor 0.30.x
* Node.js 20.x
* Yarn

### Comandos Principales
```bash
# 1. Instalar dependencias
yarn install

# 2. Compilar el programa
anchor build

# 3. Ejecutar pruebas de integración
anchor test

### Comandos Críticos y Estructura
Para instalar y probar la integridad del contrato, usa estos comandos:

```bash
# 1. Instalar dependencias
yarn install

# 2. Compilar el programa
anchor build

# 3. Ejecutar pruebas de integración
anchor test

# Estructura del Repositorio
LUMEN/
├── programs/
│   └── lumen/
│       └── src/
│           ├── lib.rs     # Lógica principal e instrucciones
│           ├── state.rs   # Definición de datos del juego
│           └── errors.rs  # Mensajes de error personalizados
├── tests/                 # Suite de pruebas en TypeScript (Mocha/Chai)
├── migrations/            # Scripts de despliegue
└── Anchor.toml            # Configuración del framework
