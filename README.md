# space_hud


# Novedades 1.3
- **Con `lsn_llaves`:** el motor (G) y el seguro (L) pasan a ser del sistema de llaves. `lsn_hud` ya no registra esas teclas
  y su menú y CarPlay usan las llaves. Sin `lsn_llaves` todo sigue como antes.
- **Arreglado:** la G que no apagaba y la L que había que spamear. Era otro script de llaves (jaksam) usando las mismas teclas:
  los dos se ejecutaban a la vez y se anulaban. Quita `vehicles_keys` del `server.cfg`.
- Export de cliente `isRetro(vehiculo)`: lo usa `lsn_llaves` para saber si al auto se le hace puente con destornillador o con programador.

# Novedades 1.2.1
- **Arreglado:** las posiciones de `/lsnhud` › Mover elementos ya se guardan. Antes, al guardar, todo volvía a su lugar (el tamaño sí se guardaba).

# Novedades 1.2
Reemplaza las carpetas `lsn_hud` y `realengine_vehicles` (1.4.1) y reinicia. No cambia la base de datos.

- **Arreglado:** el velocímetro ya no aparece a pie. Antes salía al entrar al servidor hasta la primera vez que te bajabas de un auto.
- **Bicicletas:** sin velocímetro ni odómetro. `realengine_vehicles` tampoco les cuenta kilómetros ni desgaste. Se cambia en `Config.Vehicle.noSpeedo`.
- **Música desde afuera, realista:**
  - Con el auto **cerrado** no se escucha afuera (`Config.Radio.closedFactor`; pon `0.05` si quieres que se cuele un poco de bajo).
  - El sonido sale por cada **vidrio bajado o roto, puerta abierta, capota abierta o maletero**, desde su lugar en el auto. Al caminar alrededor suena más fuerte del lado abierto y baja con la distancia.
  - Si escuchas desde **otro auto cerrado**, te llega más apagado.
  - El volumen cambia suave, sin saltos.
  - Todo se ajusta en `Config.Radio` (`range`, `refDistance`, `open`, `listenerInClosedCar`).
- **Ítems para instalar la radio** (ox_inventory):
  - `kit_carplay`: CarPlay en un auto viejo.
  - `radio_clasica`: radio de época en un auto moderno.
  - Se usan sentado al volante con el auto detenido (12 s con barra de progreso). El kit se gasta y la radio queda **guardada por placa**: dura aunque el auto vaya al garaje o reinicies el servidor.
  - Para que solo los mecánicos puedan instalar: `Config.HeadUnit.jobs = { mechanic = 0 }`.
  - **Instalación:** pega `install/ox_inventory_items.lua` dentro de `ox_inventory/data/items.lua`, copia `install/images/*.png` a `ox_inventory/web/images/` y reinicia ox_inventory.
