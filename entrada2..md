### 1. Preparació de l'entorn

He utilitzat **Visual Studio Code** com a editor principal. Per poder treballar amb C#, he hagut d'instal·lar el **.NET SDK** al meu sistema i l'extensió oficial **C# Dev Kit** dins de VSCode. Això em permet compilar i executar el codi directament des de la terminal de l'editor.

### 2. Creació del Projecte

He creat un projecte de tipus "Console Application" mitjançant el comandament `dotnet new console`. Aquesta estructura és la base estàndard per a programes senzills que s'executen per línia de comandaments.

### 3. El Codi Font

L'algorisme es basa en el càlcul del mòdul 23 del número del DNI. El resultat d'aquest residu ens indica la posició de la lletra dins d'una cadena de caràcters predefinida oficialment.

C#

```
using System;

namespace CalculadoraDNI
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("=== GENERADOR DE LLETRA DNI ESPANYOL ===");
            Console.Write("Introdueix el número del teu DNI (8 xifres): ");
            
            string entrada = Console.ReadLine();

            // Validació: comprovem que siguin 8 dígits i que siguin números
            if (entrada.Length == 8 && int.TryParse(entrada, out int numeroDni))
            {
                // L'ordre de les lletres és un estàndard oficial (mòdul 23)
                char[] lletres = { 'T', 'R', 'W', 'A', 'G', 'M', 'Y', 'F', 'P', 'D', 'X', 'B', 'N', 'J', 'Z', 'S', 'Q', 'V', 'H', 'L', 'C', 'K', 'E' };
                
                // Algorisme: El residu de la divisió per 23 ens dóna l'índex de la lletra
                int index = numeroDni % 23;
                char lletraCorresponent = lletres[index];

                Console.ForegroundColor = ConsoleColor.Green;
                Console.WriteLine($"\nResultat: El DNI complet és {entrada}-{lletraCorresponent}");
                Console.ResetColor();
            }
            else
            {
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine("\nError: Has d'introduir un número de exactament 8 xifres (sense lletres).");
                Console.ResetColor();
            }

            Console.WriteLine("\nPrem qualsevol tecla per sortir...");
            Console.ReadKey();
        }
    }
}
```

### 4. Proves i Resultats

Per verificar que el programa funciona correctament, he realitzat diverses proves d'execució:

- **Explicació pre-captura:** En la primera prova s'introdueix un DNI vàlid de 8 xifres per comprovar que el càlcul de la lletra és correcte.
    
- **[Aquí insereix la teva captura de pantalla de la terminal amb un resultat correcte]**
    
- **Explicació post-captura:** Com es pot veure, el programa retorna el DNI complet amb la lletra pintada de color verd.
    
- **Explicació pre-captura:** En la segona prova s'introdueix un text o un número amb una longitud incorrecta per comprovar la validació d'errors.
    
- **[Aquí insereix la teva captura de pantalla del missatge d'error en vermell]**
    
- **Explicació post-captura:** El programa detecta l'entrada invàlida i mostra un missatge d'advertència en vermell sense bloquejar-se.