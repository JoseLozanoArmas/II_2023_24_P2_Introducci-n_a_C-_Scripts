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

### Ejercicio 2
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio2 : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {      
        Debug.Log("Soy un objeto llamado " + gameObject.name); 
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

### Ejercicio 3
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio3 : MonoBehaviour
{
    public Vector3 fistVector;
    public Vector3 secondVector;
    // Start is called before the first frame update
    void Start()
    {
        float mangitud_first_vector = fistVector.magnitude;
        float mangitud_second_vector = secondVector.magnitude;
        Debug.Log("La magnitud del primer vector es " + mangitud_first_vector);
        Debug.Log("La magnitud del segundo vector es " + mangitud_second_vector);
        float angle = Vector3.Angle(fistVector, secondVector);
        Debug.Log("El ángulo entre los 2 vectores es " + angle);
        float distanceBetweenVectors = Vector3.Distance(fistVector, secondVector);
        Debug.Log("La distancia entre los vectores es de " + distanceBetweenVectors);
        if (fistVector.y > secondVector.y) {
            Debug.Log("El primer vector está por encima");
        } else if (fistVector.y < secondVector.y) {
            Debug.Log("El segundo vector está por encima");
        } else {
            Debug.Log("Están a la misma altura");
        }
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

### Ejercicio 4
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio4 : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        Debug.Log("La posición de la esfera es " + transform.position);
    }

    // Update is called once per frame
    void Update()
    {

    }
}
```

### Ejercicio 5
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio5 : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        GameObject laesfera = GameObject.FindWithTag("Sphere");
        float distance = Vector3.Distance(transform.position, laesfera.transform.position);
        Debug.Log("Soy el objeto " + gameObject.name + " y estoy a una distancia de " + distance );
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

### Ejercicio 6
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio6 : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        GameObject sphere = GameObject.FindWithTag("Sphere");
        GameObject cube = GameObject.FindWithTag("Cube");
        GameObject cylinder = GameObject.FindWithTag("Cylinder");
        string object_tag = gameObject.tag;
        if (object_tag == cube.tag) {
            Vector3 new_position = transform.position;
            new_position.x = sphere.transform.position.x - 5;
            transform.position = new_position;
        } else if (object_tag == cylinder.tag) {
            Vector3 new_position = transform.position;
            new_position.x = sphere.transform.position.x + 5;
            transform.position = new_position;
        }
    }
}
```

### Ejercicio 7
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio7 : MonoBehaviour
{
    public Material current_material;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.A) == true) {
            Renderer rend = GetComponent<Renderer>();
            rend.material = current_material;
        }
        
    }
}
```

### Ejercicio 8
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ejercicio8 : MonoBehaviour
{
    int size = 3;
    float[] vector;
    public GameObject first_sphere;
    public GameObject second_sphere;
    public GameObject third_sphere;
    public Material current_material;

    // Start is called before the first frame update
    void Start()
    {
        vector = new float[size];
    }

    // Update is called once per frame
    void Update()
    {
        GameObject cube = GameObject.FindWithTag("Cube");
        first_sphere = GameObject.FindWithTag("second_group");
        second_sphere = GameObject.FindWithTag("second_group");
        third_sphere = GameObject.FindWithTag("second_group");
        float distance_with_first = Vector3.Distance(cube.transform.position, first_sphere.transform.position);
        float distance_with_second = Vector3.Distance(cube.transform.position, second_sphere.transform.position);
        float distance_with_third = Vector3.Distance(cube.transform.position, third_sphere.transform.position);
        
        vector[0] = distance_with_first;
        vector[1] = distance_with_second;
        vector[2] = distance_with_third;
        float aux_nearest_distances = distance_with_first;
        if (aux_nearest_distances > distance_with_second) { aux_nearest_distances = distance_with_second; } 
        if (aux_nearest_distances > distance_with_third) { aux_nearest_distances = distance_with_third; }
        float aux_farthest_distance = distance_with_first;
        if (aux_farthest_distance < distance_with_second) { aux_farthest_distance = distance_with_second; } 
        if (aux_farthest_distance < distance_with_third) { aux_farthest_distance = distance_with_third; }
        
        if (aux_nearest_distances == distance_with_first) {
            Vector3 new_position = transform.position;
            new_position.y = cube.transform.position.y + 2;
            first_sphere.transform.position = new_position;
        }
        if (aux_nearest_distances == distance_with_second) {
            if (aux_nearest_distances == distance_with_first) {
                Vector3 new_position = transform.position;
                new_position.y = cube.transform.position.y + 2;
                second_sphere.transform.position = new_position;
            }
        }
        if (aux_nearest_distances == distance_with_third) {
            if (aux_nearest_distances == distance_with_first) {
                Vector3 new_position = transform.position;
                new_position.y = cube.transform.position.y + 2;
                third_sphere.transform.position = new_position;
            }
        }

        if (aux_farthest_distance == distance_with_first) {
            if (Input.GetKeyDown(KeyCode.Space) == true) {
               Renderer rend = first_sphere.GetComponent<Renderer>();
               rend.material = current_material;
            }
        }
        if (aux_farthest_distance == distance_with_second) {
            if (Input.GetKeyDown(KeyCode.Space) == true) {
               Renderer rend = second_sphere.GetComponent<Renderer>();
               rend.material = current_material;
            }
        }
        if (aux_farthest_distance == distance_with_third) {
            if (Input.GetKeyDown(KeyCode.Space) == true) {
               Renderer rend = third_sphere.GetComponent<Renderer>();
               rend.material = current_material;
            }
        }
    }
}

```

## Gifs con las demostraciones
A continuación se adjunta un gif con la escena realizada. En este caso el ejercicio 1 y 2

![Visualización de la escena Ej 1 y 2]

Luego los ejercicios 3, 4 y 5
![Visualización de la escena Ej 3, 4 y 5]

Y finalmente los ejercicios 6, 7 y 8 
![Visualización de la escena Ej 6, 7 y 8]

