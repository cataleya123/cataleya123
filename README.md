
#include <iostream>
#include <math.h>
#include "glut.h"


using namespace std;
GLsizei ancho = 600, alto = 600; //Se debe probar para que el usuario los de.
float ejeY = alto / 2, ejeX = ancho / 2;
void pixel(float cx, float cy, float red, float green, float blue)
{

}
void pintaplano(int ex, int ey)
{

for (float i = -ex; i < ex; i++)
{
pixel(1, 0, 1, 1, 1);
}

for (float j = -ey; j < ey; j++)
{
pixel(0, j, 1, 1, 1);
}
}
void Texto1()
{
char msg[] = { 'V','E','N','T','A','_','U','N','O'};
glColor3f(1, 1, 1); //colores del texto

glRasterPos2f(0, 580);

for (int i = 0; i < 11; i++)
{
glutBitmapCharacter(GLUT_BITMAP_TIMES_ROMAN_24, msg[i]);
}

glFlush();
}
void Texto2()
{

}
void plano()
{
Texto1();
pintaplano(ejeX, ejeY);
}
void plano2()
{

}
void menu1(int opc)
{
switch (opc)
{
case 1:
glClear(GL_COLOR_BUFFER_BIT);
glFlush(); //liberacion de memoria
plano();

break;

case 2:
exit(0);
break;

default:
break;
}
}
void menu2(int opc)
{

}
int main(int argc, char* argv[])
{
glutInit(&argc, argv);
glutInitDisplayMode(GLUT_RGBA || GLUT_SINGLE);

//ventana 1
glutInitWindowSize(ancho, alto);
glutInitWindowPosition(0, 0);
int vent1 = glutCreateWindow("Ventana uno");//retorna un dato de tipo numerico entero, para generar una o la otra.

gluOrtho2D(0, ancho, 0, alto);
glutSetWindow(vent1);
glutDisplayFunc(plano);

int variable = glutCreateMenu(menu1);

glutAddMenuEntry("Limpiar", 1);
glutAddMenuEntry("Salir", 2);
glutAttachMenu(GLUT_RIGHT_BUTTON);

//Ventana 2

glutInitWindowSize(ancho, alto);
glutInitWindowPosition(800, 0);
int vent2 = glutCreateWindow("Ventana dos");

gluOrtho2D(0, ancho, 0, alto);
glutSetWindow(vent2);
glutDisplayFunc(plano2);

int variable2 = glutCreateMenu(menu2);
glutAddMenuEntry("Dibujar", 1);

glutAddMenuEntry("Limpiar", 2);

glutAddMenuEntry("Salir", 3);
glutAttachMenu(GLUT_RIGHT_BUTTON);

glutMainLoop();

return 0;
}
