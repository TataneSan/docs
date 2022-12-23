# Algorithme
Prenons un exemple :

22 = 16 + 4 + 2 = 1*2^4 + 0*2^3 + 1*2^2 + 1*2^1 + 0*2^0
ce qui donne en binaire :

10110
Méthode "intuitive"
On réutilise la solution de l'exercice précédent. Une fois qu'on a trouvé la première puissance de 2, on affiche un 1, puis on retire cette puissance à notre nombre. On divise ensuite la puissance de 2 par 2. Si le résultat est plus grand que le nombre restant, on affiche un 1, sinon on affiche 0. On recommence ainsi jusqu'à arriver à une puissance de 2 égale à 0.

Pour s'assurer d'afficher au moins un chiffre, même si le nombre initial vaut 0, on doit éviter d'avoir une puissance de 2 égale à 0 dès le départ. On peut le faire en initialisant notre puissance à 2, et non à 1 comme dans l'exercice précédent.

Méthode "mathématique"
Reprenons l'exemple :

22 = 16 + 4 + 2 = 1*2^4 + 0*2^3 + 1*2^2 + 1*2^1 + 0*2^0 
                = 2*(1*2^3 + 0*2^2 + 1*2^1 + 1*2^0) + 0*2^0
                = 2*11 + 0
Le chiffre des unités de la décomposition binaire de 22 est le reste de la division euclidienne de 22 par 2 et les autres chiffres sont ceux de l'écriture binaire de 11, le quotient de la division euclidienne. On obtient ainsi naturellement un algorithme récursif (un chapitre entier est consacré à la récursivité donc nous ne donnerons pas tous les détails) :

> Fonction afficherBinaire(nombre)
   Si nombre <=1 alors
      Afficher(nombre)
   sinon
      afficherBinaire(nombre / 2)
      Afficher(nombre modulo 2)
On peut alors remarquer que si nombre <= 1 alors nombre et nombre modulo 2 sont égaux. Donc on peut écrire :

> Fonction afficherBinaire(nombre)
   Si nombre <= 1 alors
      Afficher(nombre modulo 2)
   sinon
      afficherBinaire(nombre / 2)
      Afficher(nombre modulo 2)
qui se simplifie en :

> Fonction afficherBinaire(nombre)
   Si nombre > 1
      alors afficherBinaire(nombre / 2)
   Afficher(nombre modulo 2)
que l'on peut aussi écrire de façon itérative en dressant dans un tableau la liste des chiffres à afficher :

> MAX_CHIFFRES <- 32
chiffresBinaires <- tableau de taille MAX_CHIFFRES
nombre <- lireEntier()
 
> iChiffre <- 0
Tant que (iChiffre = 0) ou (nombre > 0) faire
   chiffresBinaires[iChiffre] <- nombre modulo 2
   nombre <- nombre / 2
   iChiffre <- iChiffre + 1
 
> Tant que iChiffre > 0
   iChiffre <- iChiffre - 1
   Afficher(chiffresBinaires[iChiffre])


# Le programme :

## En python :

```py

nombre = int(input())
puissanceDe2 = 2
while puissanceDe2 <= nombre:
   puissanceDe2 = puissanceDe2 * 2
puissanceDe2 = puissanceDe2 // 2
while puissanceDe2 > 0:
   if puissanceDe2 <= nombre:
      print("1",end="")
      nombre = nombre - puissanceDe2
   else:
      print("0",end="")
   puissanceDe2 = puissanceDe2 // 2
print("")
```
### En récursif :

```py
def afficherBinaire(nombre):
   if nombre > 1:
      afficherBinaire(nombre // 2)
   print(nombre % 2,end="")
      
nombre = int(input())
afficherBinaire(nombre)
```

### Avec un programme itératif

```py
MAX_CHIFFRES = 32
nombre = int(input())
chiffresBinaires = [0] * MAX_CHIFFRES
iChiffre = 0
while (iChiffre == 0) or (nombre > 0):
   chiffresBinaires[iChiffre] = nombre % 2
   nombre = nombre // 2
   iChiffre = iChiffre + 1
while iChiffre > 0:
   iChiffre = iChiffre - 1
   print(chiffresBinaires[iChiffre],end="")
print()
```

## En Java :

```java
import algorea.Scanner;
class Main
{
   public static void main(String[] args)
   {
      Scanner entrée = new Scanner(System.in);
      int nombre = entrée.nextInt();
      
      int puissanceDe2 = 2;
      while (puissanceDe2 <= nombre)
         puissanceDe2 = puissanceDe2 * 2;
      puissanceDe2 = puissanceDe2 / 2;
        
      while (puissanceDe2 > 0)
      {
         if (puissanceDe2 <= nombre)
         {
            System.out.print("1");
            nombre = nombre - puissanceDe2;
         }
         else
            System.out.print("0");
         puissanceDe2 = puissanceDe2 / 2;
      }
   }
}
```
