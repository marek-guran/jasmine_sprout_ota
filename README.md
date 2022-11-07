# jasmine_sprout_ota

You need:
 <br>- Working LineageOS built from source
 <br>- File hosting with direct links, for exaple AndroidFileHost
 <br>- GitHub account

1) create public GitHub repository and create in it JSON file with following text:
```
{
  "response": [
    {
      "datetime": 1234567890,
      "filename": "ota-package.zip",
      "id": "5eb63bbbe01eeed093cb22bb8f5acdc3",
      "romtype": "unofficial",
      "size": 314572800,
      "url": "https://example.com/ota-package.zip",
      "version": "18.1"
    }
  ]
}
```
"datetime" - build date in UNIX timestamp, see out/build_date.txt[/i
 <br>"filename" - name of your OTA package
 <br>"id" - update identificator, simply use password generator
 <br>"romtype" - your build type (unofficial)
 <br>"size" - OTA package size in bytes
 <br>"url" - direct link to package
 <br>"version" - ROM version

2) Go to packages/apps/Updater/res/values and open file strings.xml and find URL define (updater_server_url):
```
<string name="updater_server_url" translatable="false">https://download.lineageos.org/api/v1/{device}/{type}/{incr}</string>
```
And copy here Raw of created JSON file, for exapmle:
```
<string name="updater_server_url" translatable="false">https://raw.githubusercontent.com/marek-guran/jasmine_sprout_ota/main/ota.json</string>
```
3) Build package with OTA support with usual method with making installclean. Done! Now you have build with OTA support.
