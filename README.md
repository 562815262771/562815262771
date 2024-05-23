xml'yi içe aktar etree . ET olarak ElementTree  
içe aktarma  istekleri

url  =  "https://tckimlik.nvi.gov.tr/Service/KPSPublic.asmx?WSDL"
başlıklar  = { "içerik türü" : "metin/xml" }

# Bunu değiştir
tc_no  =  "XXXXXXXXXXXX"
reklam  =  "NAME"
soyad  =  "SOYADI"
dogum_yili  =  1995

gövde  =  f"""<?xml version='1.0' encoding='utf-8'?>
<soap:Envelope xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd = "http://www.w3.org/2001/XMLSchema" xmlns:soap = "http ://schemas.xmlsoap.org/soap/envelope/">
  <sabun:Gövde>
    <TCKimlikNoDogrula xmlns="http://tckimlik.nvi.gov.tr/WS">
      <TCKimlikNo> { tc_no } </TCKimlikNo>
      <Reklam> { reklam } </Reklam>
      <Soyad> { soyad } </Soyad>
      <DogumYili> { dogum_yili } </DogumYili>
    </TCKimlikNoDogrula>
  </soap:Gövde>
</soap:Envelope>"""

r  =  istekler . gönderi ( url , veri = gövde , başlıklar = başlıklar )

kök  =  ET . fromstring ( r . metin )

eğer  kök . find ( ".//soap:Fault" , ad alanları = { "soap" : "http://schemas.xmlsoap.org/soap/envelope/" }):
    arıza_element  =  kök . bul ( ".//faultstring" )
    error_message  =  arıza_elemanı . metin
    print ( "Hata:" , error_message )
başka :
    sonuç_element  =  kök . find ( ".//{http://tckimlik.nvi.gov.tr/WS}TCKimlikNoDogrulaResult" )
    sonuç  =  sonuç_elemanı . metin
    yazdır ( sonuç )- 

<!---
562815262771/562815262771 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
