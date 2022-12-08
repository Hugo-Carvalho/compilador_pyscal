# Compilador Pyscal

Compilador da linguagem de programação denominada Pyscal com analises léxicas, sintáticas, semânticas e de código intermediário.


## A linguagem Pyscal

```
Programa       →   Classe EOF
Classe         →   "class" ID ":" ListaFuncao Main "end" "."
DeclaraID      →   TipoPrimitivo ID ";"
ListaFuncao    →   ListaFuncao Funcao | ε
Funcao         →   "def" TipoPrimitivo ID "(" ListaArg ")" ":" (DeclaraID)∗ListaCmd Retorno "end" ";"
ListaArg       →   Arg "," ListaArg | Arg
Arg            →   TipoPrimitivo ID
Retorno        →   "return" Expressao ";" | ε
Main           →   "defstatic" "void" "main" "(" "String" "[" "]" ID ")" ":" (DeclaraID)∗ListaCmd "end" ";"
TipoPrimitivo  →   "bool" | "integer" | "String" | "double" | "void"
ListaCmd       →   ListaCmd Cmd | ε
Cmd            →   CmdIF | CmdWhile | CmdAtribui | CmdFuncao | CmdWrite
CmdIF          →   "if" "(" Expressao ")" ":" ListaCmd "end" ";"
                   | "if" "(" Expressao ")" ":" ListaCmd "else" ":" ListaCmd "end" ";"
CmdWhile       →   "while" "(" Expressao ")" ":" ListaCmd "end" ";"
CmdWrite       →   "write" "(" Expressao ")" ";"
CmdAtribui     →   ID "=" Expressao ";"
CmdFuncao      →   ID "(" (Expressao ("," Expressao)∗ )? ")" ";"
Expressao      →   Expressao Op Expressao
                   | ID | ID "(" (Expressao ("," Expressao)∗ )? ")"
                   | ConstInteger | ConstDouble | ConstString | "true" | "false"
                   | OpUnario Expressao | "(" Expressao")"
Op             →   "or" | "and" | "<" | "<=" | ">" | ">=" | "==" | "!=" | "/" | "*" | "-" | "+"
OpUnario       →   "-" | "!" 
```

### Descrição dos Padrões de Formatação

Os padrões de formação das constantes e dos identificadores da linguagem são descritos abaixo:
- ID: deve iniciar com uma letra seguida de 0 ou mais produções de letras, dígitos e/ou caracteres _.
- ConstInteger: cadeia numérica contendo 1 ou mais produções de dígitos.
- ConstDouble cadeia numérica contendo 1 ou mais produções de dígitos, tendo em seguida um símbolo de ponto (.) e, em seguida, 1 ou mais produções de dígitos.
- ConstString: deve iniciar e finalizar com o caractere aspas (") contendo entre eles uma sequência de 1 ou mais produções de letras, dígitos e/ou símbolos da tabela ASCII – exceto o próprio caractere aspas.
- EOF é o código de fim de arquivo.
- Aspas na gramática apenas destacam os terminais, e os diferencia dos não-terminais.
- Apenas comentários de uma linha são permitidos e seguem o padrão de Python.

#### A gramática do Pyscal foi corrigida.

## Modelo do Autômato de Itens

![Automato](https://user-images.githubusercontent.com/41404633/206334741-0422bc88-3557-40e2-9c49-731eb2b270ec.png)
