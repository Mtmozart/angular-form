Formulário reativo - primeira coisa, importar o módulo de formulário reativo.
` ReactiveFormsModule` dentro de imports

Criando manualmente: Você cria um FormGroup e um FormControl para cada campo do formulário.

```typescript
  formulario!: FormGroup;

ngOnInit(): void {
    this.formulario = new FormGroup({
      conteudo: new FormControl(''),
      autoria: new FormControl(''),
      modelo: new FormControl('')
    })
  }
```

Usando o FormBuilder: O FormBuilder simplifica a criação dos formulários, atribuindo os controles aos campos automaticamente.

```typescript


ngOnInit(): void {
    this.formulario = this.formBuilder.group({
      conteudo: [''],
      autoria: [''],
      modelo: ['']
    })
  }

```

Como vincular ?
Basta por no formulário a seguinte anotação:
`<form [formGroup]="formulario">`
e usar a propriedade formControlName para fazer associação de valores:

```typescript
<form [formGroup]="formulario">
    <label for="pensamento">Pensamento</label>
    <input
      type="text"
      class="input"
      id="pensamento"
      formControlName="conteudo"
      placeholder="Digite o pensamento"
    >
  //Passando conteúdo do formulário

   <p class="conteudo">{{ formulario.get('contedo')?.value }}</p>
   <p class="autoria"><b>{{ formulario.get('autoria')?.value }}</b></p>
```

# Validação de usuário

Aplicar validator é simples, apenas utilizar a classe Validator e dentro do array passar os parâmetros que quero.

```typescript


<form [formGroup]="formulario">
    <label for="pensamento">Pensamento</label>
    <input
      type="text"
      class="input"
      id="pensamento"
      formControlName="conteudo"
      placeholder="Digite o pensamento"
    >

```

Outros validadores:
Validators.min()
Validador que exige que o valor do controle seja maior ou igual ao número fornecido.

    Validators.max()
        Validador que exige que o valor do controle seja menor ou igual ao número fornecido.

    Validators.requiredTrue()
        Validador que exige que o valor do controle seja verdadeiro. Este validador é comumente usado para caixas de seleção obrigatórias.

    Validators.email()
        Validador que exige que o valor do controle passe em um teste de validação de email.

    Validators.maxLength()
        Validador que exige que o comprimento do valor do controle seja menor ou igual ao tamanho máximo fornecido.

    Validators.nullValidator()
        Validador de valores nulos.

    Validators.composeAsync()
        Compõe vários validadores assíncronos em uma única função que retorna a união dos objetos de erro individuais para o controle fornecido.
