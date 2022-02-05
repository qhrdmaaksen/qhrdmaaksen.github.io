---
layout: single
title: "자료구조03_정렬"
---

# 자료구조
<ul>
<li>선택정렬</li>
<li>삽입정렬</li>
<li>버블정렬</li>
</ul>

선택정렬
```js
//list index 중 가장 작은 순서대로 나열하기 -선택 정렬-
#include <stdio.h>
int Min(int list[], int sIndex, int eIndex) {
	int min = sIndex; //리스트의 0번째 index
	for (int i = sIndex + 1; i <= eIndex; i++)
	{
		if (list[min] > list[i])//리스트의 최소값보다 리스트의 i 번째가 작다면 true
		{
			min = i;//1번째 인덱스가 20이기에 최소값에는 20이 대입됨
			printf("min : %d\n", min);//index min 위치 출력
		}
	}
	return min;
}
void Swap(int* pa, int* pb) {
	int temp = *pa;
	*pa = *pb;
	*pb = temp;
}
void PrintList(int list[], int size) {
	for (int i = 0; i < size; i++)
	{
		printf("%5d", list[i]);
	};
	printf("\n");
}
int main() {
	int list[10] = { 80,20,70,50,60,90,40,30 };
	int size = 8;

	PrintList(list, size);
	{
		for (int i = 0; i < size - 1; i++)
		{
			int min = Min(list, i, size - 1);
			Swap(&list[i], &list[min]);
		}
	}
	PrintList(list, size);
	return 0;
};
```

삽입정렬
```js
//list index 중 가장 작은 순서대로 나열하기 -삽입 정렬-
#include <stdio.h>
int Min(int list[], int sIndex, int eIndex) {
	int min = sIndex; //리스트의 0번째 index
	for (int i = sIndex + 1; i <= eIndex; i++)
	{
		if (list[min] > list[i])//리스트의 최소값보다 리스트의 i 번째가 작다면 true
		{
			min = i;//1번째 인덱스가 20이기에 최소값에는 20이 대입됨
			printf("min : %d\n", min);//index min 위치 출력
		}
	}
	return min;
}
void Swap(int* pa, int* pb) {
	int temp = *pa;
	*pa = *pb;
	*pb = temp;
}
void InsertionSort(int list[], int size) {

	int cur = 4; 
	int value = list[cur];
	int j;
	for ( j = cur-1; 1 ; --j)
	{
		if (list[j]>value)
		{
			list[j + 1] = list[j];
		}
		else
		{
			break; 
		}
	}
	list[j + 1] = value;
}
void PrintList(int list[], int size) {
	for (int i = 0; i < size; i++)
	{
		printf("%5d", list[i]);
	};
	printf("\n");
}
int main() {
	//int list[10] = { 80,20,70,50,60,90,40,30 };
	int list[10] = { 20,50,70,80,60,90,40,30 };
	int size = 8;

	PrintList(list, size);
	
	InsertionSort(list, size); 

	PrintList(list, size);
	return 0;
};
```

버블정렬
```js
//list index 중 가장 작은 순서대로 나열하기 -삽입 정렬-
//정렬되어있는곳에 값을 넣어 교체하며 앞의 인덱스와 비교하는것이아닌 인덱스를 뒤로 밀면서 비교
#include <stdio.h>
int Min(int list[], int sIndex, int eIndex) {
	int min = sIndex; //리스트의 0번째 index
	for (int i = sIndex + 1; i <= eIndex; i++)
	{
		if (list[min] > list[i])//리스트의 최소값보다 리스트의 i 번째가 작다면 true
		{
			min = i;//1번째 인덱스가 20이기에 최소값에는 20이 대입됨
			printf("min : %d\n", min);//index min 위치 출력
		}
	}
	return min;
}
void Swap(int* pa, int* pb) {
	int temp = *pa;
	*pa = *pb;
	*pb = temp;
}
	int j;
	int value;
	void BubbleSort(int list[], int size) {

		for (int i = 0; i < size-1; i++)//제일 마지막 부터 다시 앞으로 줄이며 
		{

		for (int j = 0; j < (size-1)-i; ++j)//제일 큰 수를 제일 마지막에 위치
		{
			if (list[j] > list[j + 1])
			{
				Swap(&list[j], &list[j + 1]);
			}
		}
		}
	};
void PrintList(int list[], int size) {
	for (int i = 0; i < size; i++)
	{
		printf("%5d", list[i]);
	};
	printf("\n");
}
int main() {
	//int list[10] = { 80,20,70,50,60,90,40,30 };
	int list[10] = { 20,50,70,80,10,90,40,30 };
	int size = 8;

	PrintList(list, size);

	BubbleSort(list, size);

	PrintList(list, size);
	return 0;
};
```