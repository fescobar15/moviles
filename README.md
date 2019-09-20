# Parcial ADB Móviles - Felipe Escobar Avila (201531251)

Para correr se debe modificar la variable path y ponerla para apuntar al directorio donde esta adb.exe.

El .apk va en el proyecto java.

El celular que se utilizó para las pruebas fue un Moto G5 Plus con Android Oreo.
El tamaño de la pantalla de este dispositivo es de 1080x1920.

Para ejecutar los comandos, el script utiliza siempre una ruta al directorio donde se encuentra el ejecutable "adb.exe", y estando alli se pueden ejecutar los comandos.

1. Se instala un apk. Se decidió usar el apk de facebook messenger lite:

adb install ./com.facebook.mlite.apk

2. Una vez instalada la aplicación se abre la aplicación:

adb shell monkey -p com.facebook.mlite -c android.intent.category.LAUNCHER 1

3. Se retorna al menú principal:

adb shell input keyevent 3

4. Se toma una captura de pantalla en el menu home:

adb shell screencap /sdcard/foto.png

5. Se saca la foto del celular y se guarda localmente (en el computador donde se corren los comandos):

adb pull /sdcard/foto.png ./img/foto.png

6. Se da click en la primera aplicación para abrirla:

adb shell input tap 500 500

7. Se baja el volúmen del celular:

adb shell input keyevent 25

8. Se retorna al menu home:

adb shell input keyevent 3

9. Se da click en la aplicación google chrome:

adb shell input tap 540 1670

10. Se da click en la barra de busqueda de google chrome:

adb shell input tap 500 155

11. Se escribe mi nombre:

adb shell input text 'Felipe Escobar'

12. Se inicializa el puerto:

adb tcpip 5555

13. Se encuentra la ip del celular:

adb shell "ip addr show wlan0 | grep -e wlan0$ | cut -d\" \" -f 6 | cut -d/ -f 1"

14. Se conencta al celular con su ip:

adb connect <ip>:5555
  
15. Se toma screenshot: 

adb shell screencap /sdcard/foto2.png

16. Se saca del celular y se guarda localmente:

adb pull /sdcard/foto.png ./img/foto2.png

17. Se agrega un contacto:

adb shell am start -a android.intent.action.INSERT -t vnd.android.cursor.dir/contact -e name 'Felipe Escobar' -e phone 123456789

18. Se hace back:

adb shell input keyevent 4

19. Finalmente se desinstala la app:

adb uninstall com.facebook.mlite
