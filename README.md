### 1. **Classes e Objetos**

#### Código
```kotlin
class Carro(val marca: String, val modelo: String) {
    fun iniciar() {
        println("Carro iniciado")
    }
}

fun main() {
    val meuCarro = Carro("Toyota", "Corolla")
    println("${meuCarro.marca} ${meuCarro.modelo}")
    meuCarro.iniciar()
}
```

#### Explicação
- **Classe:** `Carro` é uma classe com dois atributos (`marca` e `modelo`) e um método (`iniciar`).
- **Objeto:** `meuCarro` é uma instância da classe `Carro`. Os atributos são inicializados com "Toyota" e "Corolla".

### 2. **Encapsulamento**

#### Código
```kotlin
class Carro(private var marca: String, private var modelo: String) {
    fun getMarca() = marca
    fun setMarca(novaMarca: String) {
        marca = novaMarca
    }
}

fun main() {
    val meuCarro = Carro("Toyota", "Corolla")
    println(meuCarro.getMarca())
    meuCarro.setMarca("Honda")
    println(meuCarro.getMarca())
}
```

#### Explicação
- **Encapsulamento:** `marca` e `modelo` são privados e só podem ser acessados ou modificados através dos métodos `getMarca` e `setMarca`.

### 3. **Herança**

#### Código
```kotlin
open class Animal {
    open fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Latido")
    }
}

fun main() {
    val meuCachorro = Cachorro()
    meuCachorro.fazerSom()
}
```

#### Explicação
- **Herança:** `Cachorro` herda da classe `Animal`.
- **Sobrescrita de Método:** `Cachorro` sobrescreve o método `fazerSom` para fornecer uma implementação específica.

### 4. **Polimorfismo**

#### Código
```kotlin
open class Animal {
    open fun fazerSom() {
        println("Som do animal")
    }
}

class Cachorro : Animal() {
    override fun fazerSom() {
        println("Latido")
    }
}

fun fazerSom(animal: Animal) {
    animal.fazerSom()
}

fun main() {
    val meuAnimal: Animal = Cachorro()
    fazerSom(meuAnimal)
}
```

#### Explicação
- **Polimorfismo:** O método `fazerSom` aceita um parâmetro do tipo `Animal`, mas pode receber um objeto de qualquer subclasse de `Animal`, como `Cachorro`.

### 5. **Abstração**

#### Código
```kotlin
abstract class Forma {
    abstract fun desenhar()
}

class Circulo : Forma() {
    override fun desenhar() {
        println("Desenhando um círculo")
    }
}

interface Movivel {
    fun mover()
}

class Quadrado : Forma(), Movivel {
    override fun desenhar() {
        println("Desenhando um quadrado")
    }

    override fun mover() {
        println("Movendo o quadrado")
    }
}

fun main() {
    val circulo = Circulo()
    circulo.desenhar()

    val quadrado = Quadrado()
    quadrado.desenhar()
    quadrado.mover()
}
```

#### Explicação
- **Abstração:** `Forma` é uma classe abstrata que define um contrato para a classe `Circulo`.
- **Interface:** `Movivel` é uma interface que `Quadrado` implementa, adicionando comportamento extra além de `Forma`.

### 6. **Composição**

#### Código
```kotlin
class Motor(val tipo: String)

class Carro(val marca: String, val motor: Motor)

fun main() {
    val motor = Motor("V8")
    val carro = Carro("Ford", motor)
    println("Carro: ${carro.marca}, Motor: ${carro.motor.tipo}")
}
```

#### Explicação
- **Composição:** `Carro` tem um `Motor` como parte de sua estrutura, representando uma relação "tem-um".

### 7. **Associação, Agregação e Composição**

#### Código
```kotlin
class Pessoa(val nome: String)

class Carro(val modelo: String) {
    var dono: Pessoa? = null
}

fun main() {
    val pessoa = Pessoa("João")
    val carro = Carro("Fusca")
    carro.dono = pessoa
    println("Dono do carro: ${carro.dono?.nome}")
}
```

#### Explicação
- **Associação:** `Carro` tem uma referência opcional (`dono`) para uma instância de `Pessoa`, representando uma relação associativa.

### 8. **Métodos e Construtores**

#### Código
```kotlin
class Carro(val marca: String, val modelo: String) {
    init {
        println("Carro $marca $modelo criado")
    }
}

fun main() {
    val carro = Carro("Toyota", "Corolla")
}
```

#### Explicação
- **Construtores:** O bloco `init` é executado quando um objeto da classe `Carro` é criado, inicializando atributos e executando código adicional.

### 9. **Static Members**

#### Código
```kotlin
class Util {
    companion object {
        fun saudar(nome: String) {
            println("Olá, $nome")
        }
    }
}

fun main() {
    Util.saudar("Mundo")
}
```

#### Explicação
- **Companion Object:** Em Kotlin, membros estáticos são definidos dentro de um `companion object` na classe `Util`, permitindo acesso direto via `Util.saudar`.

### 10. **Exceções e Tratamento de Erros**

#### Código
```kotlin
fun dividir(a: Int, b: Int): Int {
    return try {
        a / b
    } catch (e: ArithmeticException) {
        println("Erro: divisão por zero")
        0
    }
}

fun main() {
    val resultado = dividir(10, 0)
    println("Resultado: $resultado")
}
```

#### Explicação
- **Tratamento de Exceções:** O bloco `try-catch` é usado para capturar e tratar exceções, como divisão por zero.

### 11. **Design Patterns**

#### Singleton
```kotlin
object Singleton {
    fun mostrarMensagem() {
        println("Singleton em ação")
    }
}

fun main() {
    Singleton.mostrarMensagem()
}
```

#### Explicação
- **Singleton:** `object` em Kotlin define um Singleton, garantindo que haja apenas uma instância da classe em todo o programa.

### Conclusão

Estes exemplos cobrem os conceitos fundamentais da Programação Orientada a Objetos (POO) usando Kotlin, demonstrando como utilizar classes, objetos, encapsulamento, herança, polimorfismo, abstração, composição e outros tópicos essenciais para construir software modular, reutilizável e fácil de manter.
