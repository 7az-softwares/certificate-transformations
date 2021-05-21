# Certificate to PFX
`openssl pkcs12 -export -out CERT.pfx -inkey CERT.key -in CERT.cer`

# Export PFX to Base64
`$fileContentBytes = get-content .\CERT.pfx -Encoding Byte`
`[System.Convert]::ToBase64String($fileContentBytes) | Out-File 'CERT_B64.txt'`
