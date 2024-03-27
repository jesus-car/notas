
1. Seleccionar el componente que se le quiere hacer el efecto, el bacground de este, sera el color base del borde
2. Crear un elemento ::before que sera el que le de la magia, sera un elemento con un *height: 140% y widht menor que el original* (ir probando), este elemento es el que estara rotando para dar el efecto
3. Crear un componente ::after, que sera donde ira el contenido principal. Se le aplica un background diferente al color original y un **inset** para que se acomode dentro del componente original y deje un efecto de borde

```css
.box {
  position: relative;
  width: 300px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  overflow: hidden;
  border-radius: 15px;
}

.box::before {
  content: "";
  position: absolute;
  width: 180px;
  height: 140%;
  background-color: green;
  /*background-image: conic-gradient(green 20deg, transparent 90deg) */
  box-shadow: 0 0 20px rgb(8, 8, 8);
  animation: animate 4s linear infinite;
}

.box::after {
  content: "";
  position: absolute;
  inset: 5px;
  background-color: rgb(4, 75, 97);
  border-radius: 16px;
}

@keyframes animate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

- Variante

```css
.box {
  position: relative;
  width: 300px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  overflow: hidden;
  border-radius: 15px;
} 

.box::before {
  content: "";
  position: absolute;
  width: 180%;
  height: 140%;
  background-image: conic-gradient(green 20deg, transparent 90deg);
  animation: animate 4s linear infinite;
}

.box::after {
  content: "";
  position: absolute;
  inset: 5px;
  background-color: rgb(4, 75, 97);
  border-radius: 16px;
}

  

@keyframes animate {
  0% {
    transform: rotate(360deg);
  }
  100% {
    transform: rotate(0deg);
  }
}
```