# Algorithme
On écrit une fonction qui se charge d'afficher un nombre en binaire. On peut ensuite l'appeler dans deux boucles imbriquées qui parcourent la table.

# Le programme

nbLignes <- LireEntier()
Fonction afficherBinaire(nombre)
   Si nombre > 1
      alors afficherBinaire(nombre / 2)
   Afficher(nombre modulo 2)
Pour ligne dans [0; nbLignes[ faire
   Pour colonne dans [0; nbLignes[ faire
      AfficherBinaire(ligne * colonne)
      Afficher("\t")
   Afficher("\n")

## En python :

```py
def afficherBinaire(nombre):
   if nombre > 1:
      afficherBinaire(nombre // 2)
   print(nombre % 2,end="")
nbColonnes = int(input())
for ligne in range(1, nbColonnes + 1):
   for colonne in range(1, nbColonnes + 1):
      afficherBinaire(ligne*colonne)
      print("\t",end="")
   print()
```

## En C :

```C
#include <stdio.h>
void afficheBinaire(int nombre)
{
   int puissanceDe2 = 2;
   while (puissanceDe2 <= nombre)
      puissanceDe2 *= 2;
   while (puissanceDe2 > 1)
   {
      if (nombre % puissanceDe2  >= puissanceDe2 / 2)
         printf("1");
      else
         printf("0");
      puissanceDe2 /= 2;
   }
}
int main()
{
   int nbLignes;
   int ligneActuelle = 1;
   scanf("%d", &nbLignes);
   while (ligneActuelle <= nbLignes)
   {
      int colonneActuelle = 1;
      while (colonneActuelle <= nbLignes)
      {
         afficheBinaire(colonneActuelle * ligneActuelle);
         if (colonneActuelle != nbLignes)
            printf("\t");
         colonneActuelle++;
      }
      printf("\n");
      ligneActuelle++;
   }
   return 0;
}
```

## En Java :

```java
import algorea.Scanner;
class Main
{
   public static void main(String[] args)
   {
      Scanner entrée = new Scanner(System.in);
      int nbColonnes = entrée.nextInt();
      for (int ligne = 1; ligne <= nbColonnes; ligne++)
      {
         for (int colonne = 1; colonne <= nbColonnes; colonne++)
         {
            afficherBinaire(ligne*colonne);
            System.out.print("\t");
         }
         System.out.println();
      }
   }
   static void afficherBinaire(int nombre)
   {
      if (nombre > 1)
         afficherBinaire(nombre / 2);
      System.out.print(nombre % 2);
   }
}
```

