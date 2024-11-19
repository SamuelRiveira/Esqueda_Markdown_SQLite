# SQLite
## ¿Qué es SQLite?
- Base de datos relacional integrada.
- Almacena datos localmente en dispositivos.
- Ligera, sin necesidad de servidor.

## Principales características
- **Self-contained:** Todo está contenido en una única librería.
- **Zero-configuration:** No requiere configuración o instalación.
- **Transactional:** Soporta ACID.
- **Ligera:** Ideal para aplicaciones móviles.

## Estructura básica
1. **Tablas:** Colección de datos organizados en filas y columnas.
2. **Registros:** Cada fila en una tabla.
3. **Consultas:** Comandos SQL para manipular datos.

## Operaciones CRUD
1. **Create:** Crear tablas.
2. **Read:** Consultar datos.
3. **Update:** Actualizar registros.
4. **Delete:** Eliminar registros.

## Uso en Android
### Paso 1: Crear una clase de base de datos
```kotlin
class MyDatabaseHelper(context: Context) : SQLiteOpenHelper(context, "MyDatabase", null, 1) {
    override fun onCreate(db: SQLiteDatabase) {
        db.execSQL("CREATE TABLE Users (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)")
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        db.execSQL("DROP TABLE IF EXISTS Users")
        onCreate(db)
    }
}
```
### Paso 2: Insertar datos
```kotlin
val db = MyDatabaseHelper(context).writableDatabase
val values = ContentValues().apply {
    put("name", "John")
    put("age", 25)
}
db.insert("Users", null, values)
```
### Paso 3: Consultar datos
```kotlin
val cursor = db.query("Users", null, null, null, null, null, null)
while (cursor.moveToNext()) {
    val name = cursor.getString(cursor.getColumnIndexOrThrow("name"))
    val age = cursor.getInt(cursor.getColumnIndexOrThrow("age"))
}
cursor.close()
```
### Paso 4: Actualizar datos
```kotlin
val values = ContentValues().apply {
    put("age", 26)
}
db.update("Users", values, "name = ?", arrayOf("John"))
```
### Paso 5: Eliminar datos
```kotlin
db.delete("Users", "name = ?", arrayOf("John"))
```
