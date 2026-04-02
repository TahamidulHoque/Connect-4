# Connect-4
/*Tahamidul Hoque
Period 7
Connect 4 project*/

#include<iostream>
using namespace std;

bool is_win(char val,char b[6][7]){
	bool is_won=false;
	//check horizontal
	for(int r=0; r<6; r++){
		for(int c=0; c<4; c++){
			if(b[r][c]==val&&b[r][c+1]==val&&b[r][c+2]==val&&b[r][c+3]==val){
			
				is_won=true;
			
			}
		}
	}
  	
  	//check for vertical 
  	for(int c=0; c<7; c++){
  		for(int r=0; r<4;r++){
  			if(b[r][c]==val&&b[r+1][c]==val&&b[r+2][c]==val&&b[r+3][c]==val){
  				
  				is_won=true;

			  }
		  }
	  }
	//check diagnoal bottom to top
	for(int r=5; r>=3;r-- ){
		for(int c=0; c<4;c++){
			if(b[r][c]==val&&b[r-1][c+1]==val&&b[r-2][c+2]==val&&b[r-3][c+3]==val){
				is_won=true;
			}
		}
	}
	//check for diagnol top to bottom 
	for(int r=0; r<3; r++){
		for(int c=0; c<4;c++){
			if(b[r][c]==val&&b[r+1][c+1]==val&&b[r+2][c+2]==val&&b[r+3][r+3]==val){

				is_won=true;
				
			}
		}
	}
	if(is_won){
		cout<<"You won!";
		return is_won;
	}
	return is_won;
}


void reset_board(char b[6][7]){
	for(int i=0; i<6; i++){
		for(int j=0; j<7; j++){
			b[i][j]='_';
		}
	}
}

void print_board(char b[6][7]){
	for(int i=1; i<=7; i++)
		cout<<i<<" ";
	cout<<endl;
	for(int i=0; i<6; i++){
		for(int j=0; j<7; j++){
			cout<<b[i][j]<<" ";
		}
		cout<<endl;
	}
	for(int i=1; i<=7; i++)
		cout<<i<<" ";
	cout<<endl;
}
void drop(char val,int column,char b[6][7]){
	for(int r=5; r>=0; r--){
		if(b[r][column-1]=='_'){
			b[r][column-1]=val;
			r=-1;
		}
	}
		
}

int main(){
	char b[6][7];
	reset_board(b);
	int input; 
	print_board(b);
	char val;
	int counter=0;
	do{
		if(counter%2==0){
			cout<<"choose a column for X: ";
			cin>>input;
			 val='X';
			drop(val,input,b);
			}
			
		if(counter%2==1){
			cout<<"choose a column for O: ";
			cin>>input;
			val='O';
			drop(val,input,b);
			}
		
		counter++;
		print_board(b);
	}while(!is_win(val,b));

}
