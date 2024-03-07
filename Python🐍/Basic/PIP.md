## PIP , Instalador de paquetes de Python

- pip es un explorador de package's de Python, donde puedo buscar e instalar los paquetes disponibles en el [PyPI · El Índice de paquetes de Python](https://pypi.org/)
- DEPENDENCIAS EN PYTHON: Cuanto uno usa un modulo externo de los que nos ofrece python, uno que lo hemos descargado gracias a pip, este modulo lo mas probable que use otros modulos. Y si alguien quiere usar mi codigo que use estos modulos, probablemente este tambien necesite los otros modulos. Esto hace dependiente al codigo que se esta escribiendo de todos los modulos antes usados. Para esto esta pip, este se encarga de tener todo controlado, una vez que dengamos pip, no nos tenemos que preocupar por dependencias.


**Comandos en consola**
- pip list: Lista todas los paquetes instalados en el sistema.
- pip show package_name : Muestra los metadatos del package_name.
- pip search Some_thing: Busca Some_thing en la base de datos de PyPI, puede devolvernos muchos datos asi que tratar de ser los mas especificos posibles.
- Tambien se puede buscar desde la pagina pypi.org
- pip install package_name : Despues de buscar y encontrar el paquete deseado, with this command I'll install in my enviromment python like root.
- pip install --user package_name : With this command I'll install like user. 
- pip install -U package_name : Actualiza a la version mas reciente el package_name
- pip install package_name\==version_package : Actualiza el package a la version seleccionada
- pip uninstall package_name : Desinstala el paquete seleccionado.
 