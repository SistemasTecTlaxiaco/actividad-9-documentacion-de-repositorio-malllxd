# GreenTech Hub – Plataforma Descentralizada de Donaciones Ecológicas

## Descripción del Proyecto

**GreenTech Hub** es una plataforma descentralizada de filantropía ambiental diseñada para conectar proyectos de sostenibilidad con donantes. Su objetivo es permitir que organizaciones y comunidades registren iniciativas ecológicas (como reforestación o conservación) y reciban fondos de manera directa, transparente y sin los altos costos operativos de los intermediarios tradicionales.

A diferencia de los sistemas de financiamiento centralizados, GreenTech Hub utiliza tecnología **blockchain** para gestionar la trazabilidad de las donaciones. Esto asegura que cada recurso aportado sea verificable e inmutable, fortaleciendo la confianza del donante mediante un sistema donde el destino del dinero es público y auditable.

El sistema opera sobre la red de pruebas **Stellar Testnet** y emplea contratos inteligentes desarrollados con **Soroban**, automatizando el registro de proyectos y la asignación de donaciones sin depender de una entidad central que controle la lógica de negocio.

## Características del Sistema

* **Descentralización:** La lógica de validación de proyectos y recepción de fondos reside en contratos inteligentes, no en servidores privados.
* **Transparencia Total:** Las donaciones son trazables desde el origen hasta el proyecto destino a través del ledger público de Stellar.
* **Seguridad Web3:** Uso de firmas digitales para garantizar que solo los responsables autorizados gestionen las iniciativas.
* **Automatización de Impacto:** Los contratos inteligentes ejecutan funciones programadas, eliminando la burocracia administrativa.
* **Trazabilidad:** Cada operación genera un hash único verificable en exploradores de blockchain (como Stellar Expert).
* **API de Integración:** Endpoints funcionales para interactuar con la blockchain de forma sencilla.

## Objetivos del Proyecto

### Objetivo General
Desarrollar una plataforma descentralizada que gestione donaciones para proyectos ecológicos utilizando tecnología blockchain, garantizando la transparencia absoluta y la eliminación de intermediarios.

### Objetivos Específicos
* Implementar un contrato inteligente en Rust (Soroban) para el registro y consulta de iniciativas ambientales.
* Desplegar el contrato en la red Stellar Testnet para validar su funcionamiento en un entorno real.
* Garantizar la seguridad de las transacciones mediante el uso de llaves privadas y variables de entorno.
* Realizar pruebas de integración completas desde la API Backend hasta la red blockchain.
## Arquitectura del Proyecto

```text
GreenTech/
│
├── greentech-contrato/  → Smart Contract (Rust + Soroban)
└── greentech-api/       → API Backend (Node.js)

Smart Contract
Lenguaje: Rust
```


## Función principal: Gestión de datos y fondos en la blockchain.

Operaciones: Registro de iniciativas y consulta de proyectos ecológicos.

API Backend
Tecnología: Node.js con Express.

Función: Intermediario entre el cliente y la blockchain.

Responsabilidades: Envío de transacciones, lectura de datos del contrato y manejo de errores.

## Instalación del Proyecto
1. Clonar repositorio
Bash
git clone [https://github.com/GerardoNR/GreenTech.git](https://github.com/GerardoNR/GreenTech.git)
cd GreenTech
2. Compilar contrato
Bash
cd greentech-contrato
cargo build --target wasm32v1-none --release
3. Desplegar contrato en TestNet
Bash
soroban contract deploy \
--wasm target/wasm32v1-none/release/greentech_contrato.wasm \
--source default \
--network testnet
Contract ID generado:
CC7X... (Pega aquí el ID generado por la terminal)

4. Configurar API
Bash
cd ../greentech-api
npm install
Archivo .env:

Fragmento de código
SECRET_KEY=TU_SECRET_KEY
CONTRACT_ID=TU_CONTRACT_ID_GENERADO
5. Ejecutar API
Bash
node index.js
Servidor ejecutándose en: http://localhost:3000

Endpoints de la API
Registrar Iniciativa
POST /registrar

JSON
{
  "nombre": "Reforestación Mixteca"
}
Respuesta:

JSON
{
  "success": true,
  "hash": "8f32a0b89db63011abffa86863a30a0f0fb40d4c8b6889b20503c6c5ff0922bf"
}
Obtener Proyectos
GET /proyectos
Respuesta:

JSON
{
  "success": true,
  "proyectos": ["Reforestación Mixteca"]
}
Pruebas de Integración
Se realizaron pruebas completas verificando:

Registro exitoso en la blockchain de Stellar.

Generación y validación del hash de transacción.

Lectura de datos persistentes desde el Smart Contract.

Seguridad
Uso de variables de entorno para proteger llaves privadas.

No exposición de información sensible en el código fuente.

Implementación de manejo de errores con try/catch y asincronía.

Conclusión
GreenTech Hub representa una solución moderna basada en Web3 que demuestra cómo los contratos inteligentes pueden transformar la filantropía ambiental, eliminando la opacidad y fortaleciendo la confianza entre donantes y proyectos mediante sistemas descentralizados.






