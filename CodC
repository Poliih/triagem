	#include <stdio.h>
	#include <stdlib.h>
	#include <string.h>
	#include <locale.h>
	
	char nome[200];
	char cpf[200];
	char sexo[2];
	int idade;
	int main();

	struct triagem {
		char perg[400];
		int pontos;	
	};
	
	struct triagem questoes[] = {
		{ .perg = "Tem febre? ", .pontos = 5 },
		{ .perg = "Tem dor de cabeça? ", .pontos = 1 },
		{ .perg = "Tem secreção nasal ou espirros? ", .pontos = 1 },
		{ .perg = "Tem dor/irritação na garganta? ", .pontos = 1 },
		{ .perg = "Tem tosse seca? ", .pontos = 3 },
		{ .perg = "Tem dificuldade respiratória? ", .pontos = 10 },
		{ .perg = "Tem dores no corpo? ", .pontos = 1 },
		{ .perg = "Tem diarréia? ", .pontos = 1 },
		{ .perg = "Esteve em contato, nos últimos 14 dias, com um caso diagnosticado com COVID-19? ", .pontos = 10 },
		{ .perg = "Esteve em locais com grande aglomeração? ", .pontos = 3 },
	};
	
	void perguntas(){
		
		char resp;
		int soma = 0;
		int i = 0;
		
		FILE *arquivoTxt;
		arquivoTxt = fopen("dataBase.txt", "a");
		
		if (arquivoTxt==NULL)
		{
			printf("Erro ao criar arquivo");
		}
		
		system("cls");
		printf("Responda com S para SIM ou N para NAO\n");
		printf("--------------------------------------\n");
		for(i = 0; i < 10; i++){
			printf("%s", questoes[i].perg);
			scanf("%c", &resp);
			fflush(stdin);
			fprintf(arquivoTxt, "%s %c\n", questoes[i].perg, resp);
			if(resp == 'S' || resp == 's'){
				soma = soma + questoes[i].pontos;			
			}
		}	
		fprintf(arquivoTxt, "Pontuacao total: %d", &soma);
		fclose(arquivoTxt);
		
		system("cls");
		if(soma >= 0 && soma < 10){
			printf("Voce somou %d pontos e deve encaminhe-se para a Ala de BAIXO RISCO\n", soma);
		}
		if(soma >= 10 && soma < 20){
			printf("Voce somou %d pontos e deve encaminhe-se para a Ala de MEDIO RISCO\n", soma);
		}
		if(soma >= 20){
			printf("Voce somou %d pontos e deve encaminhe-se para a Ala de ALTO RISCO\n", soma);
		}
		soma = 0;
		
		printf ("Pressione ENTER para voltar ao Menu Principal...");
		getchar();
		main();
		
	}

	void cadastrarP() {
		
		setlocale(LC_ALL, "Portuguese");
		
		FILE *arquivoTxt;
		arquivoTxt = fopen("dataBase.txt", "a");
		if (arquivoTxt==NULL)
		{
			printf("Erro ao criar arquivo");
		}
		
		printf("Insira o NOME do paciente: ");
		scanf("%s", nome);
		fflush(stdin);
		
		printf("Insira o CPF do paciente: ");
		scanf("%s", cpf);
		fflush(stdin);
		
		printf("Insira o SEXO do paciente (M/F): ");
		scanf("%s", sexo);
		fflush(stdin);
		
		printf("Insira a IDADE do paciente: ");
		scanf("%d", &idade);
		fflush(stdin);
		
		fprintf(arquivoTxt, "Nome: %s\nCPF: %s\nSexo: %s\nIdade: %d\n", nome, cpf, sexo, idade);
		fclose(arquivoTxt);
		
		printf("Dados completamente salvos\n");
		getchar();
		
		perguntas();
		
	}
	
	int main() {
		
		setlocale(LC_ALL, "Portuguese");
		
		int opc;
		
		printf("-----____MENU____-----\n");
		printf("Selecione uma opção\n");
		printf("1 - Cadastrar Paciente\n");
		printf("2 - Sair\n");
		scanf("%i", &opc);
		fflush(stdin);
		
		switch(opc) {
			case 1:
			    cadastrarP(); 	
			    break;
			case 2:
			    printf("\n Finalizando...");
				break;
			default:
				break;
		}
		
	}
