# 🕯️ LUMEN: The Definitive On-Chain Game Asset Protocol

![Solana ecosystem](https://img.shields.io/badge/Solana-Mainnet--Beta-14F195?style=for-the-badge&logo=solana&logoColor=000)
![Anchor Framework](https://img.shields.io/badge/Anchor-0.30.1-3b82f6?style=for-the-badge&logo=anchor&logoColor=fff)
![Rust Edition](https://img.shields.io/badge/Rust-2021-DEA584?style=for-the-badge&logo=rust&logoColor=000)

> **LUMEN** es una infraestructura de estado persistente diseñada para la gestión de inventarios digitales de alto rendimiento en la red Solana. No es solo un catálogo; es un motor de propiedad soberana para activos de videojuegos.

---

## 💎 Filosofía del Proyecto
En un ecosistema saturado de aplicaciones web2 disfrazadas de web3, **LUMEN** nace para demostrar el poder de la **Componibilidad** y la **Eficiencia de Alquiler (Rent Efficiency)**. Cada interacción está optimizada para consumir el mínimo de recursos, devolviendo el control total del capital al usuario final.

---

## 🛠️ Arquitectura Técnica de Élite

### 1. Sistema de Direccionamiento PDA (Program Derived Addresses)
LUMEN no utiliza bases de datos centralizadas. La localización de cada activo se deriva matemáticamente mediante semillas únicas:
`["game_item", owner_pubkey, game_title_slug]`
Esto garantiza que:
- No existen colisiones de datos.
- Las búsquedas son instantáneas a nivel de protocolo (O(1)).
- La seguridad está delegada directamente al Runtime de Solana.

### 2. Ciclo de Vida Atómico (CRUD Engine)
| Operación | Lógica de Negocio | Impacto en Ledger |
| :--- | :--- | :--- |
| **Initialize** | Registro de metadatos y asignación de espacio. | Creación de Cuenta (Rent Deposit) |
| **Sync** | Actualización de precio y estado de disponibilidad. | Modificación de Estado in-place |
| **Purge** | Cierre definitivo del listado por el propietario. | **Reclamo de SOL (Rent Refund)** |

### 3. Capa de Seguridad "Guardian"
El programa implementa validaciones de seguridad de triple capa:
1. **Signer Validation:** Solo el creador puede firmar mutaciones de estado.
2. **Space Constraints:** Optimización estricta de bytes para evitar ataques de inflado de renta.
3. **Semantic Errors:** Códigos de error personalizados que facilitan la integración con el Frontend.

---

## 📂 Anatomía del Protocolo
El repositorio sigue los estándares de la industria para auditorías y legibilidad:

```bash
LUMEN/
├── programs/
│   └── lumen/
│       ├── src/
│       │   ├── lib.rs        # Core: Orquestación de instrucciones
│       │   ├── state.rs      # Data Schemas: Estructuras de bajo nivel
│       │   ├── errors.rs     # Guard: Definición de fallos semánticos
│       │   └── constants.rs  # Config: Seeds y parámetros globales
├── tests/
│   └── lumen.test.ts         # QA: Suite de pruebas de integración
├── migrations/               # Scripts de despliegue controlado
└── Anchor.toml               # Configuración del entorno de red

🚀 Despliegue y Validación
Entorno de Desarrollo
Para replicar el entorno de producción de LUMEN, asegúrese de tener:

Solana CLI 1.18.x

Anchor CLI 0.30.x

Node.js 20.x

Comandos Críticos
# Instalar dependencias
yarn install

# Compilación con optimización de Rust
anchor build

# Ejecución de la suite de pruebas unitarias y de integración
anchor test --detach

📊 Benchmarking de Eficiencia
LUMEN está diseñado para ser "Gas-Neutral". Al utilizar el cierre de cuentas (close = owner), el costo neto de mantener un inventario a largo plazo es prácticamente cero, ya que el depósito de renta se recupera íntegramente al finalizar la venta o retirar el producto.

🛡️ Roadmap & Escalabilidad
[ ] LUMEN V2: Soporte nativo para Royalties programables.

[ ] Cross-Game: Integración con estándares SPL-Metadata.

[ ] Oracles: Precios dinámicos basados en Pyth Network.
