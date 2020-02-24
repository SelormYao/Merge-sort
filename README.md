// merge sort


#include<stdlib.h> 
#include<stdio.h> 
#include<iostream>
 
using namespace std;
 
 
void merge(int a[], int Firstindex, int m, int Lastindex) 
{ 
    int x; 
    int y;
    int z;
    int fdiv = m - Firstindex + 1; 
    int sdiv =  Lastindex - m; 
    int sub1;
    int sub2;
   
     
    int First[fdiv]; 
     
    int Second[sdiv]; 
   
     
    for (x = 0; x < fdiv; x++)
        First[x] = a[Firstindex + x]; 
    for (y = 0; y < sdiv; y++) 
        Second[y] = a[m + 1+ y]; 
   
     
    x = 0; 
    y = 0; 
    int f = Firstindex; 
    while (x < sub1 && y < sub2) 
    { 
        if (First[x] <= Second[y]) 
        { 
            a[f] = First[x]; 
            x++; 
        } 
        else
        { 
            a[f] = Second[y]; 
            y++; 
        }
        f++; 
    } 
    while (x < sub1) 
    { 
        a[f] = First[x]; 
        x++; 
        f++; 
    } 
    while (y < sub2) 
    { 
        a[f] = Second[y]; 
        y++; 
        f++; 
    } 
} 

void mergeSort(int a[], int Firstindex, int Lastindex) 
{ 
    if (Firstindex < Lastindex) 
    { 
         
        int m = Firstindex + (Lastindex - Firstindex)/2; 
   
         
        mergeSort(a, Firstindex, m); 
        mergeSort(a, m+1, Lastindex); 
   
        merge(a, Firstindex, m, Lastindex); 
    } 
}   




int main() 
{ 
    int size;
    cout<<"Enter the size of the Array that is to be sorted: "; cin>>size;
    int value[size],i;
    cout<<"Enter the values of your array";
    for(i=0; i<size; i++) cin>>value[i];
    
    mergeSort(value, 0, size - 1);
    cout<<"The Sorted List is";
    for(i=0; i<size; i++)
    {
        cout<<value[i]<<" ";
    }
    return 0;
}
