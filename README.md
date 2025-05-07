# proyecto-conecta4
import sys 
print("Bienvenidos a este espacio divertido donde podras jugar Conecta4 con tus amigos")
#Primero: se muestra el mensaje de bienvenida 

jugador_1=input("Por favor ingresar el nombre del jugador 1: ")
#Segundo: le pide el nombre a cada jugador. En la primera entrega se debe terminar el programa cuando haya un error, pero en un futuro cuando se termine el programa, puede que se deban pedir varias veces para poder continuar. por lo que decidi utilizar bucles en vez de ifs anidados.
# cuando utilizamos los bucles es que se puede seguir utilizando el programa hasta que se cumpla la condicion y siga el orden normal hasta terminar el juego. 
while not jugador_1:
    print("Error. Debes ingresar un nombre")
    exit()
    jugador_1=input("Por favor ingresar el nombre del jugador 1: ")#esto se mostrara cuando ya no empleemos el exit() y pide otra vez el nombre hasta que salga del ciclo y continue su flujo normal 
    
jugador_2=input("Por favor ingresar el nombre del jugador 2: ")
while not jugador_2:
    print("Error. Debes ingresar un nombre")
    exit()
    jugador_2=input("Por favor ingresar el nombre del jugador 2: ")
#Tercero: pido las filas y columnas teniendo en cuenta las condiciones y utilizando de nuevo los ciclos.
filas=int(input("Por favor ingresar el numero de filas para el tablero (minimo 4): ")) 
while filas<3:
    print("Error. El número de filas debe ser mayor que 3")
    exit()
    filas=int(input("Por favor ingresar el número de filas para el tablero (minimo 4): "))
columnas=int(input("Por favor ingresar el número de columnas para el tablero (minimo 4): "))
while columnas<3:
    print("Error. El número de columnas debe ser mayor que 3")
    exit()
    columnas=int(input("Por favor ingresar el número de columnas para el tablero (minimo 4): "))
#Cuarto: aqui empece a formar lo que seria el tablero según las especificaciones del usuario

tablero = [] # es una lista que contendra otras listas, cada una de ellas representando una fila con su "." representando la casilla vacia
for i in range(filas):
    fila = []
    for j in range(columnas):
        fila.append(".")
    tablero.append(fila)

# Función para mostrar el tablero
print("\n   ", end="") #los end= sirven para que los separadores de la casilla se impriman en la misma linea
for col in range(columnas): #esto es para imprimir los numeros de las columnas 
    print(f" {col+1:3}", end="")
print()
print("   +" + "---+" * columnas)
for fila in tablero:  
    print("   |", end="")
    for celda in fila:
        print(f" {celda} |", end="")
    print()
    print("   +" + "---+" * columnas)

# Jugada del jugador 1
print(f"\nTurno de {jugador_1} (X)")
col = int(input("Elige una columna: ")) - 1

# Buscar la última fila disponible en esa columna
for f in range(filas-1, -1, -1): #revisa las filas de abajo hacia arriba 
    if tablero[f][col] == ".":
        tablero[f][col] = "X"
        break #detiene el ciclo antes de que se acabe

# Mostrar el tablero de nuevo con la juagada del jugador 1
print("\n   ", end="")
for c in range(columnas):
    print(f" {c+1:3}", end="")
print()
print("   +" + "---+" * columnas)
for fila in tablero:
    print("   |", end="")
    for celda in fila:  #muestra el tablero con la primera jugada 
        print(f" {celda} |", end="")
    print()
    print("   +" + "---+" * columnas)

# Jugada del jugador 2
print(f"\nTurno de {jugador_2} (O)")
col = int(input("Elige una columna: ")) - 1 # esto es porque las listas comienzan desde 0, entonces como el usuario elige desde 1 entonces para que se ubique en la columna que es dentro de la lista

for f in range(filas-1, -1, -1):
    if tablero[f][col] == ".":
        tablero[f][col] = "O"
        break

# Mostrar el tablero final
print("\n   ", end="")
for c in range(columnas):
    print(f" {c+1:3}", end="")
print()
print("   +" + "---+" * columnas)
for fila in tablero:
    print("   |", end="")
    for celda in fila:
        print(f" {celda} |", end="")
    print()
    print("   +" + "---+" * columnas)
