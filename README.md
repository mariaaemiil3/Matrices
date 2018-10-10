#include <iostream>
#include <iomanip>

using namespace std;


struct matrix
{
    int** data;
    int row, col;
};


void createMatrix (int row, int col, int num[], matrix& mat);
void createMatrix (int row, int col, int num, matrix& mat);
void freememo(matrix& mat);
void DisplayMenu();


matrix operator+ (matrix mat1, matrix mat2);
matrix operator-  (matrix mat1, matrix mat2);
matrix operator*  (matrix mat1, matrix mat2);
matrix operator+  (matrix mat1, int scalar);
matrix operator-  (matrix mat1, int scalar);
matrix operator*  (matrix mat1, int scalar);


matrix operator+= (matrix& mat1, matrix mat2);
matrix operator-= (matrix& mat1, matrix mat2);
matrix operator+= (matrix& mat, int scalar);
matrix operator-= (matrix& mat, int scalar);
void   operator++ (matrix& mat);
void   operator-- (matrix& mat);
istream& operator>> (istream& in, matrix& mat);


ostream& operator<< (ostream& out, matrix mat);
bool   operator== (matrix mat1, matrix mat2);
bool   operator!= (matrix mat1, matrix mat2);
bool   isSquare   (matrix mat);
bool   isSymetric (matrix mat);
bool   isIdentity (matrix mat);
matrix transpose(matrix mat,matrix matt);



int main()
{
    int data1 [] = {1,2,3,4,5,6,7,8};
    int data2 [] = {13,233,3,4,5,6};
    int data3 [] = {10,100,10,100,10,100,10,100};
    int data4 [] = {1,5,2,1,5,2,7,8,2,7,3,9,1,8,9,4};
    int data5 [] = {1,2,3,4,5,6,7,8};
    int data6 [] = {1,0,0,0,1,0,0,0,1};


    matrix mat1, mat2, mat3,mat4,mat5,mat6;
    createMatrix (4, 2, data1, mat1);
    createMatrix (2, 3, data2, mat2);
    createMatrix (4, 2, data3, mat3);
    createMatrix (4, 4, data4, mat4);
    createMatrix (2, 4, data5, mat5);
    createMatrix (3, 3, data6, mat6);


    int choice;

    cout << "Ahlan ya user ya 7biby!" << endl;
    cout << "What do you want to do?" << endl;
    cout << "1.Display the menu" << endl;
    cout << "2.Display the matrices" << endl;
    cout << "3.Exit" << endl;
    cin >> choice;
    if(choice == 1){DisplayMenu();}
    if(choice == 2){cout << mat1 << endl << endl << mat2 << endl << endl << mat3 << endl << endl <<
     mat4 << endl << endl << mat5 << endl << endl << mat6 << endl << endl;}
    if(choice == 3){return 0;}


    freememo(mat1);
    freememo(mat2);
    freememo(mat3);
    freememo(mat4);
    freememo(mat5);
    freememo(mat6);
    //freememo(matt);
    return 0;
}

void DisplayMenu(){
    int choicee;
    int scalar;
    int dataa[16];
    string matName,mat1Name,mat2Name;

    int data1 [] = {1,2,3,4,5,6,7,8};
    int data2 [] = {13,233,3,4,5,6};
    int data3 [] = {10,100,10,100,10,100,10,100};
    int data4 [] = {1,5,2,1,5,2,7,8,2,7,3,9,1,8,9,4};
    int data5 [] = {1,2,3,4,5,6,7,8};
    int data6 [] = {1,0,0,0,1,0,0,0,1};


    matrix mat1, mat2, mat3,mat4,mat5,mat6,matt,matTranspose;
    createMatrix (4, 2, data1, mat1);
    createMatrix (2, 3, data2, mat2);
    createMatrix (4, 2, data3, mat3);
    createMatrix (4, 4, data4, mat4);
    createMatrix (2, 4, data5, mat5);
    createMatrix (3, 3, data6, mat6);

    cout << "1.Add two matrices" << endl;
    cout << "2.Subtract two matrices" << endl;
    cout << "3.Multiply two matrices" << endl;
    cout << "4.Add a matrix with a scalar" << endl;
    cout << "5.Subtract a matrix with a scalar" << endl;
    cout << "6.Multiply a matrix with a scalar" << endl;
    cout << "7.Add two matrices and put the result in one of them" << endl;
    cout << "8.Subtract two matrices and put the result in one of them" << endl;
    cout << "9.Add a matrix with a scalar and put the result in the same matrix" << endl;
    cout << "10.Subtract a matrix with a scalar and put the result in the same matrix" << endl;
    cout << "11.Add 1 to each element of the matrix" << endl;
    cout << "12.Subtract 1 from each element of the matrix" << endl;
    cout << "13.Input a matrix" << endl;
    cout << "14.Output a matrix" << endl;
    cout << "15.Check if two matrices are equal" << endl;
    cout << "16.Check if two matrices are not equal" << endl;
    cout << "17.Check if a matrix is a square matrix" << endl;
    cout << "18.Check if a matrix is symmetric" << endl;
    cout << "19.Check if a matrix is an identity matrix" << endl;
    cout << "20.Transpose a matrix" << endl;

    cin >> choicee;

    if(choicee == 1){cout << (mat1+mat3) << endl;}
    if(choicee == 2){cout << (mat3-mat1) << endl;}
    if(choicee == 3){cout << (mat1*mat5) << endl;}
    if(choicee == 4){
            cout << "Enter a scalar" << endl;
            cin >> scalar;
            cout << (mat2+scalar) << endl;}
    if(choicee == 5){
            cout << "Enter a scalar" << endl;
            cin >> scalar;
            cout << (mat2-scalar) << endl;}
    if(choicee == 6){
            cout << "Enter a scalar" << endl;
            cin >> scalar;
            cout << (mat2*scalar) << endl;}
    if(choicee == 7){cout << (mat1+=mat3) << endl;}
    if(choicee == 8){cout << (mat3-=mat1) << endl;}
    if(choicee == 9){
            cout << "Enter a scalar" << endl;
            cin >> scalar;
            cout << (mat2+=scalar) << endl;}
    if(choicee == 10){
            cout << "Enter a scalar" << endl;
            cin >> scalar;
            cout << (mat2-=scalar) << endl;}
    if(choicee == 11){++mat1; cout << mat1 << endl;}
    if(choicee == 12){--mat2; cout << mat2 << endl;}
    if(choicee == 13){
        cout << "Enter the data inside a 4*4 matrix separated by a space" << endl;
        for(int i=0; i<16; i++){
        cin >> dataa[i];}
        createMatrix(4, 4, dataa, matt);
        cout << matt << endl;
    }
    if(choicee == 14){
        cout << "which matrix do you want to see? \n mat1,mat2,mat3,mat4 or mat5?" << endl;
        cin >> matName;
        cout << matName;
    }
    if(choicee == 15){
        cout << "which two matrices you want to check if they are equal?" << endl;
        cin >> mat1Name >> mat2Name;
        if(mat1Name==mat2Name){cout << "The two matrices are EQUAL!" << endl;}
        else {cout << "The matrices are NOT EQUAL!!" << endl;}
    }
     if(choicee == 16){
        cout << "which two matrices you want to check if they are not equal?" << endl;
        cin >> mat1Name >> mat2Name;
        if(mat1Name!=mat2Name){cout << "The two matrices are NOT EQUAL!" << endl;}
        else {cout << "The matrices are EQUAL!!" << endl;}
    }
    if(choicee == 17){
        if(isSquare(mat4)==1){cout << "The matrix is a SQUARE matrix" << endl;}
        else{cout << "The matrix is NOT a SQUARE matrix" << endl;}
    }
    if(choicee == 18){
        if(isSymetric(mat4)==1){cout << "The matrix is SYMMETRIC" << endl;}
        else{cout << "The matrix is NOT SYMMETRIC" << endl;}
    }
    if(choicee == 19){
        if(isIdentity(mat6)==1){cout << "The matrix is an IDENTITY matrix" << endl;}
        else{cout << "The matrix is NOT an IDENTITY matrix" << endl;}
    }
    if(choicee == 20){
        transpose(mat5,matTranspose);
    }
    freememo(matt);
}

//The following function creates a matrix by passing to it the number of rows & columns and the data which will fill the matrix
//and the reference of the matrix

void createMatrix (int row, int col, int num[], matrix& mat){
    mat.row = row;
    mat.col = col;
    mat.data = new int* [row];

    for (int i = 0; i < row; i++)
        mat.data[i] = new int [col];

    for (int i = 0; i < row; i++)
        for (int j = 0; j < col; j++)
            mat.data[i][j] = num[i * col + j];
}

//The following function creates a matrix by passing to it the number of rows & columns and a number to fill the matrix with
//and the reference of the matrix

void createMatrix (int row, int col, int num, matrix& mat)
{
    mat.row = row;
    mat.col = col;
    num=0;
    mat.data = new int* [row];

    for (int i = 0; i < row; i++)
        mat.data[i] = new int [col];

    for (int i = 0; i < row; i++)
        for (int j = 0; j < col; j++)
            mat.data[i][j] = num;
}

//This function is to free the memory that has been used by matrices & it only takes the matrix

void freememo(matrix& mat)
{
    for(int i=0; i<mat.row; i++)
    {
        delete[] mat.data[i];
    }
    delete[] mat.data;
}

//This function adds two matrices and puts the result in a new matrix & its parameters are the two matrices

matrix operator + (matrix mat1, matrix mat2)
{
    matrix addition;
    createMatrix(mat1.row,mat1.col,0,addition);

    if ( mat1.row == mat2.row && mat1.col == mat2.col)
    {
        for( int i = 0; i < mat1.row; i++)
        {
            for( int j = 0; j < mat1.col; j++)
            {
                addition.data[i][j]=mat1.data[i][j]+mat2.data[i][j];
            }
        }
    }
    else
    {
        cout << "We can't add them as they don't have the same dimensions" <<endl;
    }
    return addition;
}

//This function subtracts two matrices and puts the result in a new matrix & its parameters are the two matrices

matrix operator - (matrix mat1, matrix mat2)
{

    matrix subtraction;
    createMatrix(mat1.row,mat1.col,0,subtraction);

    subtraction.row=mat1.row;
    subtraction.col=mat1.col;

    if ( mat1.row == mat2.row && mat1.col == mat2.col)
    {
        for( int i = 0; i < mat1.row; i++)
        {
            for( int j = 0; j < mat1.col; j++)
            {
                subtraction.data[i][j]=mat1.data[i][j]-mat2.data[i][j];
            }
        }
    }
    else
    {
        cout << "We can't subtract them as they don't have the same dimensions" <<endl;
    }
    return subtraction;
}

//This function multiply two matrices and puts the result in a new matrix & its parameters are the two matrices
matrix operator * (matrix mat1, matrix mat2)
{

    matrix multiplication;
    createMatrix(mat1.row,mat1.col,0,multiplication);

    if ( mat1.col == mat2.row )
    {
            for(int i = 0; i < mat1.row; ++i)
                for(int j = 0; j < mat2.col; ++j)
                {
                    multiplication.data[i][j]=0;
                }

        for(int i = 0; i < mat1.row; ++i)
            for(int j = 0; j < mat2.col; ++j)
                for(int k = 0; k < mat1.col; ++k)
                {
                    multiplication.data[i][j] += mat1.data[i][k] * mat2.data[k][j];
                }

      cout << endl << "Output Matrix: " << endl;
        for(int i = 0; i < mat1.row; ++i)
            for(int j = 0; j < mat2.col; ++j)
            {
                cout << " " << multiplication.data[i][j];
                if( j == mat2.col-1)
                    cout << endl;
            }
    }
    else
    {
        cout << "We can't multiply them as col1 not equal row2" <<endl;
    }
    return multiplication;
   }

//This function adds a matrix with a scalar and puts the result in a new matrix
//It's parameters are the matrix and the scalar

matrix operator + (matrix mat1, int scalar)
{

    matrix add;
    createMatrix(mat1.row,mat1.col,0,add);

    for ( int i = 0; i < mat1.row; i++)
    {
        for ( int j = 0; j < mat1.col; j++)
        {
            add.data[i][j] = mat1.data[i][j]+scalar;
        }
    }
    return add;
}

//This function subtracts a scalar from a matrix and puts the result in a new matrix
//It's parameters are the matrix and the scalar

matrix operator - (matrix mat1, int scalar)
{

    matrix sub;
    createMatrix(mat1.row,mat1.col,0,sub);

    for ( int i = 0; i < mat1.row; i++)
    {
        for ( int j = 0; j < mat1.col; j++)
        {
            sub.data[i][j] = mat1.data[i][j]-scalar;
        }
    }
    return sub;
}

//This function multiply a scalar by a matrix and puts the result in a new matrix
//It's parameters are the matrix and the scalar

matrix operator * (matrix mat1, int scalar)
{

    matrix multi;
    createMatrix(mat1.row,mat1.col,0,multi);

    for ( int i = 0; i < mat1.row; i++)
    {
        for ( int j = 0; j < mat1.col; j++)
        {
            multi.data[i][j] = mat1.data[i][j]*scalar;
        }
    }
    return multi;
}

//This function adds two matrices and puts the result in the first matrix
//It's parameters are two matrices

matrix operator+= (matrix& mat1, matrix mat2)
{

    for (int i=0; i<mat1.row; i++)
    {
        for(int j=0; j<mat1.col; j++)
        {
            mat1.data[i][j]=mat1.data[i][j]+mat2.data[i][j];

        }
    }
    return mat1;
}

//This function subtracts two matrices and puts the result in the first matrix
//It's parameters are two matrices

matrix operator-= (matrix& mat1, matrix mat2)
{

    for (int i=0; i<mat1.row; i++)
    {
        for(int j=0; j<mat1.col; j++)
        {
            mat1.data[i][j]=mat1.data[i][j]-mat2.data[i][j];

        }
    }
    return mat1;
}

//This function adds a scalar to a matrix and puts the result in the same matrix
//It's parameters are a scalar and a matrix

matrix operator+= (matrix& mat, int scalar)
{


    for(int i=0; i<mat.row; i++)
    {
        for(int j=0; j<mat.col; j++)
        {
            mat.data[i][j]=mat.data[i][j]+scalar;
        }
    }


    return mat;
}

//This function subtracts a scalar from a matrix and puts the result in the same matrix
//It's parameters are a scalar and a matrix

matrix operator-= (matrix& mat, int scalar)
{

    for(int i=0; i<mat.row; i++)
    {
        for(int j=0; j<mat.col; j++)
        {
            mat.data[i][j]=mat.data[i][j]-scalar;
        }
    }


    return mat;

}

//This function adds 1 to all the values inside the matrix
//It's only parameter is the matrix

void   operator++ (matrix& mat)
{


    for(int i=0; i<mat.row; i++)
    {
        for(int j=0; j<mat.col; j++)
        {
            //mat.data[i][j]=++mat.data[i][j];
            ++mat.data[i][j];
        }
    }

}

//This function subtracts 1 from all the values inside the matrix
//It's only parameter is the matrix

void   operator-- (matrix& mat)
{

    for(int i=0; i<mat.row; i++)
    {
        for(int j=0; j<mat.col; j++)
        {
           // mat.data[i][j]=--mat.data[i][j];
            --mat.data[i][j];
        }
    }
}

//This function is made to declare the in operator to take data from a user or file
//It's parameters are the istream & the matrix

istream& operator>> (istream& in, matrix& mat)
{
    for(int i=0; i<mat.row; i++)
    {
        for(int j=0; j<mat.col; j++)
        {
            in >> mat.data[i][j];
        }
    }
    return in;
}

//This function is made to declare the out operator to output data to the console window or to a file
//It's parameters are the ostream & the matrix

ostream& operator<< (ostream& out, matrix mat)
{
    for(int i=0; i<mat.row; i++)
    {
        for(int j=0; j<mat.col; j++)
        {
            out << setw(6) << mat.data[i][j] << setw(6);
        }
        out << endl;
    }
    return out;
}

//This function checks if a matrix is a square matrix(# of rows==#of columns) or not
//It's only parameter is the matrix

bool   isSquare   (matrix mat)
{
    bool check=true;
    if(mat.row!=mat.col)
    {
        check=false;
    }
    return check;
}

//This function checks if a matrix is symmetric or not
//It's only parameter is the matrix

bool   isSymetric (matrix mat){
    bool check=false;
    int counter=0;
    if(isSquare(mat)==1){
        for(int i=0;i<mat.row;i++){
            for(int j=0;j<mat.col;j++){
                if(i != j && mat.data[i][j]==mat.data[j][i]){counter++;}
        }
    }
    if(counter==(mat.row*mat.col - mat.row)){check=true;}
        }
    else{check=false;}
    return check;
}

//This function checks if a matrix is an identity matrix(all elements in matrix are 1's) or not
//It's only parameter is the matrix

bool   isIdentity (matrix mat)
{
    bool check=false;
    int counter1=0,counter2=0;
    if(isSquare(mat)==1)
        for(int i=0; i<mat.row; i++)
        {
            for(int j=0; j<mat.col; j++)
            {
                if(i==j && mat.data[i][j]==1)
                {
                    counter1+=1;
                }
                else
                {
                    counter1=counter1;
                }
                if (i!=j && mat.data[i][j]==0)
                {
                    counter2+=1;
                }
                else
                {
                    counter2=counter2;
                }
                if(counter1==mat.row && counter2==(mat.row*(mat.row-1)))
                {
                    check=true;
                }

            }
        }

    return check;
}

//This function checks if two matrices are identical(equal) or not
//It's parameters are the two matrices

bool   operator== (matrix mat1, matrix mat2)
{
    bool check=true;
    if(mat1.row==mat2.row && mat1.col==mat2.col)
    {
        for(int i=0 ; i<mat1.row ; i++)
        {
            for(int j=0 ; j<mat1.col ; j++ )
            {
                if(mat1.data[i][j]!=mat2.data[i][j])
                {
                    check=false;

                }
            }
        }
    }
    return check;
}

//This function checks if two matrices are not equal or not
//It's parameters are the two matrices

bool   operator!= (matrix mat1, matrix mat2)
{
    bool check=false;
    if(mat1.row != mat2.row || mat1.col != mat2.col)
    {
        check=true;
    }
    else
    {
        for(int i=0; i<mat1.row; i++)
        {
            for(int j=0; j<mat1.col; j++)
            {
                if(mat1.data[i][j] != mat2.data[i][j])
                {
                    check=true;
                }
                else
                {
                    check=false;
                }
            }
        }
    }
    // cout << check << " " << endl;
    return check;
}

//This function gets the transpose of a matrix
//It's parameters are the old matrix and an empty newmatrix to put the transpose of the old matrix in it

matrix transpose(matrix mat,matrix matt){
    createMatrix(mat.col,mat.row,0,matt);
    for(int i=0; i<matt.row; i++)
    {
        for(int j=0; j<matt.col; j++)
        {
            matt.data[i][j]=mat.data[j][i];
        }
    }
    cout << matt << endl;
    return matt;
}
