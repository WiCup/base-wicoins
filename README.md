# **Wicoins Project Test**

![Wicoins Project](https://res.cloudinary.com/gregoryinnovo/image/upload/v1728860743/foodhy/a3y5xbqiielugirsxy8h.png)

🚀 **Wicoin** es un proyecto de contrato inteligente y aplicación completa (backend + frontend) desarrollado para gestionar la emisión de tokens Wicoin y proporcionar la funcionalidad de **recarga** a través de la red **Base Sepolia**. Este proyecto utiliza **Solidity** para el contrato, **Node.js** para el backend, y un **frontend simple** en HTML/JavaScript para interactuar con el contrato.

## **Índice**

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Características](#características)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Uso](#uso)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Comandos Útiles](#comandos-útiles)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

---

## **Descripción del Proyecto**

Este proyecto tiene como objetivo proporcionar una solución sencilla para gestionar tokens mediante **Wicoin** y permitir que los usuarios recarguen sus saldos desde el frontend. Toda la lógica está desplegada en la red **Base Sepolia**, una red testnet compatible con Ethereum.

El backend gestiona las transacciones en la blockchain y se comunica con el contrato inteligente, mientras que el frontend permite que los usuarios realicen recargas de forma sencilla.

---

## **Características**

- Contrato inteligente para emisión de tokens Wicoin en Solidity.
- Función de recarga disponible en el backend que interactúa con la blockchain.
- Interfaz sencilla de frontend para realizar recargas.
- Conexión segura utilizando **dotenv** para manejar las claves privadas y configuraciones sensibles.
- Compatible con la red **Base Sepolia** para pruebas sin costo.

---

## **Requisitos**

- **Node.js** y **npm** instalados. Puedes verificar con:
  ```bash
  node -v
  npm -v
  ```
- **MetaMask** configurado con la red Base Sepolia.
- **ETH de prueba en Sepolia**. Puedes obtenerlo desde un [Sepolia Faucet](https://sepoliafaucet.com).
- **Hardhat** para compilar y desplegar contratos inteligentes:
  ```bash
  npm install --save-dev hardhat
  ```

---

## **Instalación**

1. **Clona el repositorio**:

   ```bash
   git clone https://github.com/tu-usuario/wicoin-project.git
   cd wicoin-project
   ```

2. **Instala las dependencias**:

   ```bash
   npm install
   ```

3. **Configura las variables de entorno**:
   Crea un archivo **`.env`** en la raíz del proyecto con el siguiente contenido:

   ```bash
   PRIVATE_KEY=tu_llave_privada
   SEPOLIA_RPC_URL=https://sepolia.base.org
   CONTRACT_ADDRESS=tu_direccion_del_contrato
   ```

4. **Compila el contrato inteligente**:

   ```bash
   npx hardhat compile
   ```

5. **Despliega el contrato en la red Sepolia**:
   Correr el comando script de despliegue o ejecutar el siguiente comando:

   ```bash
   npx hardhat run scripts/deploy.js --network sepolia
   ```

---

## **Uso**

1. **Crea el archivo `.env`**:

   - Asegúrate de crear un archivo `.env` en la carpeta del backend a partir del archivo de ejemplo `.env.example`.
   - Este archivo debe contener las siguientes credenciales necesarias:

     **Ejemplo del contenido de `.env`:**

     ```bash
     PRIVATE_KEY=tu_clave_privada
     SEPOLIA_RPC_URL=tu_infura_api_key
     CONTRACT_ADDRESS=tu_direccion_del_contrato
     ```

2. **Instala las dependencias necesarias**:
   Si no lo has hecho ya, instala las dependencias del backend y de los contratos:

   ```bash
   cd backend-wicoins
   npm install
   ```

3. **Inicia el Backend**:
   Inicia el servidor backend usando el siguiente comando:

   ```bash
   node backend-wicoins/main.js
   ```

4. **Abre el Frontend**:

   - Abre el archivo `frontend-wicoins/index.html` en tu navegador web.
   - Usa la interfaz para ingresar una dirección de Ethereum y el monto que deseas recargar.
   - Haz clic en el botón correspondiente para enviar la transacción.

5. **Prueba el Endpoint con un Cliente REST API (como Postman)**:

   - Si prefieres, también puedes probar el endpoint manualmente con Postman o cualquier otro cliente REST API.

     **Configuración del Request:**

     - **Método:** `POST`
     - **URL:** `http://localhost:3000/recharge`
     - **Body:** (en formato JSON)
       ```json
       {
         "account": "YOUR_ETHEREUM_ADDRESS",
         "amount": 50000
       }
       ```
     - **Respuesta esperada:**
       ```json
       {
         "status": "Success",
         "txHash": "0xe1c7247894423421347823abDHBSJKBKkjjkhbk99d74cc1b9269fda12e408f28e08b"
       }
       ```

6. **Verifica las Transacciones en la Blockchain**:
   - Una vez que realices una recarga, puedes verificar la transacción en la red **Sepolia**.
   - Visita el [explorador de Sepolia Etherscan](https://sepolia.etherscan.io) e ingresa el **hash de la transacción** para confirmar su estado.

---

## **Estructura del Proyecto**

```plaintext
wicoin-project/
│
├── backend-wicoins/         # Código backend en Node.js
│   ├── .env                 # Variables de entorno
│   ├── main.js              # Archivo principal del backend
│   ├── package.json         # Dependencias del backend
│   └── package-lock.json    # Bloqueo de versiones
│
├── frontend-wicoins/        # Interfaz frontend del proyecto de ejemplo
│   └── index.html           # Página HTML principal del frontend
│
├── wicoins-contracts/       # Contratos inteligentes y scripts de despliegue
│   ├── artifacts/           # Artefactos generados por Hardhat
│   ├── cache/               # Cache de Hardhat
│   ├── contracts/           # Contratos en Solidity
│   ├── ignition/            # Herramientas de despliegue avanzado
│   ├── node_modules/        # Dependencias del proyecto
│   ├── scripts/             # Scripts de despliegue y ejecución
│   ├── test/                # Pruebas para los contratos
│   ├── typechain-types/     # Tipos generados por TypeChain
│   ├── .env                 # Variables de entorno
│   ├── hardhat.config.ts    # Configuración de Hardhat
│   ├── package.json         # Dependencias del proyecto
│   ├── package-lock.json    # Bloqueo de versiones
│   ├── README.md            # Información del proyecto
│   └── tsconfig.json        # Configuración de TypeScript
```

---

## **Comandos Útiles**

- **Compilar el contrato**:

  ```bash
  npx hardhat compile
  ```

- **Desplegar el contrato**:

  ```bash
  npx hardhat run scripts/deploy.js --network sepolia
  ```

- **Iniciar el backend**:

  ```bash
  node backend-wicoins/main.js
  ```

- **Verificar el balance de la cuenta**:
  Agrega este fragmento al backend para imprimir el balance:
  ```javascript
  const balance = await provider.getBalance(wallet.address);
  console.log(`Balance: ${ethers.formatEther(balance)} ETH`);
  ```

---

## **Licencia**

Licencia privada. Todos los derechos reservados.
