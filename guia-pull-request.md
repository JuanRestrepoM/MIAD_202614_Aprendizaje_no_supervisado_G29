# Guía de contribución: cómo hacer un Pull Request

Flujo de trabajo para contribuir al repositorio sin pisar el trabajo de los demás.

> **Todos los comandos de esta guía se ejecutan desde PowerShell** (Windows). Para abrirlo: clic derecho en la carpeta del proyecto → *Abrir en Terminal*, o buscá "PowerShell" en el menú de inicio.
>
> Verificá que Git esté instalado ejecutando `git --version`. Si no aparece nada, descargalo desde [git-scm.com](https://git-scm.com/download/win).
>
> **Sobre los comandos:** las palabras EN MAYÚSCULAS son marcadores de posición — reemplazalas por tus datos reales. Por ejemplo, `git checkout -b NOMBRE-DE-TU-RAMA` se convierte en `git checkout -b feature-mi-tarea`. No uses los símbolos `< >`: en PowerShell el `<` está reservado como operador y el comando falla con el error *"The '<' operator is reserved for future use"*.

---

## Paso 1. Clonar el repositorio (solo la primera vez)

Si es la primera vez que vas a trabajar en el proyecto desde tu computadora, descargá una copia oficial desde GitHub.

Abrí **PowerShell**, andá a la carpeta donde guardás tus proyectos y clonalo:

```powershell
git clone URL-DEL-REPOSITORIO
cd NOMBRE-DE-LA-CARPETA
```

> Si ya tenés la carpeta en tu computadora de trabajos anteriores, saltá este paso y simplemente abrí PowerShell ubicado dentro de esa carpeta.

---

## Paso 2. Actualizar la rama principal (`main`)

Antes de hacer cualquier modificación, asegurate de tener la versión más reciente que está en GitHub.

```powershell
git checkout main
git pull origin main
```

Este paso evita conflictos: si trabajás sobre una versión desactualizada, después vas a tener que resolverlos a mano.

---

## Paso 3. Crear una nueva rama de trabajo

**Nunca trabajes directamente sobre `main`.** Creá una rama limpia y exclusiva para tu tarea, taller o funcionalidad:

```powershell
git checkout -b NOMBRE-DE-TU-RAMA
```

Ejemplo:

```powershell
git checkout -b feature-mi-tarea
```

---

## Paso 4. Guardar y subir tus cambios

Organizá tus archivos o carpetas y luego ejecutá:

**1. Añadir los archivos modificados o nuevos**

```powershell
git add .
```

**2. Confirmar con un mensaje descriptivo**

```powershell
git commit -m "Descripción clara de los cambios realizados"
```

**3. Subir tu rama a GitHub**

```powershell
git push -u origin NOMBRE-DE-TU-RAMA
```

El `-u` solo hace falta la primera vez que subís esa rama. Después basta con `git push`.

---

## Paso 5. Crear el Pull Request en GitHub

1. Entrá a [GitHub.com](https://github.com) y andá al repositorio.
2. Vas a ver un aviso destacado que dice **"Compare & pull request"** vinculado a la rama que acabás de subir. Hacé clic ahí.
3. Escribí un título y una descripción detallando tus aportes.
4. Hacé clic en el botón verde **Create pull request**.

Listo — tu trabajo queda formalmente enviado para revisión o integración.

---

## Resumen de comandos

```powershell
# Primera vez
git clone URL-DEL-REPOSITORIO
cd NOMBRE-DE-LA-CARPETA

# Cada vez que empezás algo nuevo
git checkout main
git pull origin main
git checkout -b NOMBRE-DE-TU-RAMA

# Cuando terminás
git add .
git commit -m "Descripción de los cambios"
git push -u origin NOMBRE-DE-TU-RAMA

# Luego: crear el PR desde GitHub.com
```

---

## Notas útiles

**Revisá qué vas a subir antes de commitear.** `git status` te muestra qué archivos cambiaron y cuáles se van a incluir. Evita subir archivos por accidente.

**Nombres de rama.** Usá algo descriptivo y sin espacios: `feature-analisis-svd`, `fix-grafico-varianza`, `taller-2-eigenfaces`.

**Si el push te rechaza** porque alguien más subió cambios mientras trabajabas:

```powershell
git pull --rebase origin main
git push
```

**Si trabajás con notebooks (.ipynb)**, considerá limpiar los outputs antes de commitear — reducen mucho el tamaño del archivo y evitan conflictos innecesarios:

```powershell
jupyter nbconvert --clear-output --inplace mi_notebook.ipynb
```

**No subas datos pesados.** Agregá un `.gitignore` en la raíz del repo con lo que no debe versionarse:

```
data/
__pycache__/
.ipynb_checkpoints/
*.csv
```