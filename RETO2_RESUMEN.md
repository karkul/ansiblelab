# Automation2021 - 2do Reto (Simplificado) 

### Resumen de tareas simplificado:

1. Crear/levantar una instancia Windows (con Vagrant o de forma manual).
  > Notas: mostrar vagrantfile, configuracion del **WinRM**, como llamar al **RDP**
  
2. Habilitar la comunicacion entre los host `tower` y `whost1`

3. Crear un nuevo playbook para:
- Copiar el ejecutable del programa **Diskusage**
- Ejecutar el programa `diskusage.exe`
- Copiar el archivo de salida `diskusage_out.txt` del whost1 de vuelta a Tower
- Enviar el reporte/archivo de salida al correo `ramon.morales-lopez@t-system.com` 

4. Enviar una notificacion a Slack donde se diga que el reto ha sido completado.

### Puntos adicionales deseables.
- Hacer que todo lo anterior funcione y se ejecute desde **Ansible Tower**.
- Pasarle entradas dinámicas al playbook a través de las *Extra Variables*