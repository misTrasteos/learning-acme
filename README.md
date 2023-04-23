 ansible-playbook acme_account.yaml


learning-acme-pebble-1        | Pebble 2023/04/23 12:11:56 GET /dir -> calling handler()
learning-acme-pebble-1        | Pebble 2023/04/23 12:11:56 HEAD /nonce-plz -> calling handler()
learning-acme-pebble-1        | Pebble 2023/04/23 12:11:56 POST /sign-me-up -> calling handler()
learning-acme-pebble-1        | Pebble 2023/04/23 12:11:56 There are now 1 accounts in memory





server_certificate

 
TASK [Dump information]

ok: [localhost] => {
    "msg": [
        "DNS:anotherexample.org",
        "DNS:yetanotherexample.org",
        "DNS:example.org"
    ]
}



https://www.digitalocean.com/community/tutorials/how-to-acquire-a-let-s-encrypt-certificate-using-ansible-on-ubuntu-18-04
https://letsencrypt.org/docs/challenge-types/


# Certbot

**Register**

```sudo certbot register --server https://localhost:14000/dir --no-verify-ssl --agree-tos -m random@email.com --non-interactive```

Saving debug log to /var/log/letsencrypt/letsencrypt.log
Account registered.



sudo certbot certificates
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Cannot extract OCSP URI from /etc/letsencrypt/live/lomo.org/cert.pem

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Found the following certs:
  Certificate Name: lomo.org
    Serial Number: 7a229707f2c2a71f
    Key Type: RSA
    Domains: lomo.org lomito.org
    Expiry Date: 2028-04-22 22:06:06+00:00 (VALID: 1826 days)
    Certificate Path: /etc/letsencrypt/live/lomo.org/fullchain.pem
    Private Key Path: /etc/letsencrypt/live/lomo.org/privkey.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -




sudo certbot delete --cert-name lomo.org
Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
The following certificate(s) are selected for deletion:

  * lomo.org

Are you sure you want to delete the above certificate(s)?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: Y
Deleted all files relating to certificate lomo.org.








con esto pido uno con las opciones básicas
sudo certbot certonly --standalone -d example.org,anotherexample.org,yetanotherexample.org -m random@email.org --no-verify-ssl --server https://localhost:14000/dir --agree-tos                        



aquí le puedo pasar un CSR que haya generado yo, aunque por línae de comando se pueden especificar varias opciones

--csr CSR             Path to a Certificate Signing Request (CSR) in DER or
                        PEM format. Currently --csr only works with the
                        'certonly' subcommand. (default: None)



To non-interactively renew *all* of your
   certificates, run "certbot renew"
