#Bento Maximo De Farias RA:1988175
#Pedro Brene De Oliveira RA:2000033
#Fernando cardamoni RA: 1960266


from collections import deque
# fernando
class Jogador:
    def __init__(self, nome, posicao):
        self.nome = nome
        self.posicao = posicao
        self.pontos = 0
        self.assistencias = 0
        self.rebotes = 0

    def __str__(self):
        return f"{self.nome} ({self.posicao}) - Pts: {self.pontos}, Ast: {self.assistencias}, Reb: {self.rebotes}"

class Equipe:
    def __init__(self, nome):
        self.nome = nome
        self.jogadores = []
        self.historico = deque(maxlen=10)

    def adicionar_jogador(self, jogador):
        self.jogadores.append(jogador)
        print(f"Jogador {jogador.nome} adicionado à equipe {self.nome}.")

    def listar_jogadores(self):
        if not self.jogadores:
            print(f"Nenhum jogador na equipe {self.nome}.")
            return
        print(f"Jogadores da equipe {self.nome}:")
        for j in self.jogadores:
            print(f" - {j}")

    def adicionar_partida(self, resultado):
        self.historico.append(resultado)

    def mostrar_historico(self):
        if not self.historico:
            print(f"Sem histórico para a equipe {self.nome}.")
            return
        print(f"Últimas partidas da equipe {self.nome}:")
        for r in self.historico:
            print(f" - {r}")

class Campeonato:
    def __init__(self, nome):
        self.nome = nome
        self.equipes = {}
        self.partidas = []

    def adicionar_equipe(self, nome):
        if nome in self.equipes:
            print(f"Equipe {nome} já existe.")
            return
        self.equipes[nome] = Equipe(nome)
        print(f"Equipe {nome} adicionada.")

    def adicionar_jogador(self, nome_equipe, nome_jogador, posicao):
        equipe = self.equipes.get(nome_equipe)
        if not equipe:
            print(f"Equipe {nome_equipe} não encontrada.")
            return
        jogador = Jogador(nome_jogador, posicao)
        equipe.adicionar_jogador(jogador)

    def registrar_partida(self, eq1, eq2, pontos_eq1, pontos_eq2):
        e1 = self.equipes.get(eq1)
        e2 = self.equipes.get(eq2)
        if not e1 or not e2:
            print("Uma das equipes não existe.")
            return
#pedro
        self.partidas.append((eq1, pontos_eq1, pontos_eq2, eq2))

        def resultado(pontos_a, pontos_b, adversario):
            if pontos_a > pontos_b:
                return f"Venceu {pontos_a} x {pontos_b} contra {adversario}"
            elif pontos_a < pontos_b:
                return f"Perdeu {pontos_a} x {pontos_b} contra {adversario}"
            else:
                return f"Empatou {pontos_a} x {pontos_b} contra {adversario}"

        e1.adicionar_partida(resultado(pontos_eq1, pontos_eq2, eq2))
        e2.adicionar_partida(resultado(pontos_eq2, pontos_eq1, eq1))

        print(f"Partida registrada: {eq1} {pontos_eq1} x {pontos_eq2} {eq2}")

    def mostrar_resultados(self):
        if not self.partidas:
            print("Nenhuma partida registrada.")
            return
        print("Resultados:")
        for eq1, p1, p2, eq2 in self.partidas:
            print(f"{eq1} {p1} x {p2} {eq2}")

    def mostrar_info_equipe(self, nome_equipe):
        equipe = self.equipes.get(nome_equipe)
        if not equipe:
            print("Equipe não encontrada.")
            return
        equipe.listar_jogadores()
        equipe.mostrar_historico()
#bento
def menu():
    campe = Campeonato("Campeonato de Basquete")

    while True:
        print("\n Menu do Campeonato ")
        print("1 - Adicionar Equipe")
        print("2 - Adicionar Jogador")
        print("3 - Registrar Partida")
        print("4 - Mostrar Resultados")
        print("5 - Mostrar Info da Equipe")
        print("6 - Sair")

        op = input("Opção: ").strip()

        if op == '1':
            nome = input("Nome da equipe: ").strip()
            campe.adicionar_equipe(nome)

        elif op == '2':
            equipe = input("Equipe: ").strip()
            nome_jog = input("Nome do jogador: ").strip()
            pos = input("Posição: ").strip()
            campe.adicionar_jogador(equipe, nome_jog, pos)

        elif op == '3':
            eq1 = input("Equipe 1: ").strip()
            eq2 = input("Equipe 2: ").strip()
            try:
                g1 = int(input(f"Pontos {eq1}: "))
                g2 = int(input(f"Pontos {eq2}: "))
            except ValueError:
                print("Pontos inválidos.")
                continue
            campe.registrar_partida(eq1, eq2, g1, g2)

        elif op == '4':
            campe.mostrar_resultados()

        elif op == '5':
            nome = input("Nome da equipe: ").strip()
            campe.mostrar_info_equipe(nome)

        elif op == '6':
            print("Saindo...")
            break

        else:
            print("Opção inválida.")

if __name__ == "__main__":
    menu()
