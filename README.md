# II_2023_24_P2_Introducci-n_a_C-_Scripts
## Introducción
El objetivo de la práctica es poner en práctica lo aprendido respecto a la programación en C#. Haciendo para ello los siguientes ejercicios con sus scripts respectivos.

## Ejercicios de la práctica
### Ejercicio 1
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio1 : MonoBehaviour
{
    public int inferior_limit = 0;
    public int superior_limit = 25;
    int size = 10;
    int[] vector;

    // Start is called before the first frame update
    void Start()
    {
        vector = new int[size];
        for (int i = 0; i < size; ++i) {
            vector[i] = Random.Range(inferior_limit, superior_limit);
        }
    }

    // Update is called once per frame
    void Update()
    {
        for (int i = 0; i < size; ++i) {
            if (vector[i] >= 15) {
              Debug.Log(vector[i]);
            }
        }
        int first_rand_position = Random.Range(0, size);
        int second_rand_position = Random.Range(0, size);
        while (first_rand_position == second_rand_position) {
            second_rand_position = Random.Range(0, size);
        }
        int change = vector[first_rand_position];
        vector[first_rand_position] = vector[second_rand_position];
        vector[second_rand_position] = change;
    }
}
```

