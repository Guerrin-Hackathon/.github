# Güerrín 🍕

Repositorio para proyecto realizado durante hackathon King Of Devs. Utilizamos Immutable X, un rollup de Ethereum.

## Abstract

Las comunidades nativas de internet no tienen sistemas de rewards propios (que no dependan de una plataforma en particular). Para eso creamos un sistema enfocado en normies, donde cualquier persona puede crear un reward para distribuir entre sus amigos, fans, etc.

El usuario puede iniciar sesión con su wallet o mismo con mail, a través de Magic Link, gracias al SDK de Immutable X lo permite. 

Cada usuario puede crear su colección de rewards, y distribuirlo simplemente con los mails de los receptores. 

Una vez hecho eso, los receptores de esa distribución recibirán un link donde podrán claimear su reward, pasando el ownership del reward del creador hasta el usuario final. 

## Tecnologías usadas

Usando Typescript como lenguaje de programación: 

- Frontend:
  - [Next.js](https://github.com/vercel/next.js) - Framework de React
- Backend: 
  - [Express.js]([https://github.com/vercel/next.js](https://expressjs.com))- Framework para Node.js
  - [Immutable X](https://www.immutable.com) - Zero Knowledge rollup donde almacenamos los coleccionables generados
  - [Mongo DB](https://www.mongodb.com) - No SQL database
  - Ethereum - Smart Contract Solidity ERC 721 (Adapatado a los requerimientos de Immutable X)
- Guía utilizada:
  - [NFT Minting Tutorial](https://docs.x.immutable.com/docs/zero-to-hero-nft-minting/) - Tutorial de Minting NFTs con Immutable X.
  
  
## Explicación de la Arquitectura
Para el diseño priorizamos dos atributos por sobre el resto: Experiencia de Usuario y Escalabilidad (preservando seguridad de L1). Por eso decidimos utilizar una L2 centralizada y especializada en NFTs que nos permite abstraer al usuario de ciertas características de Web3 (private keys si lo desea y gas fees). Para mejorar aún más la experiencia, los usuarios siempre tienen custodia de sus NFTs y utilizamos nuestro backend únicamente para realizar el minting de nuestra colección. Esta colección consiste de un contrato ERC-721 (modificado para interactuar con el rollup) que se encuentra en Ethereum L1, el minting y la transferencia de los activos ocurren off-chain para escalar. 
  
  
## Cómo correr el proyecto 
### 1. Env vars

#####  Backend

Crear un archivo en el root del proyecto llamado `.env.local`

```
NODE_ENV =
PORT =
DB_URL = 
DB_NAME = 
SALT = 
JWT_KEY =
NFT_STORAGE_API_KEY = 
#=============================================
# General
#=============================================
ALCHEMY_API_KEY=
# ropsten/mainnet etc.
ETH_NETWORK=
# IMX API endpoint
PUBLIC_API_URL=
STARK_CONTRACT_ADDRESS=
REGISTRATION_ADDRESS=
GAS_LIMIT=
GAS_PRICE=

#=============================================
# Bulk Minting
#=============================================
PRIVATE_KEY1=
TOKEN_ADDRESS=
BULK_MINT_MAX=

#=============================================
# Onboarding
#=============================================
OWNER_ACCOUNT_PRIVATE_KEY=
COLLECTION_CONTRACT_ADDRESS=
COLLECTION_PROJECT_ID=
INITIALIZE_METADATA=
```

##### Frontend
Crear un archivo en el root del proyecto llamado `.env.local`

```
ADDRESS= 
IMMUTABLEX_API=
API_URL=
```

`ADDRESS` debería ser el intermediario donde se envían las rewards antes de ser claimeadas por el usuario. Por una cuestión de tiempo, utilizamos una wallet para hacer de pasamanos. 
(Address utilizada en pruebas: 0x73D873D25BBE8BaFA27dD20c95A71AF125820a7C)

`IMMUTABLEX_API` es el link donde se encuentra la API utilizada de Immutable X. 
(Api url utilizada en pruebas https://api.sandbox.x.immutable.com/v1)

`API_URL` es el link a nuestro servidor, donde ocurre toda la logica de creación y envío de emails 
(http://localhost:8000/)

### 2. Run backend 

Hay que tener corriendo mongodb. 

Correr `npm install && npm run dev`


### 3. Run front 

Correr `npm run dev`

Nota: Hay que asegurarse de correr las aplicaciones en puertos distintos,e ingresar bien los links en el .env

## Authors 
- Julián Arce
- Roberto Catalán
- Marcos Dedeu
- Gian Luca Pecile 
- Ezequiel Pérez
  
  
  
  
