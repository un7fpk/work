# Работа
void Sort(int array[], int size){
	for(int x=size/2;x>0;x/=2){
		for(int i=x;i<size;i++){
			for(int j=i-x;j>=0 && array[j]>array[j+x];j-=x){
				int y=array[j];
				array[j]=array[j + x];
				array[j + x]=y;
			}
		}
	}
}
