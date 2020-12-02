# Работа
void Qsort(int *array, int size){
    int i=0, j=size-1, z=array[size/2];
    do{
        while(array[i]<z){
            i++;
        }
        while(array[j]>z){
            j--;
        }
        if(i<=j){
            int buf = array[i];
            array[i] = array[j];
            array[j] = buf;
            i++;
            j--;
        }
    }while(i<=j);
    if(i<size){
        Qsort(&array[i], size-i);
    }
    if(j>0){
        Qsort(array, j+1);
    }
}
