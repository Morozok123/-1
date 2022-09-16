#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <stdio.h>
#include <conio.h>

int main()
{
	int i, j, ng, nv, ** Mas, sum = 0;
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
