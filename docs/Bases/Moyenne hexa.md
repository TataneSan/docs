# Algorithme
On crée une fonction qui lit un nombre hexadécimal tapé au clavier et retourne sa valeur, puis une fonction qui affiche en hexadécimal une valeur passée en paramètre. Le programme peut alors s'écrire simplement.

# Le programme : 

CHIFFRES <- "0123456789ABCDEF"
Fonction lireEntier()
   nombre <- 0
   Pour chaque chiffre lu faire
      nombre <- nombre * 16
      Si (chiffre >= '0') et (chiffre <= '9')
         alors nombre <- nombre + entier(chiffre)
         sinon nombre <- nombre + codeASCII(chiffre) - codeASCII('A') + 10
   Retourner nombre
   
Fonction afficherEntier(nombre)
   Si nombre > 15
      alors afficherEntier(nombre / 16)
   Afficher(CHIFFRES[nombre modulo 16])
nbNombres <- lireEntier()
somme <- 0
Répéter nbNombres fois
   somme <- somme + lireEntier()
afficherEntier(somme / nbNombres)

## En python :

```py
CHIFFRES = "0123456789ABCDEF"
def lireEntier():
   nombre = 0
   for chiffre in input():
      nombre = nombre * 16
      if (chiffre >= '0') and (chiffre <= '9'):
         nombre += int(chiffre)
      else:
         nombre += ord(chiffre) - ord('A') + 10
   return nombre
   
def afficherEntier(nombre):
   if nombre > 15:
      afficherEntier(nombre // 16)
   print(CHIFFRES[nombre % 16],end="")
nbNombres = lireEntier()
somme = 0
for loop in range(nbNombres):
   somme += lireEntier()
afficherEntier(somme // nbNombres)
```

## En Java :

```java
import algorea.Scanner;
class Main
{
   static final String CHIFFRES = "0123456789ABCDEF";
   static Scanner input = new Scanner(System.in);
   public static void main(String[] args)
   {
      int nbNombres = lireEntier();
      int somme = 0;
      for (int nombre = 0; nombre < nbNombres; nombre++)
         somme += lireEntier();
      afficherEntier(somme / nbNombres);
   }
   static void afficherEntier(int nombre)
   {
      if (nombre > 15)
         afficherEntier(nombre / 16);
      System.out.print(CHIFFRES.charAt(nombre % 16));
   }
   static int lireEntier()
   {
      char [] chiffres = input.next().toCharArray();
      int nombre = 0;
      for (char chiffre: chiffres)
         if (Character.isDigit(chiffre))
            nombre = nombre * 16 + chiffre - '0';
         else
            nombre = nombre * 16 + chiffre - 'A' + 10;
      return nombre;
   }
}
```
## En C :

```C
#include <stdio.h>
int litNombreHexa()
{
   char caractereLu = '0';
   int total = 0;
   while (caractereLu != '\n')
   {
      scanf("%c", &caractereLu);
      if ((caractereLu >= '0') && (caractereLu <= '9'))
         total = total * 16 + (int)(caractereLu - '0');
      else if ((caractereLu >= 'A') && (caractereLu <= 'F'))
         total = total * 16 + 10 + (int)(caractereLu - 'A');
   }
   return total;
}
void afficheNombreHexa(int nombre)
{
   int puissanceDe16 = 16;
   while (puissanceDe16 <= nombre)
      puissanceDe16 *= 16;
   puissanceDe16 /= 16;
   while (puissanceDe16 > 0)
   {
      int chiffre = (nombre / puissanceDe16) % 16;
      if (chiffre < 10)
         printf("%c", chiffre + '0');
      else
         printf("%c", chiffre - 10 + 'A');
      puissanceDe16 /= 16;
   }
   printf("\n");
}
int main()
{
   int nbValeurs;
   int valeursLues = 0;
   int total = 0;
   nbValeurs = litNombreHexa();
   while (valeursLues < nbValeurs)
   {
      total += litNombreHexa();
      valeursLues++;
   }
   afficheNombreHexa(total / nbValeurs);
   return 0;
}
```

