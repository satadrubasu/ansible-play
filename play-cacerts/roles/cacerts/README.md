https://computingforgeeks.com/generate-openssl-self-signed-certificates-with-ansible/

openssl x509 -in certificates/{hostdomain}_cert.pem -text

=== Steps===
1. Create CA cert
2. Create server Cert signing request
3. Sign the server request using CA cert


openssl req -x509 -newkey rsa:4096 -days 1000 -keyout ca-key.pem -out ca-cert.pem -nodes -subj "/C=US/ST=Denial/L=Springfield/O=Dis/CN=jenkinslab"
openssl x509 -in ca-cert.pem -noout -text


openssl req -nodes -newkey rsa:4096 -keyout server-key.pem -out server-req.csr -subj "/C=US/ST=ATL/L=Labs/O=Dis/CN=localhost"

openssl x509 -req -in server-req.csr -CA ca-cert.pem -CAkey ca-key.pem -CAcreateserial -out server-signed-cert.pem
openssl x509 -in server-signed-cert.pem -noout -text