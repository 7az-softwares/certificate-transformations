# Certificate to PFX
`openssl pkcs12 -export -out CERT.pfx -inkey CERT.key -in CERT.cer`

# Converter certificado Sicredi
`openssl x509 -inform der -in SICREDI_OPCAO_LANG.cer -out SICREDI_OPCAO_LANG.1.cer`

# Export PFX to Base64
`$fileContentBytes = get-content .\CERT.pfx -Encoding Byte`

`[System.Convert]::ToBase64String($fileContentBytes) | Out-File 'CERT_B64.txt'`

# Gerar certificado Itaú
`openssl req -new -subj "/CN=2979ceb7-4f4b-4822-abe5-2b29ead35687/OU=7AZ.COM.BR/L=ESPERA FELIZ/ST=MG/C=BR" -out ITAU_UNIVERSO.csr -nodes -sha512 -newkey rsa:2048 -keyout ITAU_UNIVERSO.key`
