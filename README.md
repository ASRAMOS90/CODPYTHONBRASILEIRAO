# CODPYTHONBRASILEIRAO
CODIGO CRIADO EM PYTHON PARA CALCULAR PONTUAÇÃO DE CADA TIME NO CAMPEONATO BRASILEIRO, E TRAZENDO UMA TABELA ONDE OS 4 ULTIMOS TIMES INCLUIDOS NA ZONA DE REBAIXAMENTO

def atualizar_pontuacao(jogo, pontuacoes):
    time1, gols1, time2, gols2 = jogo
    
    # Se o time 1 ganhar
    if gols1 > gols2:
        pontuacoes[time1] += 3  # Time 1 ganha 3 pontos
    elif gols1 < gols2:
        pontuacoes[time2] += 3  # Time 2 ganha 3 pontos
    else:
        pontuacoes[time1] += 1  # Empate, ambos ganham 1 ponto
        pontuacoes[time2] += 1

def exibir_classificacao(pontuacoes):
    print("\nClassificação Final:")
    
    # Ordenando os times pela pontuação (decrescente)
    sorted_times = sorted(pontuacoes.items(), key=lambda item: item[1], reverse=True)
    
    # Exibindo a classificação
    for i, (time, pontos) in enumerate(sorted_times, 1):
        if i <= len(sorted_times) - 4:
            print(f"{i}. {time} - {pontos} pontos")
        else:
            print(f"{i}. {time} - {pontos} pontos (Zona de Rebaixamento)")

def main():
    # Dicionário para armazenar a pontuação dos times
    pontuacoes = {}

    # Definir alguns times
    times = ["Flamengo", "Palmeiras", "São Paulo", "Corinthians", "Grêmio", "Atlético-MG", "Internacional", "Vasco", "Botafogo", "Cruzeiro"]

    # Inicializar os times no dicionário com 0 pontos
    for time in times:
        pontuacoes[time] = 0

    # Exemplo de jogos (time1, gols1, time2, gols2)
    jogos = [
        ("Flamengo", 2, "Palmeiras", 1),   # Flamengo vence
        ("São Paulo", 1, "Corinthians", 1), # Empate
        ("Grêmio", 3, "Atlético-MG", 1),    # Grêmio vence
        ("Internacional", 2, "Flamengo", 2),# Empate
        ("Palmeiras", 0, "Grêmio", 1),      # Grêmio vence
        ("São Paulo", 3, "Internacional", 0), # São Paulo vence
        ("Vasco", 1, "Botafogo", 1),       # Empate
        ("Cruzeiro", 2, "Vasco", 3)        # Vasco vence
    ]

    # Atualizando a pontuação dos times com base nos jogos
    for jogo in jogos:
        atualizar_pontuacao(jogo, pontuacoes)

    # Exibindo a classificação final
    exibir_classificacao(pontuacoes)

if __name__ == "__main__":
    main()

Classificação Final:
1. Grêmio - 9 pontos
2. São Paulo - 7 pontos
3. Flamengo - 5 pontos
4. Palmeiras - 4 pontos
5. Internacional - 2 pontos
6. Cruzeiro - 3 pontos
7. Vasco - 4 pontos (Zona de Rebaixamento)
8. Botafogo - 2 pontos (Zona de Rebaixamento)
9. Atlético-MG - 1 ponto (Zona de Rebaixamento)
10. Corinthians - 1 ponto (Zona de Rebaixamento)
