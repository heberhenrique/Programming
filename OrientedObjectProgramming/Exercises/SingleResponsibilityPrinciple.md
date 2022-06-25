# Turma 854 - POO 2 - SRP

## Exercício de Fixação

Dado o sistema Let's Pet realize o desacoplamento das telas que cada módulo do sisteme utiliza de forma que fiquem em uma classe como o exemplo a seguir:


```csharp
public static class PrintAnimal
	{
		public static void PrintPet(Animal animal)
		{
            var response = $@"
---------- IMPRIMINDO PET ----------
Nome: {animal.Name}
Espécie: {animal.Species}
Raça: {animal.Breed}
Cor: {animal.Color}
Porte: {animal.BreedSize}
Peso: {animal.Weight}
Nascimento: {animal.BirthDate}
Idade: {animal.Age}
Sexo: {animal.Gender}
Castrado: {(animal.Castrated ? "SIM" : "NÃO")}

";

            // TODO: transformar o restante das classes que contém algum Console.Write conforme exemplo acima
            //string IsCastratedBool(Animal animal) => animal.Castrated ? "SIM" : "NÃO";

            //Console.Write($"Agressivo: ");
            //if (AggressiveBool)
            //    Console.WriteLine("SIM");
            //else
            //    Console.WriteLine("NÃO");


            //if (DiseasesBool)
            //{
            //    Console.WriteLine("Doenças do pet:");
            //    foreach (string disease in DiseasesList)
            //        Console.WriteLine(disease);
            //}
            //else
            //    Console.WriteLine("O pet não possui nenhuma doença");


            //if (AllergiesBool)
            //{
            //    Console.WriteLine("Alergias do pet:");
            //    foreach (string allergie in AllergiesList)
            //        Console.WriteLine(allergie);
            //}
            //else
            //    Console.WriteLine("O pet não possui nenhuma alergia");


            //if (PhysicalDisabilityBool)
            //{
            //    Console.WriteLine("Deficiências físicas do pet:");
            //    foreach (string deficiencia in PhysicalDisabilityList)
            //        Console.WriteLine(deficiencia);
            //}
            //else
            //    Console.WriteLine("O pet não possui nenhuma deficiência física");

            //Console.WriteLine("CARTEIRA DE VACINAÇÃO DO PET:");
            //foreach (PetVaccine vacina in PetVaccineList)
            //    Console.WriteLine(vacina);

            //Console.WriteLine($"Data de cadastro: {RegistrationDate}");
            //Console.WriteLine();
        }
	}
```

Para a resposta escreva o nome do arquivo que voce subiu.