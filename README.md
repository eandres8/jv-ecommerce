## Store Spring Boot 4

1. Clone reponsitory
2. copy the `.env` file, from `.env.template` and replace it keys
3. to create submodules use:
````cmd
git submodule update --init --recursive
````
4. run project
```cmd
docker compose up --build
```

### Pasos para crear los Git Submodules


1. Crear un nuevo repositorio en GitHub
2. Clonar el repositorio en la máquina local
3. Añadir el submodule, donde `repository_url` es la url del repositorio y `directory_name` es el nombre de la carpeta donde quieres que se guarde el sub-módulo (no debe de existir en el proyecto)
```
git submodule add <repository_url> <directory_name>
```
4. Añadir los cambios al repositorio (git add, git commit, git push)
Ej:
```
git add .
git commit -m "Add submodule"
git push
```
5. Inicializar y actualizar Sub-módulos, cuando alguien clona el repositorio por primera vez, debe de ejecutar el siguiente comando para inicializar y actualizar los sub-módulos
```
git submodule update --init --recursive
```
6. Para actualizar las referencias de los sub-módulos
```
git submodule update --remote
```


## Importante
Si se trabaja en el repositorio que tiene los sub-módulos, **primero actualizar y hacer push** en el sub-módulo y **después** en el repositorio principal. 

Si se hace al revés, se perderán las referencias de los sub-módulos en el repositorio principal y tendremos que resolver conflictos.


## To remove a submodule you need to:

* Delete the relevant section from the `.gitmodules` file.
* Stage the `.gitmodules` changes:
```
git add .gitmodules
```
* Delete the relevant section from `.git/config`.
* Remove the submodule files from the working tree and index:
```cmd
git rm --cached path_to_submodule (no trailing slash).
```
* Remove the submodule's `.git` directory:
````cmd
rm -rf .git/modules/path_to_submodule
````
* Commit the changes:
```cmd
git commit -m "Removed submodule <name>"
```
* Delete the now untracked submodule files:
```
rm -rf path_to_submodule
```