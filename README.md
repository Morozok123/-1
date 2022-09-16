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
