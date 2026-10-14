# WOW.... So Meta

Challenge link: https://ctflearn.com/problems/348

## Solution
We download the image and save it as flag.jpg

Now there are two easy ways to solve the challenge:

1. Searching through the image binary with `strings`
   ```bash
   $ strings flag.jpg | grep flag{

    <rdf:Description xmlns:MicrosoftPhoto="http://ns.microsoft.com/photo/1.0/"><MicrosoftPhoto:CameraSerialNumber>flag{EEe_x_I_FFf}</MicrosoftPhoto:CameraSerialNumber></rdf:Description></rdf:RDF>
   ```
   which reveals the flag inside of the `<MicrosoftPhoto:CameraSerialNumber>`-Tag

2. (Intended way) As the image title suggests we check the metadata of the image with `exiftool`:
   ```bash
    $ exiftool flag.jpg

    [...]
    Warning                         : [minor] Fixed incorrect URI for  xmlns:MicrosoftPhoto
    Camera Serial Number            : flag{EEe_x_I_FFf}
    Image Width                     : 800

    [...]
   ```

   flag: flag{EEe_x_I_FFf}
   