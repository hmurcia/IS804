### Ejercicio Práctico de Enrutamiento Estático en Packet Tracer

#### Situación Actual

Una pequeña empresa, "Tecnologías Avanzadas", tiene dos sucursales que necesitan comunicarse entre sí. La sede central (Sucursal A) y la sucursal remota (Sucursal B) están en redes diferentes. La sede central tiene la red 192.168.1.0/24, y la sucursal remota tiene la red 192.168.2.0/24. Ambas sucursales están conectadas a través de un router en el centro de datos.

#### Problema

Los empleados de la sucursal A necesitan acceder a recursos compartidos en la sucursal B, pero actualmente no pueden comunicarse. Los routers en cada sucursal no tienen rutas configuradas que permitan la comunicación entre las dos redes.

#### Objetivo del Ejercicio

Configurar el enrutamiento estático en ambos routers para permitir la comunicación entre las dos sucursales, asegurando que los dispositivos en la red 192.168.1.0/24 puedan comunicarse con los dispositivos en la red 192.168.2.0/24 y viceversa.

#### Condiciones a Cumplir

1. **Direcciones IP**:
   - **Sucursal A**:
     - Router A: 192.168.1.1
     - Dispositivo 1 (PC): 192.168.1.10
   - **Sucursal B**:
     - Router B: 192.168.2.1
     - Dispositivo 2 (PC): 192.168.2.10
   - **Router Central**:
     - Interfaz hacia Router A: 10.0.0.1
     - Interfaz hacia Router B: 10.0.0.2

2. **Configuración Inicial**:
   - Asegúrate de que todos los dispositivos estén conectados y que las interfaces de los routers tengan configuradas sus direcciones IP adecuadas.

3. **Requerimientos**:
   - Configura rutas estáticas en ambos routers para que:
     - Los paquetes de la red 192.168.1.0/24 se envíen a la red 192.168.2.0/24 a través del router central.
     - Los paquetes de la red 192.168.2.0/24 se envíen a la red 192.168.1.0/24 a través del router central.

#### Pasos a Seguir

1. **Configurar Router A**:
   - Accede a Router A y agrega una ruta estática que envíe el tráfico hacia la red 192.168.2.0/24 a través de la interfaz del router central.

   ```bash
   enable
   configure terminal
   ip route 192.168.2.0 255.255.255.0 10.0.0.1
   ```

2. **Configurar Router B**:
   - Accede a Router B y agrega una ruta estática que envíe el tráfico hacia la red 192.168.1.0/24 a través de la interfaz del router central.

   ```bash
   enable
   configure terminal
   ip route 192.168.1.0 255.255.255.0 10.0.0.2
   ```

3. **Verificar la Conectividad**:
   - Desde el PC en la Sucursal A, utiliza el comando `ping 192.168.2.10` para comprobar la conectividad con el PC en la Sucursal B.
   - Desde el PC en la Sucursal B, utiliza el comando `ping 192.168.1.10` para comprobar la conectividad con el PC en la Sucursal A.

4. **Documentar Resultados**:
   - Anota los resultados de los pings y cualquier error que encuentres. Si no puedes hacer ping a la otra sucursal, revisa la configuración de las rutas y asegúrate de que todos los dispositivos estén configurados correctamente.
