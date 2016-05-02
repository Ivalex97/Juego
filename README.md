#include <stdio.h>
#include <conio.h>
#include <windows.h>
#include <time.h>

#define  f 30
#define c 30

void construir (int mapa[f][c], int niv);
void imprimir (int mapa [f][c]);
void jugar (int mapa [f][c]);
void color(int x);// Funcion Color
void cursor ( short x, short y );
void diamantes (int mapa[f][c]);
int ganar(int mapa[f][c]);
void monstruo(int mapa[f][c]);


int main(){
	int mapa[f][c];
	
	
	
	
	cursor(30,2);
	system("color 09");
	color(0*16+9);
	printf(">>Nivel 1<<");
	Sleep(1000);
	system("cls");
	
	
	construir (mapa,1);
	diamantes(mapa);
	
	
	imprimir (mapa);
	
	jugar (mapa);
	
	
	cursor(30,2);
	color(0*16+9);
	Sleep(1000);
	printf(">>Nivel 2<<");
} 
  
void construir (int mapa[f][c], int niv) {

	
	int aux[f][c]={{5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5},
				   {5,0,0,0,0,0,0,0,0,5,0,0,5,5,0,0,0,0,0,5,0,0,5,5,0,0,0,0,0,5},
				   {5,0,2,5,0,5,0,0,0,5,0,0,0,0,0,0,5,0,5,5,0,0,5,5,0,0,0,0,0,5},
				   {5,0,5,5,0,0,0,0,0,5,5,5,5,5,5,0,0,0,0,5,0,0,0,0,0,0,0,0,5,5},
				   {5,5,0,0,0,5,0,0,5,0,0,0,0,0,0,0,0,0,5,5,0,0,0,0,0,0,0,0,0,5},
				   {5,0,0,0,0,0,5,5,0,0,0,0,0,5,0,5,5,5,5,0,0,0,5,5,5,5,5,0,5,5},
				   {5,5,5,5,0,0,0,0,0,0,0,0,0,0,0,5,5,5,0,5,0,0,0,0,0,0,5,0,0,5},
				   {5,0,0,0,5,5,5,5,5,5,5,0,0,0,0,5,0,5,0,5,0,0,0,0,0,0,5,0,0,5},
				   {5,0,0,0,0,0,0,0,0,0,0,5,0,0,0,0,0,0,0,5,0,0,0,0,0,0,5,0,0,5},
				   {5,5,5,5,5,5,0,0,0,0,0,0,0,0,0,5,5,5,5,5,0,0,0,0,0,0,5,0,0,5},
				   {5,0,0,0,0,0,0,0,5,5,5,0,5,5,0,0,0,0,0,5,0,0,5,5,5,5,5,0,5,5},
				   {5,0,5,0,0,0,0,0,0,5,0,0,0,0,5,0,5,0,5,5,0,0,5,0,0,0,0,0,0,5},
				   {5,0,5,5,0,0,0,0,0,5,5,5,5,5,5,0,0,0,0,5,0,0,5,0,0,0,0,0,0,5},
				   {5,5,0,0,0,5,0,0,5,0,0,0,0,0,0,0,0,0,5,5,0,0,0,0,5,5,0,0,0,5},
				   {5,0,0,0,0,5,5,5,5,0,0,0,0,0,0,0,0,0,0,5,0,0,0,0,0,0,0,0,0,5},
				   {5,5,5,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,5,0,5,5,5,0,5},
				   {5,0,0,0,5,5,5,5,5,5,5,0,0,0,0,0,0,5,0,5,5,0,0,0,5,5,5,5,0,5},
				   {5,5,5,5,0,0,0,0,0,0,0,0,0,0,0,5,0,5,0,5,0,0,0,0,0,0,0,5,0,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,5,0,5,0,0,0,5,0,0,0,5,0,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,5,0,5,0,0,0,0,0,0,0,5,0,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,5,0,0,5,5,0,0,0,0,0,5,0,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,5,0,0,0,0,5,5,0,0,0,0,0,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,5,0,5,0,0,5,5,0,0,0,0,0,5},
				   {5,0,0,0,0,5,5,0,0,5,5,0,0,0,0,5,0,5,0,5,5,0,0,0,5,5,5,5,0,5},
				   {5,0,0,0,0,5,5,0,0,5,5,0,0,0,0,5,0,5,0,0,0,0,5,0,0,0,5,0,5,5},
				   {5,0,0,0,0,5,5,0,0,5,5,0,0,0,0,5,0,5,0,5,0,0,5,0,0,0,0,0,0,5},
				   {5,0,0,0,0,5,5,0,0,5,5,0,0,0,0,5,0,5,0,5,0,0,5,0,0,5,5,0,0,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,0,0,5,0,0,5,0,0,5,0,0,5,5},
				   {5,0,0,0,0,5,5,0,0,0,0,0,0,0,0,5,0,5,0,5,0,0,5,5,0,0,0,0,0,5},
				   {5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5,5}, };
				   
				
				   
				   
				   
				   
				   
						   
   int i,j;
   	for(i=0;i<f;i++){
   		for(j=0;j<c;j++){
   			if(niv==1)
   				mapa [i][j]=aux[i][j];
   			/*if (niv==2){
   				mapa[i][j]=aux2[i][j];
			   }*/
		   }
	   }			   
				   
				   
				   
}
   				   
   				   
   			   


void imprimir(int mapa[f][c]){
	system("color 04");
    int	x,y;
	for (x=0;x<f;x++){
		
		printf("\n");
		for(y=0;y<c;y++){
			if(mapa[x][y]==0){
				color (0*16+4);//llamada a funcion color
				printf(" ");
			}
			if(mapa[x][y]==5){
				color (0*16+4);//funcion color
			printf("%c",219);
			}
			
			
			if(mapa[x][y]==2){
				color (0*16+9);// funcion color
			printf("%c",2);
			
			}
			if(mapa[x][y]==4){
			
				color(0*16+14);
				printf("%c",4);
				
			}
			if(mapa[x][y]==3){
				color(0*16+15);
				printf("%c",1);
			}
		}
	}
	
		


	
}

void jugar (int mapa [f][c]){
	
	int fila_pos=2, colu_pos=2,G;
	char tecla;
	
	while (G!=0){
		
		
		G=ganar(mapa);
		if(kbhit()){   // para esperar una tecla
		tecla=getch();//leer tecla

		if ((tecla=='d'|| tecla=='D') && mapa[fila_pos][colu_pos+1]==0 || mapa[fila_pos][colu_pos+1]==4){// Derecha
			mapa[fila_pos][colu_pos]=0;

			colu_pos++;
					
			mapa[fila_pos][colu_pos]=2;// Imprimir nueva posicion
		
			system ("cls");
			imprimir(mapa);
			Sleep(50);
	
		}
		if((tecla=='a'|| tecla=='A' ) && mapa[fila_pos][colu_pos-1]==0 || mapa[fila_pos][colu_pos-1]==4){//Izquierda
			mapa[fila_pos][colu_pos]=0;

			colu_pos--;
			mapa[fila_pos][colu_pos]=2;//Imprimir nueva posicion
		
		
			system ("cls");
			imprimir(mapa);
			Sleep(50);
			
		}
		
		if((tecla=='w'|| tecla=='W' ) && mapa[fila_pos-1][colu_pos]==0 || mapa[fila_pos-1][colu_pos]==4){// Arriba
			mapa[fila_pos][colu_pos]=0;

			fila_pos--;
			mapa[fila_pos][colu_pos]=2;// Imprimir nueva posicion
		
			system ("cls");
			imprimir(mapa);
			Sleep(50);
			
		}
		if((tecla=='s'|| tecla=='S' ) && mapa[fila_pos+1][colu_pos]==0 || mapa[fila_pos+1][colu_pos]==4){//Abajo
			mapa[fila_pos][colu_pos]=0;

			fila_pos++;
			mapa[fila_pos][colu_pos]=2;// Imprimir nueva posicion
		
		
			system ("cls");
			imprimir(mapa);
			Sleep(50);
		
	}
		
		
	
		
		
		}
		
		 
	}
	system("cls");
		
	
	if(G==0){
	
	cursor (20,4);
	color(0*16+9);
	
	printf("Nivel 1 finalizado\n\n");
    }
    
	
	
}


void color (int X){
	HANDLE hcon = GetStdHandle(STD_OUTPUT_HANDLE);
SetConsoleTextAttribute(hcon,X);
}

void cursor ( short x, short y )
{
  COORD coord = {x, y};
  SetConsoleCursorPosition ( GetStdHandle ( STD_OUTPUT_HANDLE ), coord );
}

void diamantes (int mapa[f][c]){
	int diam=0;
	int ydiam=0;
	int xdiam=0;
	srand(time(0));
	
	while(diam<20){
		xdiam=rand()%(30-1)+1;//Puntos aleatorios para los diamantes
		ydiam=rand()%(30-1)+1;
		
		if(mapa[xdiam][ydiam]==0 && mapa[diam][ydiam]!=4 && mapa[xdiam][ydiam]!=5){
	 		mapa[xdiam][ydiam]=4;
			
			diam++;	
		}
			
	}
	
}


int ganar(int mapa[f][c]){
	int x,y,g=0;
	
	for(x=0;x<f;x++){
		for(y=0;y<c;y++){
		
		if(mapa[x][y]==4)
		g++;
	
		
		}
	}
	
	return g;
}

void monstruo(int mapa[f][c]){
	int y_mon=28,x_mon=1;



	
	
		mapa[x_mon][y_mon]=0;
		y_mon--;	
		mapa[x_mon][y_mon]=3;
		imprimir(mapa);
		
	

}
