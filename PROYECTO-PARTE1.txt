#include <stdio.h>
#include <stdlib.h>


/* Inicialización de variables */
int opcion = 0;
int largodecadena = 0;
char caracteracomparar[100];
char cadena1[100];//array de caracteres (cadena)


void mostrarMenu()//MENU
{
    printf("\n");
    printf(" 1 - Ingresar una cadena \n");
    printf(" 2 - Largo de una cadena \n");
    printf(" 3 - Concatenar dos cadenas \n");
    printf(" 4 - Mostrar una cadena \n");
    printf(" 5 - Ocurrencias de un caracter en una cadena \n");
    printf(" 6 - Sustituir un caracter en una cadena \n");
    printf(" 7 - Eliminar un caracter en una cadena \n");
    printf(" 8 - Informa si se encuentra o no, un caracter en una cadena \n");
    printf(" 9 - Posicion de un caracter en una cadena  \n");
    printf(" 0 - Salir \n");
    printf("---------------------------------------------\n");
    printf("    Ingrese opcion : ");
}

void reinicioMenu()//Limpia la consola
{
if (opcion!=0) system("PAUSE");
system("CLS");
}

int getLargoCadena()//Largo de la cadena 1
{
    largodecadena=0;
    while (cadena1[largodecadena]!='\0') largodecadena++;
    return largodecadena;
}

/* === OPCIONES === */

void cargarCadena()//1 - Ingresar una cadena
{
    int recorredordecadena1 = 0;
    for (recorredordecadena1=0; cadena1[recorredordecadena1]!='\0'; recorredordecadena1++)
    {
        cadena1[recorredordecadena1] = 0;
    }
    printf("    Ingrese texto: ");
    scanf("%s", cadena1);
    printf("\n    Texto ingresado: %s \n", cadena1);
}

void largoCadena()//2 - Largo de una cadena
{
    getLargoCadena();
    if (largodecadena>0)
    {
        printf("    El largo de la cadena es de %d \n", largodecadena);
    }
    else
    {
        printf("    No se ha ingresado una cadena \n");
    }
}

void concatenar()//3 - Concatenar cadenas
{
    int largo = 0;
    int recorredorcadena2=0;
    char cadena2[100];
    getLargoCadena();
    if (largodecadena>0)
    {
        largo = largodecadena;
        printf("    Ingrese una segunda cadena: ");  //ingresar una cadena
        scanf("%s", cadena2);
        for (recorredorcadena2=0; cadena2[recorredorcadena2]!='\0'; recorredorcadena2++, largo++)
        {
            cadena1[largo]=cadena2[recorredorcadena2];
        }
        printf("    El resultado de concatenar ambas cadenas es el siguiente  : %s \n", cadena1);
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }
}

void desplegar()//4 - Desplegar una cadena
{
    int largo=0;
    getLargoCadena();
    if (largodecadena>0)
    {
        for (largo=0; cadena1[largo]!='\0'; largo++)
        {
            printf("    Posicion nro %i: %c \n", largo, cadena1[largo]);
        }
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }

}

void cantidad()//5 - Dado un caracter devuelve la cantidad de coincidencias
{
    int coincidencias=0;
    getLargoCadena();
    if (largodecadena>0)
    {
        printf("    Ingrese un caracter : ");
        scanf("%1s", caracteracomparar);
        for (int contador2=0; cadena1[contador2]; contador2++)
        {
            if (caracteracomparar[0]==cadena1[contador2])
            {
                coincidencias++;
            }
        }
        if (coincidencias>0)
        {
            printf("    Se detectaron %i coincidencias \n", coincidencias);
        }
        else
        {
            printf("    No se detectaron coincidencias \n", coincidencias);
        }
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }
}

void remplazarLetras()//6 - Remplazar un caracter
{
    char caracteracomparar2[100];
    if (largodecadena>0)
    {
        printf("    Ingrese un caracter a remplazar : ");
        scanf(" %1s", caracteracomparar);
        printf("\n");
        printf("    Ingrese el caracter que remplazara al anterior : ");
        scanf(" %1s", caracteracomparar2);
        for (int contador2=0; cadena1[contador2]; contador2++)
        {
            if (caracteracomparar[0]==cadena1[contador2])
            {
                cadena1[contador2]=caracteracomparar2[0];
            }
        }
        printf("La cadena luego de ser remplazada : %s \n", cadena1);
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }
}

void eliminarLetra()//7 - Eliminar letra
{
    getLargoCadena();
    char cadenapostremplazo[100];
    if (largodecadena>0)
    {
        int recorredorpostremplazo=0;
        printf("    Ingrese el caracter a eliminar: ");
        scanf(" %1s", caracteracomparar);
        for (int recorredor=0; cadena1[recorredor]!='\0'; recorredor++)
        {
            if (cadena1[recorredor]!=caracteracomparar[0])
            {

                cadenapostremplazo[recorredorpostremplazo]=cadena1[recorredor];
                recorredorpostremplazo++;
            }
        }
        printf("    La cadena con el caracter eliminado es : %s \n", cadenapostremplazo);
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }
}

void pertenece() // 8 - pertenece
{
    getLargoCadena();
    if (largodecadena>0)
    {
        int cant=0;
        int i=0;
        char letra[2];
        printf("    Digite una letra para verificar si pertenece a la cadena: ");
        scanf("%1s",letra);
        while(cadena1[i] != '\0')
        {
          if(cadena1[i] == letra[0])
        {
           cant++;
        }
           i++;
        }
        if(cant>=1)
           printf("    El caracter %c pertenece a la cadena \n ", letra[0]);
        else
           printf("    El caracter %c NO pertenece a la cadena \n ", letra[0]);
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }
}

void posicion() // 9- posicion
{
    char letra[2];
    int contador=0;
    int posiciones[100];
    getLargoCadena();
    if (largodecadena>0)
    {
        printf("    Ingrese el caracter a buscar en la cadena:  ");
        scanf("%1s", letra);
        for(int i=0;cadena1[i];i++)
        {
            if(letra[0]==cadena1[i])
            {
                posiciones[contador] = i;
                contador++;

                /*
                printf("La letra %c se encuentra en la posicion %d\n", letra,i);
                cont++;
                */
            }
        }
        if (contador==1)
        {
            printf("    El caracter se encuentra en la posicion: %i \n", posiciones[0]+1);//Esto es debido a que a nivel interno, empezamos desde la posición 0, mientras que el usuario cuando vea la cadena de caracteres va a interpretar que empieza desde la posición 1
        }
        else
        {
            if (contador>1)
            {
                printf("    El caracter se encuentra en las siguientes posiciones: \n");
                for (int i=0; i<contador; i++)
                {
                    printf("    %i \n", posiciones[i]);
                }
            }
            else
            {
                printf("    El caracter no se encuentra en la cadena: \n");
            }
        }
    }
    else
    {
        printf("    No se ha ingresado la primer cadena, por favor utilice la opcion 1 \n");
    }
}

int main()
{
	do
    {
		mostrarMenu();
		scanf("%d", &opcion);
		for (int i=1; i<2;i++) printf ("\n");
        switch (opcion)
	    {
            case 1:
                cargarCadena();
                break;

            case 2:
                largoCadena();
                break;
            case 3:
                concatenar();
                break;

            case 4:
                desplegar();
                break;
	        case 5:
                cantidad();		//contar
                break;
	        case 6:
                remplazarLetras();
                break;
	        case 7:
                eliminarLetra();	//problema del agujero
                break;
	        case 8:
                    pertenece();	//buscar “Letra”, devuelve un boolean
	                break;
            case 9:
                    posicion();		//que pasa si se repite la letra
                    break;
            default:
                    printf ("\n");
                    printf ("--------- Error, verifique  ------------------- \n");
        }           printf("-------------------------------------------------\n");

        reinicioMenu();
	}while (opcion != 0);
    return 0;
}
