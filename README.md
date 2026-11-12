# Cupos de diésel Naturisa

Pantalla web para repartir el cupo semanal de combustible: cuántos galones por semana le tocan a cada sucursal
en cada uso (bombeo, aireación, vehículos y equipos menores, maquinaria, proyectos y gasolina) y en qué tanque
de Data Maestra los recibe.

## Secciones

- **Cupos por uso** — matriz sucursal × uso con el cupo semanal en galones enteros, editable como en Excel
  (Enter baja a la siguiente sucursal). En cada celda se elige el tanque que recibe ese cupo; cada tanque
  marcado recibe la cantidad completa, no se reparte. Laboratorios y el grupo Otros llevan un solo cupo total.
- **Tanques** — el mismo reparto visto por tanque, agrupado por campamento. La fila del campamento suma los
  cupos asignados a sus tanques sin duplicar cuando un cupo está en varios.
- **Data Maestra › Tanques** — la tabla de tanques tal como está en Data Maestra (QA), con uso, combustible y
  "recibe" editables. Las correcciones son locales: no tocan QA.
- **Data Maestra › Campamentos** — en qué tanques recibe cada campamento el diésel y la gasolina. Por defecto
  los suyos; se pueden agregar los de otro campamento (Josefina recibe en los de Naturisa, Larviquest 4 en los
  del 3, Acualit 2 en los de Fincacua). Laboratorios y Otros no reciben gasolina.
- **Respaldos** — copia automática de los cupos cada vez que cambia algo (hasta 30 versiones). Se restaura
  cualquiera con un clic, o pegando el JSON de un respaldo.

Se puede importar el Excel de presupuesto (hoja Diésel) o una matriz descargada de aquí, y descargar todo en Excel.

## Uso

Requiere Python 3. Doble clic en `cupos-diesel/iniciar.bat` (abre http://localhost:3013).
`comun/server.py` hace de proxy local al gateway de Naturisa y al worker de D1.
La tabla de tanques viene de Data Maestra en QA, así que esa parte pide usuario y contraseña de AP1.

## Dónde se guarda

Todo lo que se edita vive en el `localStorage` del navegador de quien usa la pantalla: los cupos, los tanques
elegidos, las correcciones de Data Maestra y la configuración de campamentos. Nada de eso se escribe en QA ni
en producción.
