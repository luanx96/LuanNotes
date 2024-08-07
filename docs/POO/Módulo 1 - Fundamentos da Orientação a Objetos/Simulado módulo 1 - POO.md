
### Questão 1 

**Marque a opção que indica corretamente qual(is) modificador(es) deve(m) ser usado(s) ao declarar uma constante em Java.**

- a. const
- b. static e final ✔
- c. final e int
- d. final e public

---
### Questão 2

**Dois símbolos '&' juntos representam o operador AND (E lógico).**

**Escolha uma opção:**

- Verdadeiro ✔
- Falso
---
### Questão 3 

**Java é uma linguagem interpretada, compilada ou híbrida?**

- a. Não é uma linguagem de programação
- b. Interpretada
- c. Compilada
- d. Híbrida ✔

---
### Questão 4

**Associe os caracteres de cada operador de acordo com o nome do operador correspondente.**

- **Operador unário de incremento:** `++` ✔
- **Operador ternário:** 
- **Operador unário de decremento:** `--` ✔
- **Operador de módulo:** `%` ✔

---
### Questão 5

**Associe os caracteres de cada operador de acordo com o nome do operador correspondente.**

- **Operador unário de incremento:** `++` ✔
- **Operador ternário:** `?:` ✔
- **Operador unário de decremento:** 
- **Operador de módulo:** `%` ✔

---
### Questão 6

**O que é impresso após a execução do código?**

```java
System.out.println(1+2+""+2+1);
```

- a. 1221
- b. Não compila
- c. 6
- d. 321 ✔

---
### Questão 7
**Crie uma classe Java com um método main que leia do console seis números inteiros usando a classe Scanner e imprima o maior número inteiro lido inicialmente.**

Entrada: 1; 2; 3; 4; 2; 3;
Resultado: 4

Entrada: 598; 2; 66; 78945; 0; 1;
Resultado: 78945

Resposta: regime de penalidade: 0%
```java
import java.util.Scanner;
class Scan{
    public static void main(String[] args) {
        int i, num;
        int maior = -999999;
        Scanner scan = new Scanner(System.in);

        for (i = 0; i < 6; i++) {
            num = scan.nextInt();
            if (num > maior)
                maior = num;
        }

        System.out.println(maior);
    }
}
```
![[16M1PO_1.png]]

---
### Questão 8 
**Qual é o valor de x e de y de acordo com o código abaixo?**

```java
int x = 4;
int y = x++ + 100;
```

- a. x = 5 e y = 105
- b. x = 4 e y = 105
- c. x = 4 e y = 104
- d. x = 5 e y = 104 ✔

---
### Questão 9

**Indique se as linguagens a seguir são interpretadas, compiladas ou híbridas.**

- **C++:** Compilada ✔
- **C#:** Compilada ✔
- **PHP:**
- **C:** Compilada ✔
- **JavaScript:** Interpretada ✔
- **Java:** Híbrida ✔

---
### Questão 10

**Indique se as linguagens a seguir são interpretadas, compiladas ou híbridas.**

- **C++:** Compilada ✔
- **C#:** Compilada ✔
- **PHP:** Interpretada ✔
- **C:** Compilada ✔
- **JavaScript:** Interpretada ✔
- **Java:** Híbrida ✔
---
### Questão 11

**Indique se as linguagens a seguir são interpretadas, compiladas ou híbridas.**

- **C++:** Compilada ✔
- **C#:** Compilada
- **PHP:** Interpretada ✔
- **C:** Compilada ✔
- **JavaScript:** Interpretada ✔
- **Java:** Híbrida ✔
---
### Questão 12

**Escreva uma classe em Java contendo um método main, denominada HelloWorld, que escreve o nome da disciplina "PROGRAMAÇÃO ORIENTADA A OBJETOS" na saída padrão.**

**Por exemplo:**

**Resultado:**
```
PROGRAMAÇÃO ORIENTADA A OBJETOS
```

**Resposta:**
```java
class HelloWorld{
    public static void main(String[] args) {
        System.out.println("PROGRAMAÇÃO ORIENTADA A OBJETOS");
    }
}
```

| Esperado                       | Obteve                          |   |
|--------------------------------|---------------------------------|---|
| PROGRAMAÇÃO ORIENTADA A OBJETOS| PROGRAMAÇÃO ORIENTADA A OBJETOS | ✔ |

---
### Questão 13
