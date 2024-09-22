Para a **aula 5** do seu curso de PHP, proponho um tema avançado dentro do uso de **Programação Orientada a Objetos (POO)**, introduzindo **Herança e Polimorfismo**. Esses são conceitos centrais para entender o comportamento dinâmico e flexível que POO oferece, especialmente em projetos maiores e mais complexos.

### **Aula 5: Herança e Polimorfismo em PHP**
---

#### **Objetivos da Aula:**
- Entender o conceito de herança.
- Aprender a criar classes derivadas.
- Implementar o conceito de polimorfismo.
- Explorar a sobrescrita de métodos.
- Entender o uso de `parent` e `final`.

#### **1. Introdução à Herança**
A herança permite que uma classe herde as propriedades e métodos de outra classe, promovendo o reuso de código. A classe que herda é chamada de **classe filha** e a classe que é herdada é chamada de **classe pai**.

##### Exemplo:
```php
<?php
class Animal {
    public $nome;

    public function __construct($nome) {
        $this->nome = $nome;
    }

    public function emitirSom() {
        echo "O animal faz um som.";
    }
}

class Cachorro extends Animal {
    public function emitirSom() {
        echo "O cachorro late.";
    }
}

$cachorro = new Cachorro("Rex");
echo $cachorro->nome; // Saída: Rex
$cachorro->emitirSom(); // Saída: O cachorro late.
?>
```

**Explicação:**
- A classe `Cachorro` estende `Animal`, herdando o atributo `$nome` e o método `emitirSom()`.
- O método `emitirSom()` foi sobrescrito (override) na classe `Cachorro` para fornecer um comportamento específico.

#### **2. Polimorfismo**
O polimorfismo permite que diferentes classes utilizem o mesmo método, mas com comportamentos diferentes. Isso é possível através da sobrescrita de métodos em classes herdadas.

##### Exemplo com polimorfismo:
```php
<?php
class Gato extends Animal {
    public function emitirSom() {
        echo "O gato mia.";
    }
}

function fazerAnimalEmitirSom(Animal $animal) {
    $animal->emitirSom();
}

$cachorro = new Cachorro("Rex");
$gato = new Gato("Mia");

fazerAnimalEmitirSom($cachorro); // Saída: O cachorro late.
fazerAnimalEmitirSom($gato); // Saída: O gato mia.
?>
```

**Explicação:**
- Mesmo que o método `emitirSom()` seja chamado de maneira genérica, cada classe (`Cachorro`, `Gato`) responde de forma diferente, implementando seu próprio comportamento.

#### **3. Uso do `parent`**
O `parent` é usado para chamar métodos ou construtores da classe pai na classe filha.

##### Exemplo:
```php
<?php
class Cavalo extends Animal {
    public function __construct($nome) {
        parent::__construct($nome); // Chama o construtor da classe pai
    }

    public function emitirSom() {
        parent::emitirSom(); // Chama o método da classe pai
        echo " O cavalo relincha.";
    }
}

$cavalo = new Cavalo("Trovão");
$cavalo->emitirSom(); // Saída: O animal faz um som. O cavalo relincha.
?>
```

**Explicação:**
- A palavra-chave `parent` chama tanto o construtor quanto o método da classe `Animal`.

#### **4. Métodos `final`**
Um método `final` não pode ser sobrescrito por classes filhas.

##### Exemplo:
```php
<?php
class Ave extends Animal {
    final public function emitirSom() {
        echo "A ave canta.";
    }
}

class Papagaio extends Ave {
    // Este código gerará um erro
    public function emitirSom() {
        echo "O papagaio fala.";
    }
}
?>
```

**Explicação:**
- O método `emitirSom()` da classe `Ave` não pode ser sobrescrito na classe `Papagaio` porque foi declarado como `final`.

#### **5. Exercício Prático**
Crie um sistema de cadastro de veículos utilizando herança. Teremos uma classe `Veiculo` com atributos como `marca` e `modelo`, e classes filhas como `Carro` e `Moto` que herdarão esses atributos e terão métodos específicos.

##### Exemplo de Estrutura:
```php
<?php
class Veiculo {
    public $marca;
    public $modelo;

    public function __construct($marca, $modelo) {
        $this->marca = $marca;
        $this->modelo = $modelo;
    }

    public function detalhes() {
        echo "Veículo: $this->marca, Modelo: $this->modelo.";
    }
}

class Carro extends Veiculo {
    public function detalhes() {
        echo "Carro: $this->marca, Modelo: $this->modelo.";
    }
}

class Moto extends Veiculo {
    public function detalhes() {
        echo "Moto: $this->marca, Modelo: $this->modelo.";
    }
}

$carro = new Carro("Toyota", "Corolla");
$moto = new Moto("Honda", "CB 500");

$carro->detalhes(); // Saída: Carro: Toyota, Modelo: Corolla.
$moto->detalhes(); // Saída: Moto: Honda, Modelo: CB 500.
?>
```

#### **Conclusão:**
Nesta aula, você aprendeu a utilizar herança para reutilizar código e a aplicar polimorfismo para gerar comportamentos dinâmicos. Pratique criando suas próprias hierarquias de classes e explore as vantagens que esses conceitos trazem para o desenvolvimento de software.

---

Se precisar de mais exemplos ou algum ajuste, posso refinar ainda mais a aula.