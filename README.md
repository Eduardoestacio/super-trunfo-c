# super-trunfo-c
trabalho
#include <stdio.h>

typedef struct {
    char nome[20];
    int forca;
    int velocidade;
    int inteligencia;
} Carta;

// Função para mostrar atributos da carta
void mostrarCarta(Carta c) {
    printf("Carta: %s | Força: %d | Velocidade: %d | Inteligência: %d\n",
           c.nome, c.forca, c.velocidade, c.inteligencia);
}

// =================== DESAFIO 1 ===================
void comparacaoSimples(Carta c1, Carta c2) {
    int escolha;
    printf("\n=== COMPARAÇÃO SIMPLES ===\n");
    mostrarCarta(c1);
    mostrarCarta(c2);

    printf("\nEscolha o atributo para comparar:\n");
    printf("1 - Força\n");
    printf("2 - Velocidade\n");
    printf("3 - Inteligência\n");
    printf("Opção: ");
    scanf("%d", &escolha);

    if (escolha == 1) {
        if (c1.forca > c2.forca)
            printf("%s venceu!\n", c1.nome);
        else if (c2.forca > c1.forca)
            printf("%s venceu!\n", c2.nome);
        else
            printf("Empate!\n");
    } else if (escolha == 2) {
        if (c1.velocidade > c2.velocidade)
            printf("%s venceu!\n", c1.nome);
        else if (c2.velocidade > c1.velocidade)
            printf("%s venceu!\n", c2.nome);
        else
            printf("Empate!\n");
    } else if (escolha == 3) {
        if (c1.inteligencia > c2.inteligencia)
            printf("%s venceu!\n", c1.nome);
        else if (c2.inteligencia > c1.inteligencia)
            printf("%s venceu!\n", c2.nome);
        else
            printf("Empate!\n");
    } else {
        printf("Opção inválida!\n");
    }
}

// =================== DESAFIO 2 ===================
void comparacaoSwitch(Carta c1, Carta c2) {
    int escolha;
    printf("\n=== COMPARAÇÃO COM SWITCH ===\n");
    mostrarCarta(c1);
    mostrarCarta(c2);

    printf("\nEscolha o atributo para comparar:\n");
    printf("1 - Força\n");
    printf("2 - Velocidade\n");
    printf("3 - Inteligência\n");
    printf("Opção: ");
    scanf("%d", &escolha);

    switch (escolha) {
        case 1:
            printf("Comparando Força...\n");
            if (c1.forca > c2.forca) printf("%s venceu!\n", c1.nome);
            else if (c2.forca > c1.forca) printf("%s venceu!\n", c2.nome);
            else printf("Empate!\n");
            break;
        case 2:
            printf("Comparando Velocidade...\n");
            if (c1.velocidade > c2.velocidade) printf("%s venceu!\n", c1.nome);
            else if (c2.velocidade > c1.velocidade) printf("%s venceu!\n", c2.nome);
            else printf("Empate!\n");
            break;
        case 3:
            printf("Comparando Inteligência...\n");
            if (c1.inteligencia > c2.inteligencia) printf("%s venceu!\n", c1.nome);
            else if (c2.inteligencia > c1.inteligencia) printf("%s venceu!\n", c2.nome);
            else printf("Empate!\n");
            break;
        default:
            printf("Opção inválida!\n");
    }
}

// =================== DESAFIO 3 ===================
void comparacaoDoisAtributos(Carta c1, Carta c2) {
    int escolha1, escolha2;
    printf("\n=== COMPARAÇÃO COM DOIS ATRIBUTOS ===\n");
    mostrarCarta(c1);
    mostrarCarta(c2);

    printf("\nEscolha o primeiro atributo (1-Força, 2-Velocidade, 3-Inteligência): ");
    scanf("%d", &escolha1);
    int valor1_c1 = (escolha1 == 1) ? c1.forca : (escolha1 == 2) ? c1.velocidade : c1.inteligencia;
    int valor1_c2 = (escolha1 == 1) ? c2.forca : (escolha1 == 2) ? c2.velocidade : c2.inteligencia;

    printf("Escolha o segundo atributo (1-Força, 2-Velocidade, 3-Inteligência): ");
    scanf("%d", &escolha2);
    int valor2_c1 = (escolha2 == 1) ? c1.forca : (escolha2 == 2) ? c1.velocidade : c1.inteligencia;
    int valor2_c2 = (escolha2 == 1) ? c2.forca : (escolha2 == 2) ? c2.velocidade : c2.inteligencia;

    int total1 = valor1_c1 + valor2_c1;
    int total2 = valor1_c2 + valor2_c2;

    printf("\nResultado da soma: %s (%d) x %s (%d)\n", c1.nome, total1, c2.nome, total2);

    (total1 > total2) ? printf("%s venceu!\n", c1.nome) :
    (total2 > total1) ? printf("%s venceu!\n", c2.nome) :
    printf("Empate!\n");
}

// =================== MAIN ===================
int main() {
    Carta carta1 = {"Dragão", 90, 70, 60};
    Carta carta2 = {"Fênix", 85, 80, 75};

    int opcao;
    do {
        printf("\n===== SUPER TRUNFO =====\n");
        printf("1 - Comparação Simples (if)\n");
        printf("2 - Comparação com Switch\n");
        printf("3 - Comparação com Dois Atributos (ternário)\n");
        printf("0 - Sair\n");
        printf("Escolha: ");
        scanf("%d", &opcao);

        switch (opcao) {
            case 1:
                comparacaoSimples(carta1, carta2);
                break;
            case 2:
                comparacaoSwitch(carta1, carta2);
                break;
            case 3:
                comparacaoDoisAtributos(carta1, carta2);
                break;
            case 0:
                printf("Saindo do jogo...\n");
                break;
            default:
                printf("Opção inválida!\n");
        }
    } while (opcao != 0);

    return 0;
}
