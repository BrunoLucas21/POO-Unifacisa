# Arrays

Arrays (ou arranjos, em português) servem para armazenar um conjunto de valores.
Esses valores podem ser de tipos primitivos (int, long, float, double, boolean) bem como de tipos não-primitivos, que são as classes.

Para declarar arrays, usamos colchetes:

```java
  int [] notasProva1; //um array de inteiros
  String [] alunos;   //um array de Strings
 ```
 
 No exemplo acima o array foi apenas declarado, mas ainda não foi criado.
 Podemos criar os arrays sem conteúdo, mas definindo o tamanho do array.
 E também podemos criá-los com conteúdo.
 
 Observem o exemplo a seguir.
 
 ```java
    int[] notasProva1 = new int [6]; 
    String[] alunos = new String[] {"Joao", "Joana", "Andre", "Gustavo", "Mariana", "Aline"};
 ```
 
 Neste exemplo, o array *notasProva1* foi criado com tamanho 6.
 Nesse caso, cada posição do array assumiu o valor padrão do int que é 0.
 O array *alunos* foi criado e ao mesmo tempo populado com os seguintes valores: "Joao", "Joana", "Andre", "Gustavo", "Mariana", "Aline".
 Por essa razão, o array *alunos* tem tamanho 6.
 
 ## Percorrendo Arrays
 
 Uma vez que o array *notasProva1* foi inicializado com valores padrão, em algum momento desejaremos alterar esses valores.
 De forma semelhante, possa ser que desejemos alterar o nome de algum aluno no array *alunos*.
 
 Isto é feito da seguinte forma:
 
 ``` java
    notasProva1[0] = 10;
    notasProva1[1] = 8;
    notasProva1[2] = 9;
    notasProva1[3] = 4;
    notasProva1[4] = 1;
    notasProva1[5] = 5;
    
    alunos[3] = "Adriano";
 ```
 
 No código anterior, atribuímos notas para a primeira prova relacionada aos 6 alunos.
 Note que a indexação dos arrays sempre começa em 0.
 Portanto, um array de tamanho 6 terá índices 0, 1, 2, 3, 4, 5.
 No exemplo anterior, também alteramos o nome do quarto aluno: Gustavo foi modificado para Adriano.
 
 Uma vez que tenhamos preenchido os arrays, em algum momento desejaremos percorrê-lo para fazer algumas verificações.
 Podemos fazer isto com um *for indexado*, ou com um *for-each*.
 
 For indexado:
  ``` java
    //imprimindo alunos
    for(int i = 0; i < 6; i++) {
      System.out.println("Aluno: "+alunos[i]);			
    }
		
    //imprimindo notas
    for(int i = 0; i < 6; i++) {
      System.out.println("Nota: "+notasProva1[i]);			
    }
 ```
 
  For-each:
  ``` java
    //imprimindo alunos
    for(String aluno : alunos) {
      System.out.println("Aluno: "+aluno);
    }
		
    //imprimindo notas
    for(int nota : notasProva1) {
      System.out.println("Nota: "+nota);
    }
 ```
 
 Para essa situação, os dois tipos de for tem o mesmo efeito.
 Portanto, nesse tipo de situação, use o que você preferir.
 
 Entretanto, em outras situações, o for-each não é indicado.
 Por exemplo, se assumirmos que a nota no índice i é referente ao aluno no índice i, poderíamos querer imprimir o nome do aluno e sua nota.
 O for-each não permite você fazer isto, mas o for indexado permite.
 
 Observe:
  ``` java
    //for indexado
    for(int i = 0; i < 6; i++) {
      System.out.println("Aluno: "+alunos[i]);			
      System.out.println("Nota: "+notasProva1[i]);
    }
 ```
 
 ## Arrays também são Objetos
 
 Arrays também **são objetos**.
 Isto traz algumas consequências:
 1. Arrays tem variáveis (como é comum em objetos)
 2. Arrays tem métodos (como é comum em objetos)
 3. Se compararmos dois arrays com *==*, os endereços de memória dos arrays são comparados, e não seu conteúdo
 
 **Ponto 1:**
 Uma variável importante em arrays é *length*, que determina seu comprimento.
 Com esta informação, podemos tornar o nosso for indexado mais inteligente.
 
 Veja a seguir:
 ``` java
    //for indexado
    for(int i = 0; i < alunos.length; i++) {
      System.out.println("Aluno: "+alunos[i]);			
      System.out.println("Nota: "+notasProva1[i]);
    }
 ```
 
 Desta forma, se o tamanho de array de alunos mudasse, não precisaríamos mudar o for, pois ele inteligentemente sabe o comprimento do array.
 
 **Ponto 2:**
 Três métodos interessantes são o *clone*, *toString* e *equals*.
 O clone permite criar uma cópia do array com conteúdo idêntido.
 
 ``` java
 String[] alunos = new String[] {"Joao", "Joana", "Andre", "Gustavo", "Mariana", "Aline"};
 String[] alunosClone = alunos.clone();
 // for-each
 for (String aluno : alunosClone) {
    System.out.println("Aluno clone: " + aluno);
 }
 ```
 
 Os três métodos são herdados da classe Object.
 Por essa razão, o *toString* retorna identificador da classe + representação do endereço de memória, e *equals* basicamente compara com *==*.
 
  **Ponto 3:**
 No exemplo acima temos dois arrays: alunos e alunosClone.
 Cada array aponta para um objeto distinto, porém, ambos os objetos possuem mesmo conteúdo.
 Por esta razão, uma comparação entre alunos e alunosClone com *==* retorna *false*, e uma comparação com *equals* também retorna *false* (visto que acabamos de discutir que o equals é herdado de Object, e em Object a comparação é implementada com *==*).
 
 
 ``` java
 String[] alunos = new String[] {"Joao", "Joana", "Andre", "Gustavo", "Mariana", "Aline"};
 String[] alunosClone = alunos.clone();
 
 System.out.println(alunos.toString());
 System.out.println(alunos==alunosClone);
 System.out.println(alunos.equals(alunosClone));
 ```
 
 ## A Classe Arrays e alguns de seus métodos Estáticos
 
 No Java, existe uma classe utilitária de nome **Arrays** que nos provê alguns métodos estáticos bastante úteis.
 Os principais são: Arrays.equals(Object o1, Object o2), Arrays.sort(variavel) e Arrays.toString(variavel).
 
 - Arrays.equals(Object o1, Object o2): compara os conteúdos dos arrays
 - Arrays.sort(variável): ordena o array
 - Arrays.toString(variável): retorna uma representação textual do array
 
  ``` java
 String[] alunos = new String[] {"Joao", "Joana", "Andre", "Gustavo", "Mariana", "Aline"};
 String[] alunosClone = alunos.clone();
 
 System.out.println(Arrays.equals(alunos, alunosClone));
 
 System.out.println("Antes de ordenar notas: "+Arrays.toString(notasProva1));
 Arrays.sort(notasProva1);
 System.out.println("Depois de ordenar notas: "+Arrays.toString(notasProva1));
 ```
 
 ## Exceções
 
 As exceções mais comuns quando usamos arrays são: ArrayIndexOutOfBoundsException e NullPointerException.
  - ArrayIndexOutOfBoundsException: quando você tenta acessar um elemento do array em um índice inexistente (ex: índice negativo, ou índice que extrapola o limite do array)
  - NullPointerException: quando você tenta fazer qualquer operação em um objeto (que neste caso é um array) mas o objeto não foi instanciado
  
   ``` java
 String[] alunos = new String[] {"Joao", "Joana", "Andre", "Gustavo", "Mariana", "Aline"};
 
 System.out.println(alunos[10]);	//ArrayIndexOutOfBoundsException:
 int [] arrayNaoInstanciado = null;
 System.out.println(arrayNaoInstanciado[0]);	//NullPointerException
 ```
 
 ## Performance
 
 
 