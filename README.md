# 1. Definir el personaje principal
class Jugador:
    def __init__(self, nombre):
        self.nombre = nombre
        self.salud = 100
        self.ataque = 10
        self.nivel = 1
        self.experiencia = 0
    
    def atacar(self, enemigo):
        enemigo.salud -= self.ataque

# 2. Definir enemigos
class Enemigo:
    def __init__(self, nombre, salud, ataque):
        self.nombre = nombre
        self.salud = salud
        self.ataque = ataque
    
    def atacar(self, jugador):
        jugador.salud -= self.ataque

# 3. Crear una misión
def mision(jugador):
    print("¡Comienza una nueva misión!")
    enemigo = Enemigo("Goblin", 30, 5)
    while jugador.salud > 0 and enemigo.salud > 0:
        jugador.atacar(enemigo)
        print(f"Atacas al {enemigo.nombre}, su salud es ahora {enemigo.salud}")
        if enemigo.salud <= 0:
            print(f"¡Has derrotado al {enemigo.nombre}!")
            jugador.experiencia += 10
            break
        enemigo.atacar(jugador)
        print(f"El {enemigo.nombre} te ataca, tu salud es ahora {jugador.salud}")
        if jugador.salud <= 0:
            print("Has sido derrotado...")
            break

# 4. Crear el juego principal
def iniciar_juego():
    print("Bienvenido al juego de espadas y misiones")
    nombre = input("Introduce el nombre de tu personaje: ")
    jugador = Jugador(nombre)
    
    while jugador.salud > 0:
        print("\n¿Qué deseas hacer?")
        print("1. Empezar una misión")
        print("2. Salir del juego")
        opcion = input("Elige una opción: ")
        
        if opcion == "1":
            mision(jugador)
        elif opcion == "2":
            print("Gracias por jugar.")
            break
        else:
            print("Opción no válida")

# Ejecutar el juego
iniciar_juego()
