# test_6_6
#include <stdio.h>
//归并排序
#include <stdlib.h>
int*B = (int*)malloc(n*sizeof(int));
void Merge(int A[],int low,int mid,int high){
	int i,j,k;
	for(int k=low;k<=high;k++)
		B[k] = A[k];
	for(int i=low,j=mid+1,k=i;i<=mid && j<=high;k++){
		if(B[i] <= B[j])
			A[k] = B[i++];
		else
			A[k] = B[j++];
	}
	while(i<=mid)
		A[k++] = B[i++];
	while(j<=high)
		A[k++] = B[j++];
}
void MergeSort(int A[],int low,int high){
	if(low<high){
		int mid = (low+high)/2;
		MergeSort(A,low,mid);
		MergeSort(A,mid+1,high);
		Merge(A,low,mid,high);
	}
}
bool ListDelete(SqList &L,int i,int &e){
	if(i<1 || i>L.length)
		return false;
	e = L.data[i-1];
	for(int j=i;j<L.length;j++)
		L.data[j-1] = L.data[j];
	L.length--;
	return true;
}
bool ListInsert(SqList &L,int i,int e){
	if(i<1 || i>L.length+1)
		return false;
	if(L.length>=MaxSize)
		return false;
	for(int j=L.length;j>=i;j--)
		L.data[j] = L.data[j-1];
	L.data[i] = e;
	L.length++;
	return true;
}
