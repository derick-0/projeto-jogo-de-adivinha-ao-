# projeto-jogo-de-adivinha-ao-

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_JOGADORES 5

struct Jogador
{
    char nome[30];
    int pontuacao;
};

void modo_de_jogo5_jogar(struct Jogador jogadores[], int *totalJogadores);
int etapa5_calcularPontuacao(int tentativas);
void etapa5_mostrarRanking(struct Jogador jogadores[], int totalJogadores);

void modo_de_jogo1()
{
    int numeroAleatorio;
    int palpite;

    srand((unsigned int)time(NULL));

    numeroAleatorio = rand() % 51 + 25;

    printf("Digite seu palpite (25 a 75): ");
    if (scanf("%d", &palpite) != 1)
    {
        printf("Entrada invalida!\n");
        return;
    }

    if (palpite == numeroAleatorio)
    {
        printf("Parabens! Voce acertou.\n");
    }
    else
    {
        printf("Voce errou! O numero correto era %d.\n", numeroAleatorio);
    }
}

void modo_de_jogo2()
{
    int numeroSecreto, palpite;
    int tentativas = 0;
    int pontuacao = 100;
    int acertou = 0;
    int dificuldade;
    int limite, penalidade;
    char continuar;

    do
    {
        printf("=== JOGO DA ADIVINHACAO ===\n");
        printf("Escolha o nivel de dificuldade:\n");
        printf("1 - nivel Facil (1 a 50)\n");
        printf("2 - nivel Medio (1 a 100)\n");
        printf("3 - nivel Dificil (1 a 200)\n");
        printf("digite sua Opcao: ");
        scanf("%d", &dificuldade);

        switch (dificuldade)
        {
        case 1:
            limite = 50;
            penalidade = 4;
            break;
        case 2:
            limite = 100;
            penalidade = 7;
            break;
        case 3:
            limite = 200;
            penalidade = 12;
            break;
        default:
            printf("Opcao invalida! Nivel medio selecionado.\n");
            limite = 100;
            penalidade = 5;
        }

        srand(time(NULL));
        numeroSecreto = rand() % limite + 1;

        tentativas = 0;
        pontuacao = 100;
        acertou = 0;

        printf("\nTente adivinhar o numero entre 1 e %d\n\n", limite);

        while (!acertou)
        {
            printf("Digite seu palpite: ");
            scanf("%d", &palpite);

            tentativas++;
            pontuacao -= penalidade;

            printf("Voce digitou: %d\n", palpite);

            if (palpite == numeroSecreto)
            {
                printf("\nParabens! Voce acertou o numero!\n");
                acertou = 1;
            }
            else if (palpite > numeroSecreto)
            {
                printf("Seu palpite e MAIOR que o numero secreto.\n\n");
            }
            else
            {
                printf("Seu palpite e MENOR que o numero secreto.\n\n");
            }

            if (pontuacao < 0)
                pontuacao = 0;
        }

        printf("\n===== RESULTADO DOS PALPITES =====\n");
        printf("Numero de tentativas: %d\n", tentativas);
        printf("Pontuacao final: %d\n", pontuacao);
        printf("======================\n");

        printf("\nDeseja jogar novamente? (S/N): ");
        scanf(" %c", &continuar);

        system("clear");
        system("cls");

    } while (continuar == 'S' || continuar == 's');

    printf("\nObrigado por jogar! Ate logo!\n");
}

void modo_de_jogo3()
{
    int numeroSecreto, palpite;
    int tentativas, pontos;
    int jogarDeNovo;

    srand(time(NULL));

    do
    {
        printf("aguarde...Gerando numero aleatorio");
        for (int i = 0; i < 3; i++)
        {
            printf(".");
            fflush(stdout);
        }
        printf("\n");

        numeroSecreto = rand() % 150 + 1;
        tentativas = 0;
        pontos = 150;
        palpite = 0;

        printf("\n=== JOGO DA ADIVINHACAO ===\n");
        printf("Tente adivinhar  o numero entre 1 e 150.\n\n");

        while (palpite != numeroSecreto)
        {
            printf("qual e o seu palpite?: ");
            scanf("%d", &palpite);

            tentativas++;

            if (palpite > numeroSecreto)
            {
                printf("boa tentativa mas esta errado! O numero e menor.\n");
                pontos -= 10;
            }
            else if (palpite < numeroSecreto)
            {
                printf("boa tentativa mas esta errado! O numero e maior.\n");
                pontos -= 10;
            }
        }

        printf("\nVoce acertou,parabens!\n");
        printf("Numero secreto: %d\n", numeroSecreto);
        printf("numeros de Tentativas: %d\n", tentativas);
        printf("sua Pontuacao: %d\n", pontos);

        printf("\nDeseja jogar novamente? (1 = sim, 0 = nao): ");
        scanf("%d", &jogarDeNovo);

    } while (jogarDeNovo == 1);

    printf("\nObrigado por jogar,ate logo!\n");
}

void modo_de_jogo4()
{
    struct Jogador jogadores[MAX_JOGADORES];
    int totalJogadores;

    printf("Quantos jogadores voce ira cadastrar na equipe (maximo %d)? ", MAX_JOGADORES);
    scanf("%d", &totalJogadores);

    if (totalJogadores > MAX_JOGADORES)
    {
        totalJogadores = MAX_JOGADORES;
    }

    srand(time(NULL));

    for (int i = 0; i < totalJogadores; i++)
    {
        printf("\nNome ou apelido  do jogador %d: ", i + 1);
        scanf(" %29[^\n]", jogadores[i].nome);

        jogadores[i].pontuacao = rand() % 101;

        printf("Pontuacao registrada para %s.\n", jogadores[i].nome);
    }

    printf("\n--- Lista dos Jogadores e suas Pontuacoes atingidas ---\n");
    for (int i = 0; i < totalJogadores; i++)
    {
        printf("%s - %d pontos\n", jogadores[i].nome, jogadores[i].pontuacao);
    }
}

void modo_de_jogo5_jogar(struct Jogador jogadores[], int *totalJogadores)
{
    int secreto = rand() % 50 + 1;
    int palpite, tentativas = 0;

    printf("\nInforme seu nome ou apelido: ");
    getchar();
    fgets(jogadores[*totalJogadores].nome, 30, stdin);

    printf("Um numero aleatorio sera gerado entre 1 e 50.\n");

    do
    {
        printf("Digite qual e o seu palpite: ");
        scanf("%d", &palpite);
        tentativas++;

        if (palpite > secreto)
        {
            printf("Muito alto,tente novamente!\n");
        }
        else if (palpite < secreto)
        {
            printf("Muito baixo,tente novamente!\n");
        }

    } while (palpite != secreto);

    printf("Parabens! Voce acertou em %d tentativas!\n", tentativas);

    jogadores[*totalJogadores].pontuacao = etapa5_calcularPontuacao(tentativas);

    printf("Pontuacao obtida: %d\n", jogadores[*totalJogadores].pontuacao);

    if (*totalJogadores < MAX_JOGADORES - 1)
    {
        (*totalJogadores)++;
    }
    else
    {
        printf("Limite maximo de jogadores foi atingido.\n");
    }
}

int etapa5_calcularPontuacao(int tentativas)
{
    int pontos = 60 - tentativas * 4;
    if (pontos < 0)
        pontos = 0;
    return pontos;
}

void etapa5_mostrarRanking(struct Jogador jogadores[], int totalJogadores)
{
    if (totalJogadores == 0)
    {
        printf("\nAinda nao ha jogadores registrados.\n");
        return;
    }

    printf("\n====== [RANKING REGIONAL] ======\n");

    for (int i = 0; i < totalJogadores; i++)
    {
        printf("%dº - %sPontuacao: %d\n", i + 1, jogadores[i].nome, jogadores[i].pontuacao);
    }
}

int main()
{
    int opcao;

    struct Jogador rankingJogadores[MAX_JOGADORES];
    int totalRanking = 0;

    do
    {
        printf("\n===== [menu principal] =====\n");
        printf("1 - modo_de_jogo 1 (sera que voce consegue adivinhar?)\n");
        printf("2 - modo_de_jogo 2 ( voce gosta de desafios?)\n");
        printf("3 - modo_de_jogo 3 (tente adivinhar e descubra sua pontucao)\n");
        printf("4 - modo_de_jogo 4 (Cadastre sua equipe e ache sua pontucao)\n");
        printf("5 - modo_de_jogo 5 (use a logica e  palpites)\n");
        printf("6 - clique para Sair e salvar\n");
        printf("\n[digite o modo que quer jogar e aperte enter]\n");
        printf("voce escolheu a opçao numero: ");
        scanf("%d", &opcao);

        switch (opcao)
        {
        case 1:
            modo_de_jogo1();
            break;
        case 2:
            modo_de_jogo2();
            break;
        case 3:
            modo_de_jogo3();
            break;
        case 4:
            modo_de_jogo4();
            break;
        case 5:
            modo_de_jogo5_jogar(rankingJogadores, &totalRanking);
            break;
        case 6:
            printf("Salvando dados complementares... e Saindo...\n");
            break;
        default:
            printf("Opcao invalida!\n");
        }

    } while (opcao != 6);

    return 0;
}
