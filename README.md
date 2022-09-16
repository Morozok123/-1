//Задание 1
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>	
#include <stdio.h>	
#include <conio.h>

void main()
{
	int i, n, * Mas;
	setlocale(0, "rus");
	printf("Введите количество элементов в массиве: ");
	scanf("%d", &n);
	Mas = (int*)malloc(n * sizeof(int));
	srand(time(0));
	printf("Сгеннерированный массив:\n");
	for (i = 0; i < n;i++)
	{
		Mas[i] = rand() % 201 - 100;
		printf("|%2d| ", Mas[i]);
	}
	int min = 0, max = 0;
	for (i = 0;i < n;i++)
	{
		if (Mas[i] < Mas[min]) min = i;
		if (Mas[i] > Mas[max]) max = i;
	}
	printf("\n%d - %d = %d", Mas[max], Mas[min], Mas[max] - Mas[min]);
	_getch();
}
	
//Задание 2-4
	#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <stdio.h>
#include <conio.h>

int main()
{
	int i, j, ng, nv, ** Mas, sum = 0, gran = 1;
	setlocale(0, "rus");
	srand(time(0));
	//Задание 3
	printf("Введите размер массива по вертикали: ");
	scanf("%d", &nv);
	printf("Введите размер массива по горизонтали: ");
	scanf("%d", &ng);
	Mas = (int**)malloc(ng * sizeof(int*));
	srand(time(0));
	//Задание 2
	printf("Сгенерированный массив:\n");
	for (i = 0;i < nv;i++)

	{
		Mas[i] = (int*)malloc(nv * sizeof(int));

		for (j = 0;j < ng;j++)
		{
			Mas[i][j] = rand() % 201 - 100;
			printf("|%4d| ", Mas[i][j]);
		}
		printf("\n");
	}
	printf("\n");
	//Задание для сдачи
	for (i = 0;i < nv;i++)
	{
		for (j = i;j < ng;j++) 
		{
			sum += Mas[i][j];
		}
	}
	printf("Сумма выше главной диагонали = %d\n\n", sum);
	sum = 0;
	//Задание 4
	for (i = 0;i < nv;i++)
	{
		for (j = 0;j < ng;j++)
		{
			sum += Mas[i][j];
		}
		printf("Сумма %d строки: %-7d\n", i + 1, sum);
		sum = 0;
	}
	printf("\n");
	for (j = 0;j < ng;j++)
	{
		for (i = 0;i < nv;i++)
		{
			sum += Mas[i][j];
		}
		printf("Сумма %d столбца: %-7d\n", j + 1, sum);
		sum = 0;
	}
	_getch();
	return 0;
}
	
//Задание 5
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <stdio.h>
#include <conio.h>

int main(void)
{
	setlocale(0, "rus");
	setvbuf(stdin, NULL, _IONBF, 0);
	setvbuf(stdout, NULL, _IONBF, 0);
	int i;
	int t = 0;
	char Srch[20];
	char answer;
	int anser;
	struct student
	{
		char famil[20];
		char name[20], facult[20];
		int Nomzach;
	} stud[3];

	for (i = 0;i < 3;i++)
	{
		printf("Введите фамилию студента\n"); scanf("%20s", stud[i].famil);
	}
	for (i = 0;i < 3;i++)
	{
		printf("Введите имя студента %s\n", stud[i].famil); scanf("%20s", stud[i].name);
	}
	for (i = 0;i < 3;i++)
	{
		printf("Введите название факультета студента %s %s\n", stud[i].famil, stud[i].name); scanf("%20s", stud[i].facult);
	}
	for (i = 0;i < 3;i++)
	{
		printf("Введите номер зачётной книжки студента %s %s\n", stud[i].famil, stud[i].name); scanf("%d", &stud[i].Nomzach);
	}
	printf("\n");
	while (1)
	{
		system("cls");
		printf("Выберите столбец для поиска:\n");
		printf("1 - Фамилия студента\n");
		printf("2 - Имя студента\n");
		printf("3 - Название факультета студента\n");
		printf("4 - Номер зачётной книжки студента\n");
		scanf_s("%c", &answer, 1);
		switch (answer)
		{
			case('1'):
			{
				printf("Введите фамилию студента для поиска:");
				scanf("%s", Srch);
				for (i = 0;i < 3;i++) 
				{
					if (strcmp(stud[i].famil, Srch) == 0)
					{
						printf("Cтудент %s %s обучается на факультете %s, номер зачётной книжки %d \n", stud[i].famil, stud[i].name, stud[i].facult, stud[i].Nomzach);
						t = 1;
					}
				}
				if (t == 0) printf("Фамилия не найдена");
				return 0;
			}
			case('2'):
			{
				printf("Введите имя студента для поиска:");
				scanf("%s", Srch);
				for (i = 0;i < 3;i++)
				{
					if (strcmp(stud[i].name, Srch) == 0)
					{
						printf("Cтудент %s %s обучается на факультете %s, номер зачётной книжки %d \n", stud[i].famil, stud[i].name, stud[i].facult, stud[i].Nomzach);
						t = 1;
					}
				}
				if (t == 0) printf("Имя не найдено");
				return 0;
			}
			case('3'):
			{
				printf("Введите название факультета студента для поиска:");
				scanf("%s", Srch);
				for (i = 0;i < 3;i++)
				{
					if (strcmp(stud[i].facult, Srch) == 0)
					{
						printf("Cтудент %s %s обучается на факультете %s, номер зачётной книжки %d \n", stud[i].famil, stud[i].name, stud[i].facult, stud[i].Nomzach);
						t = 1;
					}
				}
				if (t == 0) printf("Название факультета не найдено");
				return 0;
			}
			case('4'):
			{
				printf("Введите номер зачётной книжки студента для поиска:");
				scanf("%d", &anser);
				for (i = 0;i < 3;i++)
				{
					if (anser == stud[i].Nomzach)
					{
						printf("Cтудент %s %s обучается на факультете %s, номер зачётной книжки %d \n", stud[i].famil, stud[i].name, stud[i].facult, stud[i].Nomzach);
					}
					
				}
				if (t == 0) printf("Номер зачётной книжки не найден");
				return 0;
			}
		}
	}
}
