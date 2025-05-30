#Bento Maximo De Farias RA:1988175
#Pedro Brene De Oliveira RA:2000033
#Fernando cardamoni RA: 1960266

Documentação do Sistema de Campeonato de Basquete
Introdução
Este sistema foi desenvolvido para gerenciar um campeonato de basquete, permitindo a criação de equipes, adição de jogadores, registro de partidas, exibição de resultados e histórico de jogos. O código está estruturado em três classes principais e uma função de interface de menu para interação com o usuário.

Estrutura Geral do Código
O código é dividido em três blocos principais:

Classes de domínio: Representam jogadores, equipes e o campeonato.

Estrutura de dados: Funções internas das classes para adicionar jogadores, registrar partidas e mostrar informações.

Interface interativa: Permite a interação do usuário com o sistema via terminal.


Classe Campeonato 

Objetivo: Gerenciar o campeonato, contendo as equipes participantes e as partidas disputadas.

Atributos:

nome (str): nome do campeonato.

equipes (dict): dicionário que mapeia nomes de equipes para seus objetos Equipe.

partidas (list): lista que armazena as partidas disputadas, com nomes das equipes e placares.




Métodos da classe Campeonato:

adicionar_equipe(self, nome):

Cria uma nova equipe e adiciona ao campeonato.

Verifica se a equipe já existe antes de adicionar.

Exibe mensagem confirmando a adição ou indicando que já existe.

adicionar_jogador(self, nome_equipe, nome_jogador, posicao):

Localiza a equipe pelo nome.

Cria um novo jogador e adiciona na equipe correspondente.

Caso equipe não exista, exibe mensagem de erro.

registrar_partida(self, eq1, eq2, pontos_eq1, pontos_eq2):

Recebe os nomes das duas equipes e seus respectivos pontos.

Verifica se ambas as equipes existem.

Registra a partida na lista partidas.

Cria uma descrição do resultado para cada equipe (vitória, derrota ou empate).

Adiciona o resultado no histórico de cada equipe.

Exibe confirmação do registro da partida.

mostrar_resultados(self):

Exibe todas as partidas registradas no campeonato.

Caso não tenha nenhuma partida, informa que não há resultados.

mostrar_info_equipe(self, nome_equipe):

Exibe as informações detalhadas da equipe (jogadores e histórico de partidas).

Caso equipe não exista, informa que não foi encontrada.





Função menu

Objetivo: Fornecer uma interface de linha de comando para o usuário interagir com o sistema.

Fluxo:

Instancia um objeto Campeonato.

Exibe um menu com opções numeradas:

1: Adicionar equipe.

2: Adicionar jogador.

3: Registrar partida.

4: Mostrar resultados.

5: Mostrar informações da equipe.

6: Sair do programa.

Recebe a opção do usuário via input.

Executa a ação correspondente chamando os métodos da classe Campeonato.

Permite repetição contínua até o usuário optar por sair.

Validação:

Verifica entradas inválidas para pontos nas partidas.

Informa erros para equipes não encontradas ou nomes já existentes.





Como Executar o Programa 

Exemplos de Uso
Adicionar uma equipe:

Usuário escolhe opção 1.

Insere o nome da equipe, por exemplo, "São Paulo".

O sistema confirma a criação da equipe.

Adicionar jogadores à equipe:

Escolhe opção 2.

Insere o nome da equipe criada.

Insere nome e posição do jogador, ex: "Carlos", "Armador".

O sistema confirma o jogador adicionado.

Registrar uma partida:

Escolhe opção 3.

Insere os nomes das duas equipes e seus pontos.

O sistema registra o resultado e atualiza o histórico de ambas.

Mostrar resultados:

Escolhe opção 4 para ver a lista de partidas já disputadas.

Mostrar informações da equipe:

Escolhe opção 5.

Insere o nome da equipe para visualizar seus jogadores e últimos jogos.





