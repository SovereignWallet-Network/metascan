# Metascan Explorer
Blockchain explorer for Metablockchain

## Quick Deploymenent 
Uses container for Mysql & connects to hosted node of metablockchain

# Polkascan Open-Source
Polkascan Open-Source Application

## Deployment (Use System MySQL)
### Step 1: Clone repository: 
```bash
git clone https://github.com/SovereignWallet-Network/metascan.git
```
### Step 2: Change directory: 
```bash
cd metascan
```
### Step 3: Make sure to also clone submodules within the cloned directory: 
```bash
git submodule update --init --recursive
```
### Step 4: Then build the other docker containers
```bash
docker-compose -p metablockchain -f docker-compose.metablockchain-quick.yml up --build
```

## Deployment Full (Using System MySQL)
### Step 1: Clone repository: 
```bash
git clone https://github.com/SovereignWallet-Network/metascan.git
```
### Step 2: Change directory: 
```bash
cd metascan
```
### Step 3: Make sure to also clone submodules within the cloned directory: 
```bash
git submodule update --init --recursive
```
### Step 4: Make sure that the mysql server is running & is configured correctly in the  `docker-compose.metablockchain.yml` file

### Step 5: Make sure that the RPC URL is configured correctly
### Step 6: Then build the other docker containers
```bash
docker-compose -p metablockchain -f docker-compose.metablockchain.yml up --build
```
## Links to applications
* Metascan Explorer GUI: http://127.0.0.1:8080
* Monitor harvester progress: http://127.0.0.1:8080/metablockchain/harvester/admin
* Harvester Task Monitor: http://127.0.0.1:5555
* Polkadot JS Apps: http://127.0.0.1:8081

## Add new types for blockchain

* Modify `harvester/app/type_registry/metablockchain_types.json` to match the introduced types of the chain
* Truncate `runtime` and `runtime_*` tables on database
* Start harvester
* Check http://127.0.0.1:8080/<NETWOR_ID>/runtime-type if all type are now correctly supported
* Monitor http://127.0.0.1:8080/<NETWOR_ID>/harvester/admin if blocks are being processed and try to restart by pressing "Process blocks in harvester queue" if process is interupted.

## Cleanup Docker
Use the following commands with caution to cleanup your Docker environment.

### Prune images
```bash
docker system prune
```

### Prune images (force)
```bash
docker system prune -a
```

### Prune volumes
```bash
docker volume prune
```
