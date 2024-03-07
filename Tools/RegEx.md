
- \\d : Busca un digito
	- /d{n} : busca un numero con n digitos
- \\/ : Busca una barra / , pero es necesario escaparla con \\ para que no entre en conflicto

```python
fecha = "\d{2}\/\d{2}\/d{4}"       # Encontrara fechas con el formado 14/14/1414
```

