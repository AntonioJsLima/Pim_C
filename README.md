#include <stdio.h>
#include <string.h>

// ============================================================
//  ATRIBUIDOR DE NOTAS SEMESTRAIS
// ============================================================

// ESTRUTURA PRINCIPAL ----------------------------------------
// Estrutura que armazena as informacoes de cada aluno
struct Aluno_ {
    char nome[50];       // nome do aluno
    char curso[50];      // curso do aluno
    int periodo;         // periodo do aluno
    char materia[50];    // nome da materia
    float Nota;          // nota final calculada
};
// ------------------------------------------------------------

int main() {

    // VARIAVEIS PRINCIPAIS -----------------------------------
    struct Aluno_ alunos[50];  // vetor que armazena os alunos cadastrados
    int Quant_Alun = 0;        // contador de alunos cadastrados
    int opcao;                 // controle do menu principal
    char professor[50];        // nome do professor
    // --------------------------------------------------------

    // ========================================================
    // TELA INICIAL - IDENTIFICACAO DO PROFESSOR
    // ========================================================
    printf("==============================================\n");
    printf("     ATRIBUIDOR DE NOTAS SEMESTRAIS\n");
    printf("==============================================\n\n");

    printf("Digite o nome do professor: ");
    scanf(" %[^\n]", professor);

    printf("\nSeja bem vindo, %s!\n", professor);

    // LOOP PRINCIPAL DO SISTEMA ------------------------------
    do {
        printf("\n==============================================\n");
        printf("MENU PRINCIPAL\n");
        printf("1 - Lancar notas\n");
        printf("2 - Visualizar notas lancadas\n");
        printf("0 - Sair\n");
        printf("==============================================\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);

        // ====================================================
        // OPCAO 1 - LANCAR NOTAS
        // ====================================================
        if (opcao == 1) {
            struct Aluno_ aluno;  // variavel temporaria para novo aluno

            printf("\n=== LANCAR NOTAS ===\n");
            printf("Nome do aluno: ");
            scanf(" %[^\n]", aluno.nome);
            printf("Curso: ");
            scanf(" %[^\n]", aluno.curso);
            printf("Periodo: ");
            scanf("%d", &aluno.periodo);
            printf("Materia: ");
            scanf(" %[^\n]", aluno.materia);

            float np1, np2, pim;
            printf("Nota NP1: ");
            scanf("%f", &np1);
            printf("Nota NP2: ");
            scanf("%f", &np2);
            printf("Nota PIM: ");
            scanf("%f", &pim);

            aluno.Nota = (np1 * 4 + np2 * 4 + pim * 2) / 10; // calculo da nota final

            alunos[Quant_Alun] = aluno; // armazena aluno no vetor
            Quant_Alun++;               // incrementa quantidade

            printf("\nNota registrada com sucesso!\n");
            printf("Pressione Enter para voltar...");
            scanf(" %c"); // pausa para o usuario
        }

        // ====================================================
        // OPCAO 2 - VISUALIZAR NOTAS LANCADAS
        // ====================================================
        else if (opcao == 2) {
            printf("\n=== NOTAS LANCADAS ===\n\n");
            
            if (Quant_Alun == 0) {
                printf("Nenhum aluno cadastrado ainda.\n");
            } else {
                printf("NOME | CURSO | PERIODO | MATERIA | NOTA\n");
                printf("----------------------------------------------\n");

                for (int i = 0; i < Quant_Alun; i++) {
                    printf("%s | %s | %d | %s | %.2f\n",
                           alunos[i].nome,
                           alunos[i].curso,
                           alunos[i].periodo,
                           alunos[i].materia,
                           alunos[i].Nota);
                }
            }

            printf("\nPressione Enter para voltar...");
            scanf(" %c"); // pausa para o usuario
        }

    } while (opcao != 0);

    // ========================================================
    // FINALIZACAO DO PROGRAMA
    // ========================================================
    printf("\nEncerrando o sistema...\n");
    printf("Ate logo, %s!\n", professor);
    printf("==============================================\n");

    return 0;
}

