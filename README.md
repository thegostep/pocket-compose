# pocket-compose

Requires docker-compose installed on ubuntu machine.

Install docker image.  
`docker pull poktnetwork/pocket-core:RC-0.4.0`

Clone git repo.  
`git clone https://github.com/thegostep/pocket-compose.git .`

Create ssl certificates.  
`sudo openssl req -x509 -newkey rsa:4096 -keyout nginx/ssl/key.pem -out nginx/ssl/cert.pem -days 365 -nodes -subj '/CN=localhost'`

Create Diffie-Hellman group.  
`sudo openssl dhparam -out nginx/ssl/dhparam.pem 4096`

Start containers.  
`docker-compose up -d`

Enter pocket-core container.  
`docker exec -it --user root pocket-core /bin/bash`

Create account.  
`pocket accounts create`

Store account as validator.  
`pocket accounts set-validator <address>`

Bootstrap node sync with seed nodes.  
`pocket start --seeds="b3d86cd8ab4aa0cb9861cb795d8d154e685a94cf@seed1.testnet.pokt.network:26656,17ca63e4ff7535a40512c550dd0267e519cafc1a@seed2.testnet.pokt.network:26656,f99386c6d7cd42a486c63ccd80f5fbea68759cd7@seed3.testnet.pokt.network:26656"`

## Troubleshoot

If you want to start a fresh sync, run `pocket reset` once in pocket-core container.

## Additional Resources

- https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-18-04
- https://www.freecodecamp.org/news/docker-nginx-letsencrypt-easy-secure-reverse-proxy-40165ba3aee2/
