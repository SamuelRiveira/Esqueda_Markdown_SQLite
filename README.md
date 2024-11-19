# SQLite

## 1. Crear una clase para la base de datos
- Extender `SQLiteOpenHelper`
- Sobrescribir `onCreate` para crear tablas
- Sobrescribir `onUpgrade` para manejar cambios de versión

## 2. Operaciones CRUD
- **Insertar:** `db.insert(tabla, null, ContentValues)`
- **Leer:** `db.rawQuery("SELECT ...")` o `db.query()`
- **Actualizar:** `db.update(tabla, ContentValues, condiciones)`
- **Eliminar:** `db.delete(tabla, condiciones)`

## 3. Uso de la base de datos
- Crear una instancia de la clase
- Llamar a los métodos CRUD según sea necesario
- Cerrar el cursor y la base de datos cuando terminen
