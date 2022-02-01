# Gerar certificado Sicredi
`openssl genrsa -des3 -out SICREDI_DIGITALNET.key 2048`

`openssl req -new -key SICREDI_DIGITALNET.key -out SICREDI_DIGITALNET.csr`

![image](https://user-images.githubusercontent.com/6507492/151967222-8b994b24-605a-4fc9-9051-52e02023f965.png)



# Gerar certificado Itaú
`openssl genpkey -out private.pem -algorithm RSA -pkeyopt rsa_keygen_bits:2048`

`openssl rsa -in private.pem -pubout -out public.pem`


# Certificate to PFX
`openssl pkcs12 -export -out CERT.pfx -inkey CERT.key -in CERT.cer`

# Converter certificado Sicredi
`openssl x509 -inform der -in SICREDI_OPCAO_LANG.cer -out SICREDI_OPCAO_LANG.1.cer`

# Export PFX to Base64
`$fileContentBytes = get-content .\CERT.pfx -Encoding Byte`

`[System.Convert]::ToBase64String($fileContentBytes) | Out-File 'CERT_B64.txt'`

# Gerar certificado Itaú
`openssl req -new -subj "/CN=2979ceb7-4f4b-4822-abe5-2b29ead35687/OU=7AZ.COM.BR/L=ESPERA FELIZ/ST=MG/C=BR" -out ITAU_UNIVERSO.csr -nodes -sha512 -newkey rsa:2048 -keyout ITAU_UNIVERSO.key`
