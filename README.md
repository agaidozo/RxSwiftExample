# RxSwiftExample

Este repositório contém um exemplo simples de como usar a biblioteca RxSwift para iOS.

## Instalação

Para instalar o RxSwift, execute o seguinte comando no terminal:

```
pod install
```

## Uso

Para executar o exemplo, abra o projeto no Xcode e execute-o no simulador ou em um dispositivo físico.

## Explicação

O exemplo consiste em uma tela com um botão e um label. Quando o botão é pressionado, um Observable é emitido com um valor aleatório. O Observable é então ligado ao label, que é atualizado com o valor emitido.

## Código

O código do exemplo está localizado no arquivo `ViewController.swift`.

```Swift
import UIKit
import RxSwift

class ViewController: UIViewController {

    @IBOutlet weak var button: UIButton!
    @IBOutlet weak var label: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()

        // Cria um Observable que emite um valor aleatório a cada segundo
        let randomNumbers = Observable<Int>.interval(1, scheduler: MainScheduler.instance)
            .map { _ in Int.random(in: 0...100) }

        // Liga o Observable ao label
        randomNumbers
            .bind(to: label.rx.text)
            .disposed(by: disposeBag)
    }
}
```

Para mais informações sobre RxSwift, consulte a documentação oficial: https://github.com/ReactiveX/RxSwift.

Data de criação: 2023-09-27  
Autor: Obde Willy

