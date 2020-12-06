# work
void Ssort(int * num,int i, int newsize){
    int max, a=0;
    while((2*i<=newsize) && (!a)){
        if(2*i==newsize){
            max=2*i;
        }
        else if(num[2*i]>num[2*i+1]){
            max=2*i;
        }
        else{
            max=2*i+1;
        }
        if(num[i]<num[max]){
            int buf = num[i];
            num[i] = num[max];
            num[max] = buf;
            i = max;
        }
        else{
            a=1;
        }
    }
}
void Psort(int * num, int size){
    for(int i = size/2-1;i>=0;i--){
        Ssort(num, i, size-1);
    }
    for(int i = size-1;i>=1;i--){
        int buf = num[0];
        num[0] = num[i];
        num[i] = buf;
        Ssort(num, 0, i-1);
    }
}
void Qsort(int * array, int size, int z, int * q){
    int i=0, j=size-1;
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
        q[1]=i;
    }
    if(j>0){
        q[2]=j;
    }
}

void Intrsort(int * array, int size, int r, int * q){
    if(size<=16 || r==0){
        Ssort(array, 0, size);
    } else {
        int a = array[0], b = array[(size-1)/2], c = array[size-1];
        if(a>b && a>c){
            int point = a;
        } else if (b>c){
            int point = b;
        } else {
            int point = c;
        }
        Qsort(array, size, point, q);
        Intrsort(&array[q[1]], size-q[1], r, q);
        Intrsort(array, q[2]+1, r, q);
    }
    
}

int main () {
    // ввод массива 
    // размер
    int *q= malloc(sizeof(int)2);
    int r = 2*log(size);
    Intrsort(&array[0], size, r, q);
    free(q);    
    return 0;
}
