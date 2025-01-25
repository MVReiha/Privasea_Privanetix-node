# Privanetix node
## Minimum system requirements
OS: Ubuntu (Recommended)

The CPU can only be amd64 architecture

Storage: 100GB available storage

Memory: 4GB RAM

Processor: A processor with 6 cores, x86 architecture.

##  1. Install Docker 
If Docker is already installed, you can skip this step. Alternatively, you can ask ChatGPT for help with Docker installation. The following steps are for reference

Install necessary dependencies
```
sudo apt update && sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

Add Docker's official GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Add Docker's official repository
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

Update APT package index
```
sudo apt update
```
Install Docker
```
sudo apt install -y docker-ce
```
 
Verify if Docker is installed successfully

```
sudo docker --version
```

## 2. First pull the docker image using the following command:
```
docker pull privasea/acceleration-node-beta:latest
```

## 3. Node program configuration

1. Buat direktori :
```
mkdir -p  /privasea/config && cd  /privasea
```
2. Get the keystore file (simpan baik-baik dan jangan sampai hilang)
   
Use an existing wallet keystore file or execute the following command to generate a new one:
```
docker run -it -v "/privasea/config:/app/config"  \
privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
 ![Screenshot 2025-01-25 111802](https://github.com/user-attachments/assets/a84c8952-6b1a-4f8d-b16e-e77874d396b4)



Check if there is a keystore file in the /privasea/config directory:
```
cd /privasea/config && ls
```
Rename the keystore file you noted in the previous step:
```
mv ./UTC--2025-01-06T06-11-07.485797065Z--f07c3ef23ae7beb8cd8ba5ff546e35fd4b332b34  ./wallet_keystore
```
Replace UTC--2025-01-06T06-11-07.485797065Z--f07c3ef23ae7beb8cd8ba5ff546e35fd4b332b34 with the name of the keystore file you found.

Check that the wallet_keystore file in the /privasea/config folder was modified correctly:
```
ls 
```
![2](https://github.com/user-attachments/assets/aa4c5642-f254-4590-be85-3194c5391d89)

## 4. Link node address and reward address
Use the wallet address corresponding to the keystore file to link it with the reward address on DeepSea https://deepsea-beta.privasea.ai/privanetixNode

![3](https://github.com/user-attachments/assets/c9e27d04-e548-422e-9b70-f1980955a266)

## 5. Start the node

Run the command to start the Privanetix(acceleration) node:
```
cd /privasea/
```
```
docker run  -d   -v "/privasea/config:/app/config" \
  -e KEYSTORE_PASSWORD=123456 \
  privasea/acceleration-node-beta:latest
```

Parameter Explanation:
 EYSTORE_PASSWORD: The password corresponding to the keystore file
 
 /privasea/config: The local directory where the wallet_keystore file is stored

![4](https://github.com/user-attachments/assets/ae0188bc-551f-4d78-ba95-b2389945dcf9)

check the dashboard whether the node is online

![Screenshot 2025-01-25 111202](https://github.com/user-attachments/assets/bb31680e-e800-4515-a66e-77e6f66606c1)


## 6. View the node health
```
# Command to check the node's running status:
docker logs -f (nama docker nya)

#Parameter Explanation:
# eb723c38e3e6283f6c9d50512828408bd6df2fbba22d1991daa459778d3e73bc is the container ID from the previous operation.
```


## Done and LFG 


